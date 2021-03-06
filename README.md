# MRTK-Quest
MRTK-Quest is a Mixed Reality Toolkit (MRTK) extension for Oculus Quest, now with support for Rift/Rift S as well.
It was built to showcase the hand-driven interaction model designed by Microsoft for HoloLens 2, on the Oculus ecosystem.

## Main features
- Full support for articulated hand tracking, and simulated hand tracking using controllers with avatar hands.
- Support for Oculus Link on Quest with controllers, which means rapid iteration without builds.
- Full support for any interaction in the MRTK designed to work for HoloLens 2.

## Demo Video
[![Demo video](https://user-images.githubusercontent.com/7420990/75618297-21b59300-5b3a-11ea-8093-365ce3921c15.gif)](https://twitter.com/prvncher/status/1235731976893665280)

# Supported versions
- Unity 2018.4.x (Currently targetting 2018.4.18f1). Some users have reported success with 2019.3 as well.
- Oculus Integration 14.0
- Mixed Reality Toolkit v2.3.0+

# Supported target devices
- Oculus Rift/S - Windows Standalone
- Oculus Quest  - Android / Windows Standalone w/ Link

## FAQ
Hands don't seem to work in builds, what am I doing wrong?
- Due to licensing reasons, the Oculus Integrations folder is not included in this repo. In that folder, there is a scriptable object called *OculusProjectConfig*. In that config file, you need to set *HandTrackingSupport* to "Controllers and Hands".

Avatar hands don't work for me, what am I doing wrong?
- Avatar hand support requires an app id to be set in *Resources/OvrAvatarSettings*. This repo sets a dummy id "12345".

No matter what I do, I cannot get everything setup right, what do I do?
- Some users have issues with either MRTK, or Oculus Integration. As such, I've created a sample project called [MRTK-Quest-Sample](https://github.com/provencher/MRTK-Quest-Sample). Since it features all the depedencies, it uses a different license than this project, as such I only recommend consulting it for education purposes. I'll try and keep it up to date as all the depedencies evolve.

How do I allow MRTK-Quest and HoloLens 2 to co-exist in a project?
- First you will need to add the scripting define "OVRPLUGIN_UNSUPPORTED_PLATFORM" to the UWP build target.
- Second, delete the SampleFramework from your Oculus integration folder.
- Finally, you will need to replace the OVR Camera Rig from your scene, and use the MRTK Default Camera + Playspace setup.
-> [MRTK-Quest-Sample](https://github.com/provencher/MRTK-Quest-Sample) is setup this wayfor everything except the camera configuration.

# Getting started with MRTK-Quest

## 1. Obtain MRTK-Quest

### 1a. Develop with the MRTK-Quest repository directly
Clone this repository, and then make sure to initialize submodules.
To do this, open a command line terminal, rooted on the folder you'd like the project to be in. 
(Hold shift + right click -> Select "Open Powershell Window Here")

Then clone using this command "git clone --recurse-submodules https://github.com/provencher/MRTK-Quest.git"

    This will clone the official MRTK development branch as well. 
    If you'd like your own version of MRTK, simply remove "--recurse-submodules" from the command, 
    and copy your MRTK files to the External folder, before proceeding to step 2.

### 1b. Develop an existing MRTK application
Simply download the MRTK-Quest **.unitypackage** from the latest **[Release page.](https://github.com/provencher/MRTK-Quest/releases)**. As of 0.6, Examples are split out into a separate package, so that users without MRTK Examples can work with a minimal MRTK-Quest development environment.

    If MRTK is already in your project, move to step 3.

## 2. Import MRTK

### 2a. Obtain MRTK from cloning the submodule included with this REPO
MRTK will be located in your **External** folder.

If you wish to **develop MRTK**, and modify code within in it, independently from your project, this is the preferred approach.

    Since MRTK is located in **External**, it will be necessary to make them appear as if they are in **Assets**.
    To accomplish this, you will need to create a SymLink.

    - On Windows run the bat External/createSymlink.bat by double clicking it. 
    - On OS X execute the shell script via "./createSymlink.sh".
    This will link the MRTK folders cloned via the submodule into the project.

### 2b. Obtain MRTK via alternative means
It is possible to import MRTK directly into the Assets folder by downloading the [latest oficial release](https://github.com/microsoft/MixedRealityToolkit-Unity/releases), or via alternative means like nuget.

If you wish to use MRTK as a library, and wait for official releases, this is the preferred approach.

    Simply move onto step 3 if your project has MRTK configured this way.

## 3. Import Oculus Integration
Download [Oculus Integration 13.0](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from Asset Store and import it.
- Alternatively just drag and drop the Oculus folder into Assets/

## 4. Project Configuration Window
MRTK has a Project Configuration modal window that pops up when you first open a project.

- **MultiThreaded Rendering** The project configuration window will attempt to disable this option, 
however, from my testing with Quest, it works properly, and improves performance.

- **[Possibly obsolete][MSBuild]** In this window, there is a checkbox for MSBuild, which will attempt to add MSBuild to your manifest.json that then adds various DLLs to your project via NuGET. MSBuild is not currently necessary for functional Android builds. This may change in the future. If you are approching the 256 character path limit, this may cause problems for you.

## 5. MRTK-Quest Integration Configuration
New Config scriptable object exposing hand mesh material and performance seetings.
This is a project singleton located in Resources/MRTK-OculusConfig    
![image](https://user-images.githubusercontent.com/7420990/75618441-81ad3900-5b3c-11ea-9baa-9ac2833e8dad.png)


## 6. Community and support
If you'd like to discuss your issues or ideas to improve this project, please join us over on the [HoloDevs Slack](https://holodevelopersslack.azurewebsites.net/).
There is a public channel called #MRTK-Quest.

# Author
Eric Provencher [@prvncher](https://twitter.com/prvncher)

Modified from: 
Furuta, Yusuke ([@tarukosu](https://twitter.com/tarukosu))

# License
MIT
