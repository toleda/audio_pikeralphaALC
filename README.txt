audio_pikeralphaALC
============
Piker-Aplha - http://pikeralpha.wordpress.com/
Realtek ALC Audio - Native AppleHDA.kext/No Patching/Persistant

The Realtek ALC AppleHDA Support kext, installed with the native AppleHDA.kext, enables full onboard, HDMI and DP audio (Note 1).  The ALC AppleHDA Support kext provides audio codec binary patch and config data and layouts and platforms injection.

Update: 10.10: Yosemite Initial Realtek ALC support (v3.0 and newer)

Requirements
  1. Chameleon/Chimera/Clover 
        1. Optional/Clover, see https://github.com/toleda/audio_CloverALC
  2. OS X
	1. 10.10 or newer
	2. 10.9 or newer
  3. Native AppleHDA.kext  (If not installed, run Yosemite installer)
  4. Supported Realtek on board audio codec
  5. Audio ID Injection, see https://github.com/toleda/audio_ALCinjectiom

Required Information (Select one from each category)
  1. Codec/ALC
	1. 885
	2. 887 (for Legacy only, Note 2)
	3. 888 (for Legacy only, Note 2)
	4. 889
	5. 892
	6. 898
	7. 1150
  2. Layout Support (Definitions, Note 3)
	1. 885, 887, 888, 889, 892, 898, 1150
	2. 887, 888, 889, 892, 898, 1150
	3. 887, 888, 889, 892, 898
  3. Yosemite version
	1. 10.10
  4. Mavericks version
	1. 10.9 (all versions)

pikeralphaALC AppleHDA Support Kext Method
  1. Realtek ALC AppleHDA Support kext with patched binaries
	1. Native AppleHDA.kext untouched
  2. AppleHDA8Series - ConfigData, layouts, Platforms and HDA binary patch

pikeralphaALC AppleHDA Support Kext - Installation
  1. AppleHDA Support kext (Use Terminal/Terminal output below)
	1. https://github.com/Piker-Alpha/AppleHDA8Series.sh 
	2. Download Zip
	3. $ cd Downloads/AppleHDA8Series.sh-master 
	4a. Chameleon/Chimera/Clover - no AppleHDA binary patch
		1. $ ./AppleHDA8Series.sh -b AppleHDA
		2. $ ./AppleHDA8Series.sh -b AppleHDA - b AppleHDAController
	4b. Clover - with AppleHDA kext patch(es)
		1. $ ./AppleHDA8Series.sh
	5. Password
	6. Codec
	7. Layout
	8. Version
	9. Install S/L/E
	10. Reboot
  3. Restart
  4. Verify ALC AppleHDA Support kext installed
	1. S/L/E/AppleHDA885
	2. S/L/E/AppleHDA887 
	3. S/L/E/AppleHDA888
	4. S/L/E/AppleHDA889
	5. S/L/E/AppleHDA892
	6. S/L/E/AppleHDA898
	7. S/L/E/AppleHDA1150
  5. Verify ALC onboard audio
	1. System Preferences/Sound/Output/select audio device

Notes
  1. HDMI/DP audio may require
	1. dsdt/ssdt edits
	2. framebuffer edits
  2. 887/888 Legacy
	1.  Replace AppleHDALoader.kext/Contents/Resources/Platforms.xml.zlib
            with Legacy Platforms.xml.zlib (v100202) from:
		1. https://github.com/toleda/audio_ALC887
		2. https://github.com/toleda/audio_ALC888
  3. Layout Definitions (Layout/Audio ID injection installed separately, 
        see https://github.com/toleda/audio_ALCInjection)
	1 - 3/5/6 audio port analog audio
	2 - 3 audio port analog audio
	3 - HD3000/HD4000 HDMI audio and analog audio

Tools
  1. IOReg (View Raw) - https://github.com/toleda/audio_ALCInjection/blob/master/IORegistryExplorer_v2.1.zip

Problem Reporting (include the following information)
  1. Description of audio problem
	1. OS X version/motherboard model/BIOS version/processor/graphics
	2. Procedure/Guide Used/AppleHDA.kext version
	3. AppleHDA(codec).kext (i.e., AppleHDA1150.kext)
	4. Copy of IOReg - IOReg_v2.1/File/Save a Copy As…, verify file (not
           ioreg.txt)
	5. Extra/dsdt.aml (if installed)
	6. Console/All Messages/kernel Sound assertions selected/Save
           Selection As…..
	7. Screenshot of System Information/Hardware/Audio/Intel High
           Definition Audio (not Devices)
  2. Post to:
	1. https://github.com/Piker-Alpha/AppleHDA8Series.sh/issues

Credit: PikeRAlpha 
http://pikeralpha.wordpress.com/2014/07/08/applehda8series-sh-v2-9-with-yosemite-support/
http://pikeralpha.wordpress.com/2014/01/05/new-style-of-applehda-kext-patching-take-ii/

AppleHDA Support Kext Method/Terminal Output
$ ./AppleHDA8Series.sh -b AppleHDA -b AppleHDAController
This script must be run as root!
Password:
AppleHDA8Series.sh v3.1 Copyright (c) 2013-2014 by Pike R. Alpha
                    patched XML files by Toleda and contributors
----------------------------------------------------------------
The supported Realtek ALC codecs for AppleHDA8Series.sh are:

    [1] Realtek ALC  885 (0x10EC0885 / 283904133)
    [2] Realtek ALC  887 (0x10EC0887 / 283904135)
    [3] Realtek ALC  888 (0x10EC0888 / 283904136)
    [4] Realtek ALC  889 (0x10EC0889 / 283904137)
    [5] Realtek ALC  892 (0x10EC0892 / 283904146)
    [6] Realtek ALC  898 (0x10EC0899 / 283904153)
    [7] Realtek ALC 1150 (0x10EC0900 / 283904256)

Please choose the desired codec for the hardware: 5
Do you want to use [1] as the layout-id (y/n)? y
Looking in: /System/Library/Extensions/AppleHDA.kext for ConfigData
Looking in: /System/Library/Extensions/FakeSMC.kext for ConfigData
Error: ConfigData NOT found!
Downloading https://raw.githubusercontent.com/toleda/audio_ALC892/master/892.zip ...
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 25382  100 25382    0     0  42912      0 --:--:-- --:--:-- --:--:-- 42875

ConfigData for Realtek ALC 892 found!
------------------------------------------------------------
IUccECFHHUAhRx4RIUcfkCFXHCAhVx0QIVceASFXHwEhZxwwIWcdYCFnHgEhZx8BIXcc8CF3HQAhdx4AIXcfQCGHHEAhhx2QIYceoCGHH5AhlxxgIZcdkCGXHoEhlx8CIaccUCGnHTAhpx6BIacfASG3HHAhtx1AIbceISG3HwIh5xyQIecdYSHnHksh5x8BIfcc8CH3HQAh9x4AIfcfQCEXHPAhFx0AIRceACEXH0A=
------------------------------------------------------------
Creating AppleHDA892.kext in: /Users/.../Downloads/AppleHDA8Series.sh-master
Copying AppleHDA ...
Bin-patching AppleHDA ... Done.
 Done.
AppleHDA892.kext appears to be loadable (including linkage for on-disk libraries).
Do you want to copy AppleHDA892.kext to: /System/Library/Extensions? (y/n) y
Do you want to reboot now? (y/n) 

toleda
https://github.com/toleda/audio_pikeralphaALC