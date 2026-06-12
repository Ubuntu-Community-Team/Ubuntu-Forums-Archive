---
title: "Issue attempting to install ANY variation/flavor of 16.04 ubuntu"
date: 2018-04-21
forum: Installation &amp; Upgrades
---

### Post by arcadeportal32 on 2018-04-21
Hi Guys and Girls,

My name is Alex and I am "*_VERY_"* new to Linux and Ubuntu and I do not know much about it other then basics. 

I am a very experienced Windows user and have built my own PC's, however I have a PC that is older.. well more considered now "Vintage" then anything lol. I use it for early 2000's PC Games and Software that does not run on Modern PC's.
I want to Dual-Boot or even just Try "ANY" Flavor of 16.04 on it, preferably a more "lighter-weight" one especially so I can web-browse/YouTube a bit faster on it Vs using Firefox which works good, but is a bit laggy due to the lack of RAM. it is also connected to my TV so I can play DOOM, ect... on it :D.

I am having alot of issues installing ANY Flavor least (Ubuntu/Xubuntu/Kubuntu) 16.04 onto it, I have gotten the 16.04 Network Installer to work most of they way but it seems to crash eather when downloading.... **nic-firmware**


I have had only one NetBoot installer work just before Partitioning which I believe was eather for 17.10 or 14.04, however it hanged and crashed with a purple screen.

Every other way I have tried installing Ubuntu/Xubuntu/Kubuntu 16.04 as ended with this exact hang... "Tried with Unetbootin, a USB stick with Ubuntu 16.04" _HOWEVER_ the USB stick showed a Ubuntu screen with two pictures on the bottom but both crashing with this Command-Line Message as shown in the included Picture....

[IMG]https://ibb.co/hSSOeH[/IMG][IMG]https://ibb.co/hSSOeH[/IMG][IMG]https://preview.ibb.co/cB6umx/20180421_160047.jpg[/IMG]

The DVD-R copy of Ubuntu the BIOS seems to read, however whether due to the Drive or Bios it only shows a command cursor and went back the the BIOS OS Boot Select Screen.

Specs: It is a Working & Modified 18+ Year Old "1999/2000 Dell Dimension L1000R"

------------------
System Information
------------------
```
Time of this report: 4/8/2018, 22:02:20
       Machine name: PENT-554801DA61
   Operating System: Windows XP Professional (5.1, Build 2600) Service Pack 3 (2600.xpsp_sp3_qfe.130704-0421)
           Language: English (Regional Setting: English)
System Manufacturer: Dell Computer Corporation      
       System Model: L100R                          
               BIOS: Default System BIOS
          Processor: Intel Pentium III, ~1.0GHz
             Memory: 254MB RAM
          Page File: 782MB used, 207MB available
        Windows Dir: C:\WINDOWS
    DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
     DxDiag Version: 5.03.2600.5512 32bit Unicode

---------------
Display Devices
---------------
        Card name: NVIDIA EVGA GeForce 6200  
     Manufacturer: NVIDIA
        Chip type: GeForce 6200
         DAC type: Integrated RAMDAC
       Device Key: Enum\PCI\VEN_10DE&DEV_0221&SUBSYS_B4003842&REV_A1
   Display Memory: 256.0 MB
     Current Mode: 1440 x 900 (32 bit) (60Hz)
          Monitor: Plug and Play Monitor
  Monitor Max Res: 1600,1200
      Driver Name: nv4_disp.dll
   Driver Version: 6.14.0013.0783 (English)
      DDI Version: 9 (or higher)
Driver Attributes: Final Retail
 Driver Date/Size: 1/31/2013 04:22:47, 4494336 bytes
      WHQL Logo'd: n/a
  WHQL Date Stamp: n/a
              VDD: n/a
         Mini VDD: nv4_mini.sys
    Mini VDD Date: 1/31/2013 04:22:47, 12648960 bytes
Device Identifier: {D7B71E3E-4161-11CF-FD58-0D9400C2CB35}
        Vendor ID: 0x10DE
        Device ID: 0x0221
        SubSys ID: 0xB4003842
      Revision ID: 0x00A1
      Revision ID: 0x00A1
      Video Accel: ModeMPEG2_C ModeMPEG2_D ModeWMV9_B ModeWMV9_A 
 Deinterlace Caps: {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                   {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(UYVY,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(UYVY,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                   {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(YV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                   {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
         Registry: OK
     DDraw Status: Enabled
       D3D Status: Enabled
       AGP Status: Enabled
DDraw Test Result: Not run
 D3D7 Test Result: Not run
 D3D8 Test Result: Not run
 D3D9 Test Result: Not run


        Card name: Intel(R) 82810E Graphics Controller (Microsoft Corporation)
     Manufacturer: Intel Corporation
        Chip type: Intel(R) 82810
         DAC type: Internal
       Device Key: Enum\PCI\VEN_8086&DEV_7125&SUBSYS_43328086&REV_03
   Display Memory: 32.0 MB
     Current Mode: 800 x 600 (24 bit) (60Hz)
          Monitor: Default Monitor
  Monitor Max Res: 
      Driver Name: i81xdnt5.dll
   Driver Version: 6.13.0001.3198 (English)
      DDI Version: 8
Driver Attributes: Final Retail
 Driver Date/Size: 4/13/2008 22:41:56, 702845 bytes
      WHQL Logo'd: n/a
  WHQL Date Stamp: n/a
              VDD: n/a
         Mini VDD: i81xnt5.sys
    Mini VDD Date: 4/13/2008 15:04:28, 161020 bytes
Device Identifier: {D7B78E66-3265-11CF-48EF-3363A1C2CB35}
        Vendor ID: 0x8086
        Device ID: 0x7125
        SubSys ID: 0x43328086
      Revision ID: 0x0003
      Revision ID: 0x0003
      Video Accel: ModeMPEG2_A ModeMPEG2_B ModeMPEG2_C ModeMPEG2_D 
 Deinterlace Caps: n/a
         Registry: OK
     DDraw Status: Enabled
       D3D Status: Enabled
       AGP Status: Enabled
DDraw Test Result: Not run
 D3D7 Test Result: Not run
 D3D8 Test Result: Not run
 D3D9 Test Result: Not run
```

_Extra Info_:
```
Sound Card: Creative Sound Blaster PCI100 1999
IDE HDD Master: WD400 40 GB IDE HDD  <--- Ducktaped to the extra Floppy Bay :KS
IDE HDD Secondary: Seagate 40 GB IDE HDD <--- Mostly Empty
External Locked HDD: Toshiba 1 TB USB HDD  <--- For Extra Storage for games, programs
```

It runs very good, mostly thanks to the late model FULL SIZE EVGA GeForce 6200 with DVI-I/HDMI, VGA, & S-Video V.s. its original 24-Bit Color 82810E Integrated GPU Controller. You would not guess, but it **is** *ABLE* to run **Titan Souls and Minecraft** at 30+FPS :o

I have yet to install, but it can be upgraded it 512mb RAM. 


I would like **ANY** help the Ubuntu/Linux community can give me and getting some sort of Ubuntu installed. I have _*yet*_ to try to install Lubuntu, but I would guess I would get the same error? Help would be nice :D :KS

---

### Post by kerry_s on 2018-04-21
> Processor: Intel Pentium III, ~1.0GHz
Memory: 254MB RAM

your going to have to go really old school with those specs, totally bare bones.
[https://itsfoss.com/lightweight-linux-beginners/](https://itsfoss.com/lightweight-linux-beginners/)

make sure you look at the requirements & pick accordingly.

---

### Post by arcadeportal32 on 2018-04-21
Ill have to try some of the lighter distros as you said, I hope they don't have the same errors as the others trying to install.

---

### Post by arcadeportal32 on 2018-04-22
I guess should I try a lower version, every single 16.04 distro I have thrown at it has crashed with the Error I posted before?

Edit: I have booted a copy of Lubuntu 14.04 and it seems to be working so far, gotten past Lubuntu loading screen and mouse is currently working. Waiting for more prompts to show up lol.


EDIT EDIT: Alright I got Lubuntu on, however my desktop is blank with no icons visible. But the background is there, and I can access the terminal & desktop prefs. I currently have it on Try before install mode from the launcher. Help?

EDIT EDIT EDIT: It seams to be fully working now, it is installing :"D

---

### Post by kerry_s on 2018-04-22
cause:
> Minimum hardware requirements for Lubuntu:
RAM: 512 MB of RAM (recommended 1GB)
CPU: Pentium 4 or Pentium M or AMD K8 or higher

---

