---
title: "Can't install Ubunutu or Kubuntu 15/14.04 on windows 10 machine, blank screen"
date: 2015-09-20
forum: Installation &amp; Upgrades
---

### Post by Christopher_Bell on 2015-09-20
I'm having a lot of trouble and have been at it for a while today with no avail.

My machine has Windows 10, upgraded from Windows 8.1. I would like to install Ubuntu or Kubuntu as a dual boot, but I have UEFI. 

I created two bootable USB drives, one for each, and neither work. Once it brings me to the UEFI selection menu, if I select any option that could further the installation process (try Ubuntu or install) my screen stays blank, sometimes with my monitors going in and out of power saving state sometimes or just staying entirely blank. I'm not sure if it helps, but here's a dxdiag for any specs that are needed to be found ```
------------------
System Information
------------------
      Time of this report: 9/21/2015, 03:44:29
             Machine name: CHRISTOPHERS
         Operating System: Windows 10 Pro 64-bit (10.0, Build 10240) (10240.th1.150819-1946)
                 Language: English (Regional Setting: English)
      System Manufacturer: MSI
             System Model: MS-7885
                     BIOS: Default System BIOS
                Processor: Intel(R) Core(TM) i7-5820K CPU @ 3.30GHz (12 CPUs), ~3.3GHz
                   Memory: 16384MB RAM
      Available OS Memory: 16280MB RAM
                Page File: 4129MB used, 32629MB available
              Windows Dir: C:\WINDOWS
          DirectX Version: 12
      DX Setup Parameters: Not found
         User DPI Setting: 112 DPI (116 percent)
       System DPI Setting: 96 DPI (100 percent)
          DWM DPI Scaling: Enabled
                 Miracast: Available, with HDCP
Microsoft Graphics Hybrid: Not Supported
           DxDiag Version: 10.00.10240.16384 64bit Unicode


------------
DxDiag Notes
------------
      Display Tab 1: No problems found.
      Display Tab 2: No problems found.
        Sound Tab 1: No problems found.
        Sound Tab 2: No problems found.
        Sound Tab 3: No problems found.
          Input Tab: No problems found.


--------------------
DirectX Debug Levels
--------------------
Direct3D:    0/4 (retail)
DirectDraw:  0/4 (retail)
DirectInput: 0/5 (retail)
DirectMusic: 0/5 (retail)
DirectPlay:  0/9 (retail)
DirectSound: 0/5 (retail)
DirectShow:  0/6 (retail)


---------------
Display Devices
---------------
          Card name: NVIDIA GeForce GTX 980
       Manufacturer: NVIDIA
          Chip type: GeForce GTX 980
           DAC type: Integrated RAMDAC
        Device Type: Full Device
         Device Key: Enum\PCI\VEN_10DE&DEV_13C0&SUBSYS_31701462&REV_A1
     Display Memory: 12149 MB
   Dedicated Memory: 4009 MB
      Shared Memory: 8139 MB
       Current Mode: 2560 x 1440 (32 bit) (59Hz)
       Monitor Name: Dell U2713HM (DP)
      Monitor Model: DELL U2713HM
         Monitor Id: DEL4080
        Native Mode: 2560 x 1440(p) (59.951Hz)
        Output Type: Displayport External
        Driver Name: nvd3dumx.dll,nvwgf2umx.dll,nvwgf2umx.dll,nvwgf2umx.dll,nvd3dum,nvwgf2um,nvwgf2um,nvwgf2um
Driver File Version: 10.18.0013.5362 (English)
     Driver Version: 10.18.13.5362
        DDI Version: 12
     Feature Levels: 12.1,12.0,11.1,11.0,10.1,10.0,9.3,9.2,9.1
       Driver Model: WDDM 2.0
Graphics Preemption: DMA
 Compute Preemption: DMA
           Miracast: Not Supported by Graphics driver
Hybrid Graphics GPU: Not Supported
     Power P-states: Not Supported
  Driver Attributes: Final Retail
   Driver Date/Size: 7/23/2015 04:02:12, 16011680 bytes
        WHQL Logo'd: n/a
    WHQL Date Stamp: n/a
  Device Identifier: {D7B71E3E-5080-11CF-2063-7D111CC2C735}
          Vendor ID: 0x10DE
          Device ID: 0x13C0
          SubSys ID: 0x31701462
        Revision ID: 0x00A1
 Driver Strong Name: oem272.inf:0f066de3ad09d9de:Section044:10.18.13.5362:pci\ven_10de&dev_13c0
     Rank Of Driver: 00D12001
        Video Accel: 
        DXVA2 Modes: DXVA2_ModeMPEG2_VLD  DXVA2_ModeVC1_D2010  DXVA2_ModeVC1_VLD  DXVA2_ModeH264_VLD_Stereo_Progressive_NoFGT  DXVA2_ModeH264_VLD_Stereo_NoFGT  DXVA2_ModeH264_VLD_NoFGT  DXVA2_ModeHEVC_VLD_Main  DXVA2_ModeMPEG4pt2_VLD_Simple  DXVA2_ModeMPEG4pt2_VLD_AdvSimple_NoGMC  
   Deinterlace Caps: {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                     {F9F19DA5-3B09-4B2F-9D89-C64753E3EAAB}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY 
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY 
                     {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                     {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(UYVY,UYVY) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                     {F9F19DA5-3B09-4B2F-9D89-C64753E3EAAB}: Format(In/Out)=(UYVY,UYVY) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY 
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(UYVY,UYVY) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY 
                     {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(UYVY,UYVY) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                     {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(YV12,0x32315659) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                     {F9F19DA5-3B09-4B2F-9D89-C64753E3EAAB}: Format(In/Out)=(YV12,0x32315659) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY 
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(YV12,0x32315659) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY 
                     {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YV12,0x32315659) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                     {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                     {F9F19DA5-3B09-4B2F-9D89-C64753E3EAAB}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY 
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY 
                     {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                     {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(IMC1,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {F9F19DA5-3B09-4B2F-9D89-C64753E3EAAB}: Format(In/Out)=(IMC1,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(IMC1,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(IMC1,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(IMC2,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {F9F19DA5-3B09-4B2F-9D89-C64753E3EAAB}: Format(In/Out)=(IMC2,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(IMC2,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(IMC2,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(IMC3,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {F9F19DA5-3B09-4B2F-9D89-C64753E3EAAB}: Format(In/Out)=(IMC3,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(IMC3,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(IMC3,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(IMC4,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {F9F19DA5-3B09-4B2F-9D89-C64753E3EAAB}: Format(In/Out)=(IMC4,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(IMC4,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(IMC4,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(S340,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {F9F19DA5-3B09-4B2F-9D89-C64753E3EAAB}: Format(In/Out)=(S340,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(S340,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(S340,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(S342,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {F9F19DA5-3B09-4B2F-9D89-C64753E3EAAB}: Format(In/Out)=(S342,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(S342,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(S342,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
       D3D9 Overlay: Supported
            DXVA-HD: Supported
       DDraw Status: Enabled
         D3D Status: Enabled
         AGP Status: Enabled


          Card name: NVIDIA GeForce GTX 980
       Manufacturer: NVIDIA
          Chip type: GeForce GTX 980
           DAC type: Integrated RAMDAC
        Device Type: Full Device
         Device Key: Enum\PCI\VEN_10DE&DEV_13C0&SUBSYS_31701462&REV_A1
     Display Memory: 12149 MB
   Dedicated Memory: 4009 MB
      Shared Memory: 8139 MB
       Current Mode: 1920 x 1080 (32 bit) (60Hz)
       Monitor Name: Generic PnP Monitor
      Monitor Model: DELL U2414H
         Monitor Id: DELA0A3
        Native Mode: 1920 x 1080(p) (60.000Hz)
        Output Type: Displayport External
        Driver Name: nvd3dumx.dll,nvwgf2umx.dll,nvwgf2umx.dll,nvwgf2umx.dll,nvd3dum,nvwgf2um,nvwgf2um,nvwgf2um
Driver File Version: 10.18.0013.5362 (English)
     Driver Version: 10.18.13.5362
        DDI Version: 12
     Feature Levels: 12.1,12.0,11.1,11.0,10.1,10.0,9.3,9.2,9.1
       Driver Model: WDDM 2.0
Graphics Preemption: DMA
 Compute Preemption: DMA
           Miracast: Not Supported by Graphics driver
Hybrid Graphics GPU: Not Supported
     Power P-states: Not Supported
  Driver Attributes: Final Retail
   Driver Date/Size: 7/23/2015 04:02:12, 16011680 bytes
        WHQL Logo'd: n/a
    WHQL Date Stamp: n/a
  Device Identifier: {D7B71E3E-5080-11CF-2063-7D111CC2C735}
          Vendor ID: 0x10DE
          Device ID: 0x13C0
          SubSys ID: 0x31701462
        Revision ID: 0x00A1
 Driver Strong Name: oem272.inf:0f066de3ad09d9de:Section044:10.18.13.5362:pci\ven_10de&dev_13c0
     Rank Of Driver: 00D12001
        Video Accel: 
        DXVA2 Modes: DXVA2_ModeMPEG2_VLD  DXVA2_ModeVC1_D2010  DXVA2_ModeVC1_VLD  DXVA2_ModeH264_VLD_Stereo_Progressive_NoFGT  DXVA2_ModeH264_VLD_Stereo_NoFGT  DXVA2_ModeH264_VLD_NoFGT  DXVA2_ModeHEVC_VLD_Main  DXVA2_ModeMPEG4pt2_VLD_Simple  DXVA2_ModeMPEG4pt2_VLD_AdvSimple_NoGMC  
   Deinterlace Caps: {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                     {F9F19DA5-3B09-4B2F-9D89-C64753E3EAAB}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY 
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY 
                     {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                     {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(UYVY,UYVY) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                     {F9F19DA5-3B09-4B2F-9D89-C64753E3EAAB}: Format(In/Out)=(UYVY,UYVY) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY 
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(UYVY,UYVY) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY 
                     {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(UYVY,UYVY) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                     {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(YV12,0x32315659) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                     {F9F19DA5-3B09-4B2F-9D89-C64753E3EAAB}: Format(In/Out)=(YV12,0x32315659) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY 
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(YV12,0x32315659) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY 
                     {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YV12,0x32315659) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                     {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                     {F9F19DA5-3B09-4B2F-9D89-C64753E3EAAB}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY 
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY 
                     {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                     {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(IMC1,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {F9F19DA5-3B09-4B2F-9D89-C64753E3EAAB}: Format(In/Out)=(IMC1,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(IMC1,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(IMC1,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(IMC2,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {F9F19DA5-3B09-4B2F-9D89-C64753E3EAAB}: Format(In/Out)=(IMC2,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(IMC2,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(IMC2,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(IMC3,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {F9F19DA5-3B09-4B2F-9D89-C64753E3EAAB}: Format(In/Out)=(IMC3,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(IMC3,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(IMC3,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(IMC4,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {F9F19DA5-3B09-4B2F-9D89-C64753E3EAAB}: Format(In/Out)=(IMC4,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(IMC4,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(IMC4,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(S340,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {F9F19DA5-3B09-4B2F-9D89-C64753E3EAAB}: Format(In/Out)=(S340,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(S340,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(S340,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {6CB69578-7617-4637-91E5-1C02DB810285}: Format(In/Out)=(S342,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {F9F19DA5-3B09-4B2F-9D89-C64753E3EAAB}: Format(In/Out)=(S342,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(S342,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                     {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(S342,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
       D3D9 Overlay: Supported
            DXVA-HD: Supported
       DDraw Status: Enabled
         D3D Status: Enabled
         AGP Status: Enabled


-------------
Sound Devices
-------------
            Description: Speakers (Realtek High Definition Audio)
 Default Sound Playback: Yes
 Default Voice Playback: Yes
            Hardware ID: HDAUDIO\FUNC_01&VEN_10EC&DEV_0892&SUBSYS_1462D885&REV_1003
        Manufacturer ID: 1
             Product ID: 100
                   Type: WDM
            Driver Name: RTKVHD64.sys
         Driver Version: 6.00.0001.7535 (English)
      Driver Attributes: Final Retail
            WHQL Logo'd: n/a
          Date and Size: 6/24/2015 22:57:00, 4504320 bytes
            Other Files: 
        Driver Provider: Realtek Semiconductor Corp.
         HW Accel Level: Basic
              Cap Flags: 0x0
    Min/Max Sample Rate: 0, 0
Static/Strm HW Mix Bufs: 0, 0
 Static/Strm HW 3D Bufs: 0, 0
              HW Memory: 0
       Voice Management: No
 EAX(tm) 2.0 Listen/Src: No, No
   I3DL2(tm) Listen/Src: No, No
Sensaura(tm) ZoomFX(tm): No


            Description: Realtek Digital Output (Realtek High Definition Audio)
 Default Sound Playback: No
 Default Voice Playback: No
            Hardware ID: HDAUDIO\FUNC_01&VEN_10EC&DEV_0892&SUBSYS_1462D885&REV_1003
        Manufacturer ID: 1
             Product ID: 100
                   Type: WDM
            Driver Name: RTKVHD64.sys
         Driver Version: 6.00.0001.7535 (English)
      Driver Attributes: Final Retail
            WHQL Logo'd: n/a
          Date and Size: 6/24/2015 22:57:00, 4504320 bytes
            Other Files: 
        Driver Provider: Realtek Semiconductor Corp.
         HW Accel Level: Basic
              Cap Flags: 0x0
    Min/Max Sample Rate: 0, 0
Static/Strm HW Mix Bufs: 0, 0
 Static/Strm HW 3D Bufs: 0, 0
              HW Memory: 0
       Voice Management: No
 EAX(tm) 2.0 Listen/Src: No, No
   I3DL2(tm) Listen/Src: No, No
Sensaura(tm) ZoomFX(tm): No


            Description: Realtek HD Audio 2nd output (Realtek High Definition Audio)
 Default Sound Playback: No
 Default Voice Playback: No
            Hardware ID: HDAUDIO\FUNC_01&VEN_10EC&DEV_0892&SUBSYS_1462D885&REV_1003
        Manufacturer ID: 1
             Product ID: 100
                   Type: WDM
            Driver Name: RTKVHD64.sys
         Driver Version: 6.00.0001.7535 (English)
      Driver Attributes: Final Retail
            WHQL Logo'd: n/a
          Date and Size: 6/24/2015 22:57:00, 4504320 bytes
            Other Files: 
        Driver Provider: Realtek Semiconductor Corp.
         HW Accel Level: Basic
              Cap Flags: 0x0
    Min/Max Sample Rate: 0, 0
Static/Strm HW Mix Bufs: 0, 0
 Static/Strm HW 3D Bufs: 0, 0
              HW Memory: 0
       Voice Management: No
 EAX(tm) 2.0 Listen/Src: No, No
   I3DL2(tm) Listen/Src: No, No
Sensaura(tm) ZoomFX(tm): No


---------------------
Sound Capture Devices
---------------------
            Description: Microphone (Blue Snowball)
  Default Sound Capture: Yes
  Default Voice Capture: Yes
            Driver Name: CMUSBDAC.sys
         Driver Version: 8.01.0014.7043 (English)
      Driver Attributes: Final Retail
          Date and Size: 9/19/2014 05:58:34, 595456 bytes
              Cap Flags: 0x0
           Format Flags: 0x0


            Description: Microphone (ManyCam Virtual Microphone)
  Default Sound Capture: No
  Default Voice Capture: No
            Driver Name: mcaudrv_x64.sys
         Driver Version: 4.00.0000.0000 (English)
      Driver Attributes: Final Retail
          Date and Size: 11/10/2014 04:49:50, 36000 bytes
              Cap Flags: 0x0
           Format Flags: 0x0


            Description: Microphone (Realtek High Definition Audio)
  Default Sound Capture: No
  Default Voice Capture: No
            Driver Name: RTKVHD64.sys
         Driver Version: 6.00.0001.7535 (English)
      Driver Attributes: Final Retail
          Date and Size: 6/24/2015 22:57:00, 4504320 bytes
              Cap Flags: 0x0
           Format Flags: 0x0


---------------------
Video Capture Devices
Number of Devices: 1
---------------------
           FriendlyName: ManyCam Virtual Webcam
               Location: n/a
           SymbolicLink: \\?\root#image#0001#{e5323777-f976-4f5b-9b55-b94699c46e44}\global
           Manufacturer: Visicom Media Inc.
             HardwareID: MANYCAM
             DriverDesc: ManyCam Virtual Webcam
         DriverProvider: Visicom Media Inc.
          DriverVersion: 4.1.200.0
      DriverDateEnglish: 10/22/2014 00:00:00
    DriverDateLocalized: 10/22/2014 12:00:00 AM
                Service: ManyCam
                  Class: Image
          DevNodeStatus: 180200B[DN_ROOT_ENUMERATED|DN_DRIVER_LOADED|DN_STARTED|DN_DISABLEABLE|DN_NT_ENUMERATOR|DN_NT_DRIVER]
            ContainerId: {00000000-0000-0000-FFFF-FFFFFFFFFFFF}
            ProblemCode: No Problem
  BusReportedDeviceDesc: n/a
                 Parent: HTREE\ROOT\0
      DriverProblemDesc: n/a
           UpperFilters: n/a
           LowerFilters: n/a
                  Stack: \Driver\ksthunk,\Driver\ManyCam,\Driver\PnpManager
      ContainerCategory: Imaging


-------------------
DirectInput Devices
-------------------
      Device Name: Mouse
         Attached: 1
    Controller ID: n/a
Vendor/Product ID: n/a
        FF Driver: n/a


      Device Name: Keyboard
         Attached: 1
    Controller ID: n/a
Vendor/Product ID: n/a
        FF Driver: n/a


      Device Name: Razer Naga Epic Chroma
         Attached: 1
    Controller ID: 0x0
Vendor/Product ID: 0x1532, 0x003E
        FF Driver: n/a


      Device Name: Razer BlackWidow Ultimate
         Attached: 1
    Controller ID: 0x0
Vendor/Product ID: 0x1532, 0x011A
        FF Driver: n/a


      Device Name: Razer Naga Epic Chroma
         Attached: 1
    Controller ID: 0x0
Vendor/Product ID: 0x1532, 0x003E
        FF Driver: n/a


      Device Name: Razer BlackWidow Ultimate
         Attached: 1
    Controller ID: 0x0
Vendor/Product ID: 0x1532, 0x011A
        FF Driver: n/a


      Device Name: Wacom Tablet
         Attached: 1
    Controller ID: 0x0
Vendor/Product ID: 0x056A, 0x0302
        FF Driver: n/a


      Device Name: Wacom Tablet
         Attached: 1
    Controller ID: 0x0
Vendor/Product ID: 0x056A, 0x0302
        FF Driver: n/a


      Device Name: Razer Naga Epic Chroma
         Attached: 1
    Controller ID: 0x0
Vendor/Product ID: 0x1532, 0x003E
        FF Driver: n/a


      Device Name: Razer BlackWidow Ultimate
         Attached: 1
    Controller ID: 0x0
Vendor/Product ID: 0x1532, 0x011A
        FF Driver: n/a


      Device Name: Wacom Tablet
         Attached: 1
    Controller ID: 0x0
Vendor/Product ID: 0x056A, 0x0302
        FF Driver: n/a


      Device Name: Razer Naga Epic Chroma
         Attached: 1
    Controller ID: 0x0
Vendor/Product ID: 0x1532, 0x003E
        FF Driver: n/a


      Device Name: Razer BlackWidow Ultimate
         Attached: 1
    Controller ID: 0x0
Vendor/Product ID: 0x1532, 0x011A
        FF Driver: n/a


      Device Name: Blue Snowball 
         Attached: 1
    Controller ID: 0x0
Vendor/Product ID: 0x0D8C, 0x0005
        FF Driver: n/a


Poll w/ Interrupt: No


-----------
USB Devices
-----------
+ USB Root Hub (xHCI)
| Vendor/Product ID: 0x1106, 0x3483
| Matching Device ID: USB\ROOT_HUB30
| Service: USBHUB3
| Driver: USBHUB3.SYS, 8/2/2015 21:17:45, 516960 bytes
| 
+-+ Generic USB Hub
| | Vendor/Product ID: 0x2109, 0x3431
| | Location: Port_#0001.Hub_#0004
| | Matching Device ID: USB\USB20_HUB
| | Service: USBHUB3
| | Driver: USBHUB3.SYS, 8/2/2015 21:17:45, 516960 bytes
| | 
| +-+ USB Composite Device
| | | Vendor/Product ID: 0x1532, 0x011A
| | | Location: Port_#0002.Hub_#0007
| | | Matching Device ID: USB\COMPOSITE
| | | Service: usbccgp
| | | Driver: usbccgp.sys, 7/10/2015 05:59:39, 159072 bytes
| | | 
| | +-+ Razer BlackWidow Ultimate
| | | | Vendor/Product ID: 0x1532, 0x011A
| | | | Location: 0007.0000.0000.001.002.000.000.000.000
| | | | Matching Device ID: usb\vid_1532&pid_011a&mi_00
| | | | Service: HidUsb
| | | | Driver: RzWizardPkg.exe, 7/27/2015 09:21:18, 3188056 bytes
| | | | Driver: hidusb.sys, 7/10/2015 05:59:38, 38400 bytes
| | | | Driver: hidclass.sys, 7/10/2015 05:59:38, 153088 bytes
| | | | Driver: hidparse.sys, 7/10/2015 05:59:38, 39936 bytes
| | | | Driver: RazerCoinstaller.dll, 7/27/2015 09:21:08, 89104 bytes
| | | | 
| | | +-+ HID Keyboard Device
| | | | | Vendor/Product ID: 0x1532, 0x011A
| | | | | Matching Device ID: HID_DEVICE_SYSTEM_KEYBOARD
| | | | | Service: kbdhid
| | | | | Driver: kbdhid.sys, 7/10/2015 05:59:38, 36864 bytes
| | | | | Driver: kbdclass.sys, 7/10/2015 05:59:38, 62304 bytes
| | | | 
| | +-+ Razer BlackWidow Ultimate
| | | | Vendor/Product ID: 0x1532, 0x011A
| | | | Location: 0007.0000.0000.001.002.000.000.000.000
| | | | Matching Device ID: USB\VID_1532&PID_011A&MI_01
| | | | Lower Filters: rzendpt
| | | | Service: HidUsb
| | | | Driver: rzendpt.sys, 8/13/2015 10:36:50, 50392 bytes
| | | | Driver: hidusb.sys, 7/10/2015 05:59:38, 38400 bytes
| | | | Driver: hidclass.sys, 7/10/2015 05:59:38, 153088 bytes
| | | | Driver: hidparse.sys, 7/10/2015 05:59:38, 39936 bytes
| | | | Driver: WdfCoInstaller01009.dll, 9/14/2015 18:48:39, 1730328 bytes
| | | | 
| | | +-+ Razer BlackWidow Ultimate
| | | | | Vendor/Product ID: 0x1532, 0x011A
| | | | | Matching Device ID: HID\VID_1532&PID_011A&MI_01&Col01
| | | | | Upper Filters: rzudd
| | | | | Service: kbdhid
| | | | | Driver: rzudd.sys, 9/14/2015 18:48:39, 202952 bytes
| | | | | Driver: kbdhid.sys, 7/10/2015 05:59:38, 36864 bytes
| | | | | Driver: kbdclass.sys, 7/10/2015 05:59:38, 62304 bytes
| | | | | Driver: WdfCoInstaller01009.dll, 9/14/2015 18:48:39, 1730328 bytes
| | | | 
| | +-+ USB Input Device
| | | | Vendor/Product ID: 0x1532, 0x011A
| | | | Location: 0007.0000.0000.001.002.000.000.000.000
| | | | Matching Device ID: USB\Class_03
| | | | Service: HidUsb
| | | | Driver: hidusb.sys, 7/10/2015 05:59:38, 38400 bytes
| | | | Driver: hidclass.sys, 7/10/2015 05:59:38, 153088 bytes
| | | | Driver: hidparse.sys, 7/10/2015 05:59:38, 39936 bytes
| | | | 
| | | +-+ Razer BlackWidow Ultimate
| | | | | Vendor/Product ID: 0x1532, 0x011A
| | | | | Matching Device ID: HID\VID_1532&PID_011A&MI_02
| | | | | Upper Filters: rzudd
| | | | | Service: mouhid
| | | | | Driver: rzudd.sys, 9/14/2015 18:48:39, 202952 bytes
| | | | | Driver: mouhid.sys, 7/10/2015 05:59:39, 32256 bytes
| | | | | Driver: mouclass.sys, 7/10/2015 05:59:39, 59232 bytes
| | | | | Driver: WdfCoInstaller01009.dll, 9/14/2015 18:48:39, 1730328 bytes
| | | 
| +-+ Generic USB Hub
| | | Vendor/Product ID: 0x0451, 0x8043
| | | Location: Port_#0003.Hub_#0007
| | | Matching Device ID: USB\USB20_HUB
| | | Service: USBHUB3
| | | Driver: USBHUB3.SYS, 8/2/2015 21:17:45, 516960 bytes
| | | 
| | +-+ Wacom Tablet
| | | | Vendor/Product ID: 0x056A, 0x0302
| | | | Location: Port_#0001.Hub_#0009
| | | | Matching Device ID: USB\VID_056A&PID_0302
| | | | Upper Filters: hidkmdf
| | | | Service: WacHidRouter
| | | | Driver: wachidrouter.sys, 10/25/2014 15:52:20, 100664 bytes
| | | | Driver: hidkmdf.sys, 10/25/2014 15:52:20, 14136 bytes
| | | | Driver: wdfcoinstaller01009.dll, 9/14/2015 18:48:39, 1730328 bytes
| | | | 
| | | +-+ HID-Compliant Mouse
| | | | | Vendor/Product ID: 0x056A, 0x0302
| | | | | Matching Device ID: HID\VID_056A&PID_0302&Col01
| | | | | Upper Filters: wacomrouterfilter
| | | | | Service: mouhid
| | | | | Driver: wacomrouterfilter.sys, 10/25/2014 15:52:20, 15160 bytes
| | | | | Driver: mouhid.sys, 7/10/2015 05:59:39, 32256 bytes
| | | | | Driver: mouclass.sys, 7/10/2015 05:59:39, 59232 bytes
| | | | | Driver: wdfcoinstaller01009.dll, 12/11/2012 17:12:00, 1721576 bytes
| | | 
| +-+ USB Composite Device
| | | Vendor/Product ID: 0x1532, 0x003E
| | | Location: Port_#0004.Hub_#0007
| | | Matching Device ID: USB\COMPOSITE
| | | Service: usbccgp
| | | Driver: usbccgp.sys, 7/10/2015 05:59:39, 159072 bytes
| | | 
| | +-+ Razer Naga Epic Chroma
| | | | Vendor/Product ID: 0x1532, 0x003E
| | | | Location: 0007.0000.0000.001.004.000.000.000.000
| | | | Matching Device ID: USB\VID_1532&PID_003E&MI_00
| | | | Lower Filters: rzmpos
| | | | Service: HidUsb
| | | | Driver: rzmpos.sys, 8/13/2015 10:36:50, 48840 bytes
| | | | Driver: hidusb.sys, 7/10/2015 05:59:38, 38400 bytes
| | | | Driver: hidclass.sys, 7/10/2015 05:59:38, 153088 bytes
| | | | Driver: hidparse.sys, 7/10/2015 05:59:38, 39936 bytes
| | | | Driver: WdfCoInstaller01009.dll, 9/14/2015 18:48:39, 1730328 bytes
| | | | 
| | | +-+ Razer Naga Epic Chroma
| | | | | Vendor/Product ID: 0x1532, 0x003E
| | | | | Matching Device ID: HID\VID_1532&PID_003E&MI_00
| | | | | Upper Filters: rzudd
| | | | | Service: mouhid
| | | | | Driver: rzudd.sys, 9/14/2015 18:48:39, 202952 bytes
| | | | | Driver: mouhid.sys, 7/10/2015 05:59:39, 32256 bytes
| | | | | Driver: mouclass.sys, 7/10/2015 05:59:39, 59232 bytes
| | | | | Driver: WdfCoInstaller01009.dll, 9/14/2015 18:48:39, 1730328 bytes
| | | | 
| | +-+ USB Input Device
| | | | Vendor/Product ID: 0x1532, 0x003E
| | | | Location: 0007.0000.0000.001.004.000.000.000.000
| | | | Matching Device ID: USB\Class_03
| | | | Service: HidUsb
| | | | Driver: hidusb.sys, 7/10/2015 05:59:38, 38400 bytes
| | | | Driver: hidclass.sys, 7/10/2015 05:59:38, 153088 bytes
| | | | Driver: hidparse.sys, 7/10/2015 05:59:38, 39936 bytes
| | | | 
| | | +-+ Razer Naga Epic Chroma
| | | | | Vendor/Product ID: 0x1532, 0x003E
| | | | | Matching Device ID: HID\VID_1532&PID_003E&MI_01
| | | | | Upper Filters: rzudd
| | | | | Service: kbdhid
| | | | | Driver: rzudd.sys, 9/14/2015 18:48:39, 202952 bytes
| | | | | Driver: kbdhid.sys, 7/10/2015 05:59:38, 36864 bytes
| | | | | Driver: kbdclass.sys, 7/10/2015 05:59:38, 62304 bytes
| | | | | Driver: WdfCoInstaller01009.dll, 9/14/2015 18:48:39, 1730328 bytes
| | | | 
| | +-+ Razer Naga Epic Chroma
| | | | Vendor/Product ID: 0x1532, 0x003E
| | | | Location: 0007.0000.0000.001.004.000.000.000.000
| | | | Matching Device ID: usb\vid_1532&pid_003e&mi_02
| | | | Service: HidUsb
| | | | Driver: RzWizardPkg.exe, 7/27/2015 09:21:18, 3188056 bytes
| | | | Driver: hidusb.sys, 7/10/2015 05:59:38, 38400 bytes
| | | | Driver: hidclass.sys, 7/10/2015 05:59:38, 153088 bytes
| | | | Driver: hidparse.sys, 7/10/2015 05:59:38, 39936 bytes
| | | | Driver: RazerCoinstaller.dll, 7/27/2015 09:21:08, 89104 bytes
| | | | 
| | | +-+ HID Keyboard Device
| | | | | Vendor/Product ID: 0x1532, 0x003E
| | | | | Matching Device ID: HID_DEVICE_SYSTEM_KEYBOARD
| | | | | Service: kbdhid
| | | | | Driver: kbdhid.sys, 7/10/2015 05:59:38, 36864 bytes
| | | | | Driver: kbdclass.sys, 7/10/2015 05:59:38, 62304 bytes


----------------
Gameport Devices
----------------


------------
PS/2 Devices
------------


------------------------
Disk & DVD/CD-ROM Drives
------------------------
      Drive: C:
 Free Space: 10.2 GB
Total Space: 121.3 GB
File System: NTFS
      Model: APOTOP SSD S3C


      Drive: D:
 Free Space: 449.2 GB
Total Space: 953.9 GB
File System: NTFS
      Model: WDC WD10EZEX-08M2NA0


      Drive: E:
 Free Space: 99.9 GB
Total Space: 100.0 GB
File System: NTFS
      Model: WDC WD20EZRX-00D8PB0


      Drive: G:
 Free Space: 1807.5 GB
Total Space: 1807.7 GB
File System: NTFS
      Model: WDC WD20EZRX-00D8PB0


      Drive: F:
      Model: TSSTcorp CDDVDW SH-224DB
     Driver: c:\windows\system32\drivers\cdrom.sys, 10.00.10240.16384 (English), 7/10/2015 05:59:39, 174080 bytes


--------------
System Devices
--------------
     Name: Standard SATA AHCI Controller
Device ID: PCI\VEN_8086&DEV_8D62&SUBSYS_78851462&REV_05\3&11583659&1&8C
   Driver: C:\WINDOWS\system32\DRIVERS\storahci.sys, 10.00.10240.16384 (English), 7/10/2015 05:59:39, 133984 bytes


     Name: VIA USB 3.0 eXtensible Host Controller - 1.0 (Microsoft)
Device ID: PCI\VEN_1106&DEV_3483&SUBSYS_78851462&REV_01\4&167045A8&0&00E3
   Driver: C:\WINDOWS\system32\DRIVERS\USBXHCI.SYS, 10.00.10240.16461 (English), 8/18/2015 02:55:45, 373072 bytes


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FAC&SUBSYS_2FAC8086&REV_02\3&103A9D54&0&9C
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2F8A&SUBSYS_00000000&REV_02\3&103A9D54&0&FA
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FAA&SUBSYS_2FAA8086&REV_02\3&103A9D54&0&9A
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2F98&SUBSYS_2F988086&REV_02\3&103A9D54&0&F0
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FE5&SUBSYS_00001462&REV_02\3&103A9D54&0&65
   Driver: n/a


     Name: Standard Enhanced PCI to USB Host Controller
Device ID: PCI\VEN_8086&DEV_8D26&SUBSYS_78851462&REV_05\3&11583659&1&E8
   Driver: C:\WINDOWS\system32\drivers\usbehci.sys, 10.00.10240.16384 (English), 7/10/2015 05:59:39, 95584 bytes
   Driver: C:\WINDOWS\system32\drivers\usbport.sys, 10.00.10240.16384 (English), 7/10/2015 05:59:39, 457056 bytes
   Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 10.00.10240.16401 (English), 7/29/2015 21:11:22, 498016 bytes


     Name: High Definition Audio Controller
Device ID: PCI\VEN_8086&DEV_8D20&SUBSYS_D8851462&REV_05\3&11583659&1&D8
   Driver: C:\WINDOWS\system32\DRIVERS\hdaudbus.sys, 10.00.10240.16384 (English), 7/10/2015 05:59:36, 80896 bytes
   Driver: C:\WINDOWS\system32\drivers\drmk.sys, 10.00.10240.16384 (English), 7/10/2015 05:59:36, 96768 bytes
   Driver: C:\WINDOWS\system32\drivers\portcls.sys, 10.00.10240.16384 (English), 7/10/2015 05:59:36, 320512 bytes


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2F34&SUBSYS_2F348086&REV_02\3&103A9D54&0&81
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FAF&SUBSYS_00000000&REV_02\3&103A9D54&0&9F
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2F37&SUBSYS_78851462&REV_02\3&103A9D54&0&5A
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2F30&SUBSYS_2F308086&REV_02\3&103A9D54&0&91
   Driver: n/a


     Name: PCI Express Root Port
Device ID: PCI\VEN_8086&DEV_2F02&SUBSYS_78851462&REV_02\3&11583659&1&08
   Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 10.00.10240.16390 (English), 7/29/2015 21:11:22, 325984 bytes


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FFD&SUBSYS_00001462&REV_02\3&103A9D54&0&7D
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FE0&SUBSYS_00001462&REV_02\3&103A9D54&0&60
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FBB&SUBSYS_00000000&REV_02\3&103A9D54&0&BF
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FC0&SUBSYS_2FC08086&REV_02\3&103A9D54&0&F3
   Driver: n/a


     Name: Standard Enhanced PCI to USB Host Controller
Device ID: PCI\VEN_8086&DEV_8D2D&SUBSYS_78851462&REV_05\3&11583659&1&D0
   Driver: C:\WINDOWS\system32\drivers\usbehci.sys, 10.00.10240.16384 (English), 7/10/2015 05:59:39, 95584 bytes
   Driver: C:\WINDOWS\system32\drivers\usbport.sys, 10.00.10240.16384 (English), 7/10/2015 05:59:39, 457056 bytes
   Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 10.00.10240.16401 (English), 7/29/2015 21:11:22, 498016 bytes


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FF9&SUBSYS_00000000&REV_02\3&103A9D54&0&79
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FE3&SUBSYS_00001462&REV_02\3&103A9D54&0&63
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2F6E&SUBSYS_00000000&REV_02\3&103A9D54&0&B6
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2F7D&SUBSYS_2F7D8086&REV_02\3&103A9D54&0&86
   Driver: n/a


     Name: PCI Express Root Port
Device ID: PCI\VEN_8086&DEV_2F03&SUBSYS_00008086&REV_02\3&11583659&1&09
   Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 10.00.10240.16390 (English), 7/29/2015 21:11:22, 325984 bytes


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FBE&SUBSYS_00000000&REV_02\3&103A9D54&0&A6
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2F1F&SUBSYS_2F1F8086&REV_02\3&103A9D54&0&87
   Driver: n/a


     Name: PCI Express Root Port
Device ID: PCI\VEN_8086&DEV_2F08&SUBSYS_78851462&REV_02\3&11583659&1&18
   Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 10.00.10240.16390 (English), 7/29/2015 21:11:22, 325984 bytes


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FB7&SUBSYS_2FB78086&REV_02\3&103A9D54&0&AB
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2F1D&SUBSYS_2F1D8086&REV_02\3&103A9D54&0&80
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FB5&SUBSYS_2FB58086&REV_02\3&103A9D54&0&A9
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FB3&SUBSYS_2FB38086&REV_02\3&103A9D54&0&A3
   Driver: n/a


     Name: Standard SATA AHCI Controller
Device ID: PCI\VEN_8086&DEV_8D02&SUBSYS_78851462&REV_05\3&11583659&1&FA
   Driver: C:\WINDOWS\system32\DRIVERS\storahci.sys, 10.00.10240.16384 (English), 7/10/2015 05:59:39, 133984 bytes


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FB1&SUBSYS_2FB18086&REV_02\3&103A9D54&0&A1
   Driver: n/a


     Name: PCI standard host CPU bridge
Device ID: PCI\VEN_8086&DEV_2F00&SUBSYS_78851462&REV_02\3&11583659&1&00
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2F9C&SUBSYS_2F9C8086&REV_02\3&103A9D54&0&F4
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2F9A&SUBSYS_2F9A8086&REV_02\3&103A9D54&0&F2
   Driver: n/a


     Name: PCI Express Root Port
Device ID: PCI\VEN_8086&DEV_2F06&SUBSYS_00008086&REV_02\3&11583659&1&12
   Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 10.00.10240.16390 (English), 7/29/2015 21:11:22, 325984 bytes


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FAD&SUBSYS_2FAD8086&REV_02\3&103A9D54&0&9D
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2F68&SUBSYS_00000000&REV_02\3&103A9D54&0&B0
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FAB&SUBSYS_2FAB8086&REV_02\3&103A9D54&0&9B
   Driver: n/a


     Name: NVIDIA GeForce GTX 980
Device ID: PCI\VEN_10DE&DEV_13C0&SUBSYS_31701462&REV_A1\4&3733ABE7&0&0018
   Driver: C:\Program Files\NVIDIA Corporation\Drs\dbInstaller.exe, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 448144 bytes
   Driver: C:\Program Files\NVIDIA Corporation\Drs\nvdrsdb.bin, 7/23/2015 04:02:12, 1300484 bytes
   Driver: C:\WINDOWS\System32\DriverStore\FileRepository\nv_dispiwu.inf_amd64_81b753f5b6dc2d8a\NvCplSetupInt.exe, 1.00.0005.0000 (English), 7/29/2015 18:42:29, 95302112 bytes
   Driver: C:\Program Files (x86)\NVIDIA Corporation\coprocmanager\detoured.dll, 7/23/2015 04:02:12, 12104 bytes
   Driver: C:\Program Files (x86)\NVIDIA Corporation\coprocmanager\nvd3d9wrap.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 155952 bytes
   Driver: C:\Program Files (x86)\NVIDIA Corporation\coprocmanager\nvdxgiwrap.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 105328 bytes
   Driver: C:\Program Files\NVIDIA Corporation\coprocmanager\detoured.dll, 7/23/2015 04:02:12, 11920 bytes
   Driver: C:\Program Files\NVIDIA Corporation\coprocmanager\nvd3d9wrapx.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 185656 bytes
   Driver: C:\Program Files\NVIDIA Corporation\coprocmanager\nvdxgiwrapx.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 125576 bytes
   Driver: C:\Program Files\NVIDIA Corporation\license.txt, 7/23/2015 04:02:12, 21910 bytes
   Driver: C:\Program Files\NVIDIA Corporation\NVSMI\MCU.exe, 1.01.5204.20580 (English), 7/29/2015 18:42:28, 841360 bytes
   Driver: C:\Program Files\NVIDIA Corporation\NVSMI\nvdebugdump.exe, 6.14.0013.5362 (English), 7/29/2015 18:42:29, 227984 bytes
   Driver: C:\Program Files\NVIDIA Corporation\NVSMI\nvidia-smi.1.pdf, 7/29/2015 18:42:29, 72727 bytes
   Driver: C:\Program Files\NVIDIA Corporation\NVSMI\nvidia-smi.exe, 8.17.0013.5362 (English), 7/29/2015 18:42:29, 415560 bytes
   Driver: C:\Program Files\NVIDIA Corporation\NVSMI\nvml.dll, 8.17.0013.5362 (English), 7/29/2015 18:42:29, 1194640 bytes
   Driver: C:\Program Files\NVIDIA Corporation\OpenCL\OpenCL.dll, 1.02.0011.0000 (English), 7/23/2015 04:02:12, 105288 bytes
   Driver: C:\Program Files\NVIDIA Corporation\OpenCL\OpenCL64.dll, 1.02.0011.0000 (English), 7/23/2015 04:02:12, 112784 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\nvlddmkm.sys, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 11142984 bytes
   Driver: C:\WINDOWS\system32\NvFBC64.dll, 6.14.0013.5362 (English), 7/23/2015 04:02:12, 1053000 bytes
   Driver: C:\WINDOWS\system32\NvIFR64.dll, 6.14.0013.5362 (English), 7/23/2015 04:02:12, 1061008 bytes
   Driver: C:\WINDOWS\system32\NvIFROpenGL.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 408208 bytes
   Driver: C:\WINDOWS\system32\nvDecMFTMjpeg.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 374600 bytes
   Driver: C:\WINDOWS\system32\nvEncMFTH264.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 787384 bytes
   Driver: C:\WINDOWS\system32\nvEncMFThevc.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 785152 bytes
   Driver: C:\WINDOWS\system32\nvEncodeAPI64.dll, 6.14.0013.5362 (English), 7/23/2015 04:02:12, 384464 bytes
   Driver: C:\WINDOWS\system32\nvapi64.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 3351864 bytes
   Driver: C:\WINDOWS\system32\nvcompiler.dll, 7/23/2015 04:02:12, 42730312 bytes
   Driver: C:\WINDOWS\system32\nvcuda.dll, 8.17.0013.5362 (English), 7/23/2015 04:02:12, 14511608 bytes
   Driver: C:\WINDOWS\system32\nvcuvid.dll, 7.17.0013.5362 (English), 7/23/2015 04:02:12, 2360976 bytes
   Driver: C:\WINDOWS\system32\nvd3dumx.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 16011680 bytes
   Driver: C:\WINDOWS\system32\nvinfo.pb, 7/29/2015 18:42:29, 31976 bytes
   Driver: C:\WINDOWS\system32\nvinitx.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 176904 bytes
   Driver: C:\WINDOWS\system32\nvmcumd.dll, 7/23/2015 04:02:12, 601752 bytes
   Driver: C:\WINDOWS\system32\nvoglshim64.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 150832 bytes
   Driver: C:\WINDOWS\system32\nvoglv64.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 30518928 bytes
   Driver: C:\WINDOWS\system32\nvopencl.dll, 8.17.0013.5362 (English), 7/23/2015 04:02:12, 16160440 bytes
   Driver: C:\WINDOWS\system32\nvumdshimx.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 1165192 bytes
   Driver: C:\WINDOWS\system32\nvwgf2umx.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 18376584 bytes
   Driver: C:\WINDOWS\SysWow64\NvFBC.dll, 6.14.0013.5362 (English), 7/23/2015 04:02:12, 976528 bytes
   Driver: C:\WINDOWS\SysWow64\NvIFR.dll, 6.14.0013.5362 (English), 7/23/2015 04:02:12, 983368 bytes
   Driver: C:\WINDOWS\SysWow64\NvIFROpenGL.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 364360 bytes
   Driver: C:\WINDOWS\SysWow64\nvDecMFTMjpeg.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 340624 bytes
   Driver: C:\WINDOWS\SysWow64\nvEncMFTH264.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 632664 bytes
   Driver: C:\WINDOWS\SysWow64\nvEncMFThevc.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 631312 bytes
   Driver: C:\WINDOWS\SysWow64\nvEncodeAPI.dll, 6.14.0013.5362 (English), 7/23/2015 04:02:12, 314936 bytes
   Driver: C:\WINDOWS\SysWow64\nvapi.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 2963208 bytes
   Driver: C:\WINDOWS\SysWow64\nvcompiler.dll, 7/23/2015 04:02:12, 37749064 bytes
   Driver: C:\WINDOWS\SysWow64\nvcuda.dll, 8.17.0013.5362 (English), 7/23/2015 04:02:12, 11843384 bytes
   Driver: C:\WINDOWS\SysWow64\nvcuvid.dll, 7.17.0013.5362 (English), 7/23/2015 04:02:12, 2164040 bytes
   Driver: C:\WINDOWS\SysWow64\nvd3dum.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 12973680 bytes
   Driver: C:\WINDOWS\SysWow64\nvinit.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 155280 bytes
   Driver: C:\WINDOWS\SysWow64\nvoglshim32.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 128512 bytes
   Driver: C:\WINDOWS\SysWow64\nvoglv32.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 22973584 bytes
   Driver: C:\WINDOWS\SysWow64\nvopencl.dll, 8.17.0013.5362 (English), 7/23/2015 04:02:12, 13274904 bytes
   Driver: C:\WINDOWS\SysWow64\nvumdshim.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 991152 bytes
   Driver: C:\WINDOWS\SysWow64\nvwgf2um.dll, 10.18.0013.5362 (English), 7/23/2015 04:02:12, 15754192 bytes
   Driver: C:\WINDOWS\system32\nvdispco6435362.dll, 2.00.0043.0004 (English), 7/23/2015 04:02:12, 1898128 bytes
   Driver: C:\WINDOWS\system32\nvdispgenco6435362.dll, 2.00.0020.0002 (English), 7/23/2015 04:02:12, 1557648 bytes


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2F99&SUBSYS_2F998086&REV_02\3&103A9D54&0&F1
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FB8&SUBSYS_00000000&REV_02\3&103A9D54&0&BC
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FFE&SUBSYS_00001462&REV_02\3&103A9D54&0&7E
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2F28&SUBSYS_78851462&REV_02\3&11583659&1&28
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FA8&SUBSYS_2FA88086&REV_02\3&103A9D54&0&98
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FE1&SUBSYS_00001462&REV_02\3&103A9D54&0&61
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_8D22&SUBSYS_78851462&REV_05\3&11583659&1&FB
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FA0&SUBSYS_2FA08086&REV_02\3&103A9D54&0&90
   Driver: n/a


     Name: PCI standard ISA bridge
Device ID: PCI\VEN_8086&DEV_8D47&SUBSYS_78851462&REV_05\3&11583659&1&F8
   Driver: C:\WINDOWS\system32\DRIVERS\msisadrv.sys, 10.00.10240.16384 (English), 7/10/2015 05:59:38, 19296 bytes


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2F2C&SUBSYS_78851462&REV_02\3&11583659&1&2C
   Driver: n/a


     Name: PCI Express Root Port
Device ID: PCI\VEN_8086&DEV_8D18&SUBSYS_78851462&REV_D5\3&11583659&1&E4
   Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 10.00.10240.16390 (English), 7/29/2015 21:11:22, 325984 bytes


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2F88&SUBSYS_00000000&REV_02\3&103A9D54&0&F8
   Driver: n/a


     Name: High Definition Audio Controller
Device ID: PCI\VEN_10DE&DEV_0FBB&SUBSYS_31701462&REV_A1\4&3733ABE7&0&0118
   Driver: C:\WINDOWS\system32\DRIVERS\hdaudbus.sys, 10.00.10240.16384 (English), 7/10/2015 05:59:36, 80896 bytes
   Driver: C:\WINDOWS\system32\drivers\drmk.sys, 10.00.10240.16384 (English), 7/10/2015 05:59:36, 96768 bytes
   Driver: C:\WINDOWS\system32\drivers\portcls.sys, 10.00.10240.16384 (English), 7/10/2015 05:59:36, 320512 bytes


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FE4&SUBSYS_00001462&REV_02\3&103A9D54&0&64
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2F6F&SUBSYS_00000000&REV_02\3&103A9D54&0&B7
   Driver: n/a


     Name: Intel(R) Ethernet Connection (2) I218-V
Device ID: PCI\VEN_8086&DEV_15A1&SUBSYS_78851462&REV_05\3&11583659&1&C8
   Driver: C:\WINDOWS\system32\DRIVERS\e1i63x64.sys, 12.12.0050.0006 (English), 7/10/2015 05:59:36, 482328 bytes


     Name: PCI Express Root Port
Device ID: PCI\VEN_8086&DEV_8D10&SUBSYS_78851462&REV_D5\3&11583659&1&E0
   Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 10.00.10240.16390 (English), 7/29/2015 21:11:22, 325984 bytes


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FBF&SUBSYS_00000000&REV_02\3&103A9D54&0&A7
   Driver: n/a


     Name: Intel(R) Management Engine Interface 
Device ID: PCI\VEN_8086&DEV_8D3A&SUBSYS_78851462&REV_05\3&11583659&1&B0
   Driver: C:\WINDOWS\system32\DRIVERS\TeeDriverx64.sys, 10.00.0030.1054 (English), 9/30/2014 17:47:28, 129312 bytes
   Driver: C:\ProgramData\Microsoft\Windows\DeviceMetadataStore\EN\3f3ca95b-3978-4168-b47b-5444f42d6c89.devicemetadata-ms, 9/30/2014 17:47:28, 938 bytes
   Driver: C:\ProgramData\Microsoft\Windows\DeviceMetadataStore\EN\46a6fdbe-c823-4579-bab6-35f67e01f793.devicemetadata-ms, 9/30/2014 17:47:28, 833 bytes
   Driver: C:\WINDOWS\system32\WdfCoInstaller01011.dll, 1.11.9200.16384 (English), 9/30/2014 17:47:28, 1795952 bytes


     Name: ASMedia USB 3.0 eXtensible Host Controller - 1.0 (Microsoft)
Device ID: PCI\VEN_1B21&DEV_1142&SUBSYS_78851462&REV_00\4&2727FBE3&0&00E4
   Driver: C:\WINDOWS\system32\DRIVERS\USBXHCI.SYS, 10.00.10240.16461 (English), 8/18/2015 02:55:45, 373072 bytes


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FD0&SUBSYS_00000000&REV_02\3&103A9D54&0&B8
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FAE&SUBSYS_00000000&REV_02\3&103A9D54&0&9E
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2F36&SUBSYS_78851462&REV_02\3&103A9D54&0&59
   Driver: n/a


     Name: Intel(R) USB 3.0 eXtensible Host Controller - 1.0 (Microsoft)
Device ID: PCI\VEN_8086&DEV_8D31&SUBSYS_78851462&REV_05\3&11583659&1&A0
   Driver: C:\WINDOWS\system32\DRIVERS\USBXHCI.SYS, 10.00.10240.16461 (English), 8/18/2015 02:55:45, 373072 bytes


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FFC&SUBSYS_00001462&REV_02\3&103A9D54&0&7C
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_8D7C&SUBSYS_78851462&REV_05\3&11583659&1&88
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2F81&SUBSYS_78851462&REV_02\3&103A9D54&0&58
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FBA&SUBSYS_00000000&REV_02\3&103A9D54&0&BE
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2F1E&SUBSYS_2F1E8086&REV_02\3&103A9D54&0&85
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2F2A&SUBSYS_78851462&REV_02\3&11583659&1&2A
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FF8&SUBSYS_00000000&REV_02\3&103A9D54&0&78
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FB6&SUBSYS_2FB68086&REV_02\3&103A9D54&0&AA
   Driver: n/a


     Name: PCI Express Root Port
Device ID: PCI\VEN_8086&DEV_8D16&SUBSYS_78851462&REV_D5\3&11583659&1&E3
   Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 10.00.10240.16390 (English), 7/29/2015 21:11:22, 325984 bytes


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FB4&SUBSYS_2FB48086&REV_02\3&103A9D54&0&A8
   Driver: n/a


     Name: PCI Express Root Port
Device ID: PCI\VEN_8086&DEV_2F04&SUBSYS_78851462&REV_02\3&11583659&1&10
   Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 10.00.10240.16390 (English), 7/29/2015 21:11:22, 325984 bytes


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FB9&SUBSYS_00000000&REV_02\3&103A9D54&0&BD
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FB2&SUBSYS_2FB28086&REV_02\3&103A9D54&0&A2
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2F71&SUBSYS_2F718086&REV_02\3&103A9D54&0&99
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FB0&SUBSYS_2FB08086&REV_02\3&103A9D54&0&A0
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2F29&SUBSYS_78851462&REV_02\3&11583659&1&29
   Driver: n/a


     Name: Intel Device
Device ID: PCI\VEN_8086&DEV_2FE2&SUBSYS_00001462&REV_02\3&103A9D54&0&62
   Driver: n/a


------------------
DirectShow Filters
------------------


DirectShow Filters:
WMAudio Decoder DMO,0x00800800,1,1,WMADMOD.DLL,10.00.10240.16384
WMAPro over S/PDIF DMO,0x00600800,1,1,WMADMOD.DLL,10.00.10240.16384
WMSpeech Decoder DMO,0x00600800,1,1,WMSPDMOD.DLL,10.00.10240.16384
MP3 Decoder DMO,0x00600800,1,1,mp3dmod.dll,10.00.10240.16384
Mpeg4s Decoder DMO,0x00800001,1,1,mp4sdecd.dll,10.00.10240.16384
WMV Screen decoder DMO,0x00600800,1,1,wmvsdecd.dll,10.00.10240.16384
WMVideo Decoder DMO,0x00800001,1,1,wmvdecod.dll,10.00.10240.16384
Mpeg43 Decoder DMO,0x00800001,1,1,mp43decd.dll,10.00.10240.16384
Mpeg4 Decoder DMO,0x00800001,1,1,mpg4decd.dll,10.00.10240.16384
DV Muxer,0x00400000,0,0,qdv.dll,10.00.10240.16384
Color Space Converter,0x00400001,1,1,quartz.dll,10.00.10240.16384
WM ASF Reader,0x00400000,0,0,qasf.dll,12.00.10240.16384
AVI Splitter,0x00600000,1,1,quartz.dll,10.00.10240.16384
VGA 16 Color Ditherer,0x00400000,1,1,quartz.dll,10.00.10240.16384
SBE2MediaTypeProfile,0x00200000,0,0,sbe.dll,10.00.10240.16384
Microsoft DTV-DVD Video Decoder,0x005fffff,2,4,msmpeg2vdec.dll,12.00.10132.0000
AC3 Parser Filter,0x00600000,1,1,mpg2splt.ax,10.00.10240.16384
StreamBufferSink,0x00200000,0,0,sbe.dll,10.00.10240.16384
MJPEG Decompressor,0x00600000,1,1,quartz.dll,10.00.10240.16384
VHMixerSource,0x00200000,0,1,VHMediaCOM.dll,2.00.0000.0487
MPEG-I Stream Splitter,0x00600000,1,2,quartz.dll,10.00.10240.16384
SAMI (CC) Parser,0x00400000,1,1,quartz.dll,10.00.10240.16384
VBI Codec,0x00600000,1,4,VBICodec.ax,10.00.10240.16384
MPEG-2 Splitter,0x005fffff,1,0,mpg2splt.ax,10.00.10240.16384
Closed Captions Analysis Filter,0x00200000,2,5,cca.dll,10.00.10240.16384
SBE2FileScan,0x00200000,0,0,sbe.dll,10.00.10240.16384
Microsoft MPEG-2 Video Encoder,0x00200000,1,1,msmpeg2enc.dll,12.00.10240.16384
Internal Script Command Renderer,0x00800001,1,0,quartz.dll,10.00.10240.16384
MPEG Audio Decoder,0x03680001,1,1,quartz.dll,10.00.10240.16384
DV Splitter,0x00600000,1,2,qdv.dll,10.00.10240.16384
Video Mixing Renderer 9,0x00200000,1,0,quartz.dll,10.00.10240.16384
Microsoft MPEG-2 Encoder,0x00200000,2,1,msmpeg2enc.dll,12.00.10240.16384
VHAudioDSP,0x00200000,1,1,VHMediaCOM.dll,2.00.0000.0487
VHSplitProcSource,0x00200000,0,1,VHMediaCOM.dll,2.00.0000.0487
VHCropResize,0x00200000,1,1,VHMediaCOM.dll,2.00.0000.0487
ACM Wrapper,0x00600000,1,1,quartz.dll,10.00.10240.16384
Video Renderer,0x00800001,1,0,quartz.dll,10.00.10240.16384
MPEG-2 Video Stream Analyzer,0x00200000,0,0,sbe.dll,10.00.10240.16384
Line 21 Decoder,0x00600000,1,1,,
Video Port Manager,0x00600000,2,1,quartz.dll,10.00.10240.16384
Video Renderer,0x00400000,1,0,quartz.dll,10.00.10240.16384
VPS Decoder,0x00200000,0,0,WSTPager.ax,10.00.10240.16384
WM ASF Writer,0x00400000,0,0,qasf.dll,12.00.10240.16384
VBI Surface Allocator,0x00600000,1,1,vbisurf.ax,10.00.10240.16384
File writer,0x00200000,1,0,qcap.dll,10.00.10240.16384
DVD Navigator,0x00200000,0,3,qdvd.dll,10.00.10240.16384
Overlay Mixer2,0x00200000,1,1,,
VHYV12Decoder,0x00200000,1,1,VHMediaCOM.dll,2.00.0000.0487
VHStreamDelay,0x00200000,1,1,VHMediaCOM.dll,2.00.0000.0487
Microsoft MPEG-2 Audio Encoder,0x00200000,1,1,msmpeg2enc.dll,12.00.10240.16384
VHMultiWriter,0x00200000,1,0,VHMediaCOM.dll,2.00.0000.0487
WST Pager,0x00200000,1,1,WSTPager.ax,10.00.10240.16384
MPEG-2 Demultiplexer,0x00600000,1,1,mpg2splt.ax,10.00.10240.16384
VHAudioGain,0x00200000,1,1,VHMediaCOM.dll,2.00.0000.0487
DV Video Decoder,0x00800000,1,1,qdv.dll,10.00.10240.16384
VHFrameRateConv,0x00200000,1,1,VHMediaCOM.dll,2.00.0000.0487
SampleGrabber,0x00200000,1,1,qedit.dll,10.00.10240.16384
Null Renderer,0x00200000,1,0,qedit.dll,10.00.10240.16384
MPEG-2 Sections and Tables,0x005fffff,1,0,Mpeg2Data.ax,10.00.10240.16384
Microsoft AC3 Encoder,0x00200000,1,1,msac3enc.dll,10.00.10240.16384
VHAudioDelay,0x00200000,1,1,VHMediaCOM.dll,2.00.0000.0487
StreamBufferSource,0x00200000,0,0,sbe.dll,10.00.10240.16384
Smart Tee,0x00200000,1,2,qcap.dll,10.00.10240.16384
Overlay Mixer,0x00200000,0,0,,
AVI Decompressor,0x00600000,1,1,quartz.dll,10.00.10240.16384
VHDeinterlace,0x00200000,1,1,VHMediaCOM.dll,2.00.0000.0487
VHYV12Encoder,0x00200000,1,1,VHMediaCOM.dll,2.00.0000.0487
AVI/WAV File Source,0x00400000,0,2,quartz.dll,10.00.10240.16384
Wave Parser,0x00400000,1,1,quartz.dll,10.00.10240.16384
MIDI Parser,0x00400000,1,1,quartz.dll,10.00.10240.16384
Multi-file Parser,0x00400000,1,1,quartz.dll,10.00.10240.16384
File stream renderer,0x00400000,1,1,quartz.dll,10.00.10240.16384
VHMultiReader,0x00200000,0,1,VHMediaCOM.dll,2.00.0000.0487
Microsoft DTV-DVD Audio Decoder,0x005fffff,1,1,msmpeg2adec.dll,12.00.10132.0000
StreamBufferSink2,0x00200000,0,0,sbe.dll,10.00.10240.16384
AVI Mux,0x00200000,1,0,qcap.dll,10.00.10240.16384
Line 21 Decoder 2,0x00600002,1,1,quartz.dll,10.00.10240.16384
File Source (Async.),0x00400000,0,1,quartz.dll,10.00.10240.16384
File Source (URL),0x00400000,0,1,quartz.dll,10.00.10240.16384
Infinite Pin Tee Filter,0x00200000,1,1,qcap.dll,10.00.10240.16384
Enhanced Video Renderer,0x00200000,1,0,evr.dll,10.00.10240.16384
BDA MPEG2 Transport Information Filter,0x00200000,2,0,psisrndr.ax,10.00.10240.16384
MPEG Video Decoder,0x40000001,1,1,quartz.dll,10.00.10240.16384


WDM Streaming Tee/Splitter Devices:
Tee/Sink-to-Sink Converter,0x00200000,1,1,ksproxy.ax,10.00.10240.16384


Video Compressors:
WMVideo8 Encoder DMO,0x00600800,1,1,wmvxencd.dll,10.00.10240.16384
WMVideo9 Encoder DMO,0x00600800,1,1,wmvencod.dll,10.00.10240.16384
MSScreen 9 encoder DMO,0x00600800,1,1,wmvsencd.dll,10.00.10240.16384
DV Video Encoder,0x00200000,0,0,qdv.dll,10.00.10240.16384
MJPEG Compressor,0x00200000,0,0,quartz.dll,10.00.10240.16384


Audio Compressors:
WM Speech Encoder DMO,0x00600800,1,1,WMSPDMOE.DLL,10.00.10240.16384
WMAudio Encoder DMO,0x00600800,1,1,WMADMOE.DLL,10.00.10240.16384
IMA ADPCM,0x00200000,1,1,quartz.dll,10.00.10240.16384
PCM,0x00200000,1,1,quartz.dll,10.00.10240.16384
Microsoft ADPCM,0x00200000,1,1,quartz.dll,10.00.10240.16384
GSM 6.10,0x00200000,1,1,quartz.dll,10.00.10240.16384
CCITT A-Law,0x00200000,1,1,quartz.dll,10.00.10240.16384
CCITT u-Law,0x00200000,1,1,quartz.dll,10.00.10240.16384
MPEG Layer-3,0x00200000,1,1,quartz.dll,10.00.10240.16384


Audio Capture Sources:
Microphone (Blue Snowball),0x00200000,0,0,qcap.dll,10.00.10240.16384
XSplitBroadcaster,0x00200000,0,1,VHMediaCOM.dll,2.00.0000.0487
Microphone (ManyCam Virtual Microphone),0x00200000,0,0,qcap.dll,10.00.10240.16384
Microphone (Realtek High Definition Audio),0x00200000,0,0,qcap.dll,10.00.10240.16384


PBDA CP Filters:
PBDA DTFilter,0x00600000,1,1,CPFilters.dll,10.00.10240.16384
PBDA ETFilter,0x00200000,0,0,CPFilters.dll,10.00.10240.16384
PBDA PTFilter,0x00200000,0,0,CPFilters.dll,10.00.10240.16384


Midi Renderers:
Default MidiOut Device,0x00800000,1,0,quartz.dll,10.00.10240.16384
Microsoft GS Wavetable Synth,0x00200000,1,0,quartz.dll,10.00.10240.16384


WDM Streaming Capture Devices:
ManyCam Virtual Webcam,0x00200000,1,2,ksproxy.ax,10.00.10240.16384
,0x00000000,0,0,,
,0x00000000,0,0,,
Realtek HD Audio Mic input,0x00200000,1,1,ksproxy.ax,10.00.10240.16384
Realtek HD Audio Stereo input,0x00200000,1,1,ksproxy.ax,10.00.10240.16384
Realtek HD Audio Line input,0x00200000,1,1,ksproxy.ax,10.00.10240.16384
ManyCam Wave,0x00200000,1,1,ksproxy.ax,10.00.10240.16384
XSplit Wave,0x00200000,1,1,ksproxy.ax,10.00.10240.16384
MicIn,0x00200000,1,1,ksproxy.ax,10.00.10240.16384


WDM Streaming Rendering Devices:
Realtek HDA SPDIF Out,0x00200000,1,1,ksproxy.ax,10.00.10240.16384
Realtek HD Audio output,0x00200000,1,1,ksproxy.ax,10.00.10240.16384
Realtek HD Audio 2nd output,0x00200000,1,1,ksproxy.ax,10.00.10240.16384
,0x00000000,0,0,,
XSplit Wave,0x00200000,1,1,ksproxy.ax,10.00.10240.16384
,0x00000000,0,0,,
,0x00000000,0,0,,


BDA Network Providers:
Microsoft ATSC Network Provider,0x00200000,0,1,MSDvbNP.ax,10.00.10240.16384
Microsoft DVBC Network Provider,0x00200000,0,1,MSDvbNP.ax,10.00.10240.16384
Microsoft DVBS Network Provider,0x00200000,0,1,MSDvbNP.ax,10.00.10240.16384
Microsoft DVBT Network Provider,0x00200000,0,1,MSDvbNP.ax,10.00.10240.16384
Microsoft Network Provider,0x00200000,0,1,MSNP.ax,10.00.10240.16384


Video Capture Sources:
ManyCam Virtual Webcam,0x00200000,1,2,ksproxy.ax,10.00.10240.16384
XSplitBroadcaster,0x00200000,0,1,VHMediaCOM.dll,2.00.0000.0487


Multi-Instance Capable VBI Codecs:
VBI Codec,0x00600000,1,4,VBICodec.ax,10.00.10240.16384


BDA Transport Information Renderers:
BDA MPEG2 Transport Information Filter,0x00600000,2,0,psisrndr.ax,10.00.10240.16384
MPEG-2 Sections and Tables,0x00600000,1,0,Mpeg2Data.ax,10.00.10240.16384


BDA CP/CA Filters:
Decrypt/Tag,0x00600000,1,1,EncDec.dll,10.00.10240.16384
Encrypt/Tag,0x00200000,0,0,EncDec.dll,10.00.10240.16384
PTFilter,0x00200000,0,0,EncDec.dll,10.00.10240.16384
XDS Codec,0x00200000,0,0,EncDec.dll,10.00.10240.16384


WDM Streaming Communication Transforms:
Tee/Sink-to-Sink Converter,0x00200000,1,1,ksproxy.ax,10.00.10240.16384


Audio Renderers:
Speakers (Realtek High Definition Audio),0x00200000,1,0,quartz.dll,10.00.10240.16384
Default DirectSound Device,0x00800000,1,0,quartz.dll,10.00.10240.16384
Default WaveOut Device,0x00200000,1,0,quartz.dll,10.00.10240.16384
DirectSound: Realtek Digital Output (Realtek High Definition Audio),0x00200000,1,0,quartz.dll,10.00.10240.16384
DirectSound: Speakers (Realtek High Definition Audio),0x00200000,1,0,quartz.dll,10.00.10240.16384
DirectSound: Realtek HD Audio 2nd output (Realtek High Definition Audio),0x00200000,1,0,quartz.dll,10.00.10240.16384
Realtek Digital Output (Realtek High Definition Audio),0x00200000,1,0,quartz.dll,10.00.10240.16384
Realtek HD Audio 2nd output (Realtek High Definition Audio),0x00200000,1,0,quartz.dll,10.00.10240.16384



----------------------------
Preferred DirectShow Filters
----------------------------


[HKEY_LOCAL_MACHINE\Software\Microsoft\DirectShow\Preferred]


<media subtype GUID>, [<filter friendly name>, ]<filter CLSID>


MEDIASUBTYPE_MPEG1Payload, MPEG Video Decoder, CLSID_CMpegVideoCodec
MEDIASUBTYPE_MPEG1Packet, MPEG Video Decoder, CLSID_CMpegVideoCodec
MEDIASUBTYPE_DVD_LPCM_AUDIO, Microsoft DTV-DVD Audio Decoder, CLSID_CMPEG2AudDecoderDS
MEDIASUBTYPE_MPEG2_AUDIO, Microsoft DTV-DVD Audio Decoder, CLSID_CMPEG2AudDecoderDS
MEDIASUBTYPE_MPEG2_VIDEO, Microsoft DTV-DVD Video Decoder, CLSID_CMPEG2VidDecoderDS
{78766964-0000-0010-8000-00AA00389B71}, Mpeg4s Decoder DMO, CLSID_CMpeg4sDecMediaObject
{7634706D-0000-0010-8000-00AA00389B71}, Mpeg4s Decoder DMO, CLSID_CMpeg4sDecMediaObject
MEDIASUBTYPE_mp4s, Mpeg4s Decoder DMO, CLSID_CMpeg4sDecMediaObject
{6C737664-0000-0010-8000-00AA00389B71}, DV Video Decoder, CLSID_DVVideoCodec
{64737664-0000-0010-8000-00AA00389B71}, DV Video Decoder, CLSID_DVVideoCodec
{64697678-0000-0010-8000-00AA00389B71}, Mpeg4s Decoder DMO, CLSID_CMpeg4sDecMediaObject
{64687664-0000-0010-8000-00AA00389B71}, DV Video Decoder, CLSID_DVVideoCodec
{58564944-0000-0010-8000-00AA00389B71}, Mpeg4s Decoder DMO, CLSID_CMpeg4sDecMediaObject
{5634504D-0000-0010-8000-00AA00389B71}, Mpeg4s Decoder DMO, CLSID_CMpeg4sDecMediaObject
MEDIASUBTYPE_MP4S, Mpeg4s Decoder DMO, CLSID_CMpeg4sDecMediaObject
MEDIASUBTYPE_WMVR, WMVideo Decoder DMO, CLSID_CWMVDecMediaObject
MEDIASUBTYPE_WMVP, WMVideo Decoder DMO, CLSID_CWMVDecMediaObject
MEDIASUBTYPE_MJPG, MJPEG Decompressor, CLSID_MjpegDec
{44495658-0000-0010-8000-00AA00389B71}, Mpeg4s Decoder DMO, CLSID_CMpeg4sDecMediaObject
MEDIASUBTYPE_WMVA, WMVideo Decoder DMO, CLSID_CWMVDecMediaObject
MEDIASUBTYPE_mpg4, Mpeg4 Decoder DMO, CLSID_CMpeg4DecMediaObject
MEDIASUBTYPE_MPG4, Mpeg4 Decoder DMO, CLSID_CMpeg4DecMediaObject
MEDIASUBTYPE_h264, Microsoft DTV-DVD Video Decoder, CLSID_CMPEG2VidDecoderDS
MEDIASUBTYPE_H264, Microsoft DTV-DVD Video Decoder, CLSID_CMPEG2VidDecoderDS
MEDIASUBTYPE_WMV3, WMVideo Decoder DMO, CLSID_CWMVDecMediaObject
MEDIASUBTYPE_mp43, Mpeg43 Decoder DMO, CLSID_CMpeg43DecMediaObject
MEDIASUBTYPE_MP43, Mpeg43 Decoder DMO, CLSID_CMpeg43DecMediaObject
MEDIASUBTYPE_m4s2, Mpeg4s Decoder DMO, CLSID_CMpeg4sDecMediaObject
MEDIASUBTYPE_WMV2, WMVideo Decoder DMO, CLSID_CWMVDecMediaObject
MEDIASUBTYPE_MSS2, WMV Screen decoder DMO, CLSID_CMSSCDecMediaObject
MEDIASUBTYPE_M4S2, Mpeg4s Decoder DMO, CLSID_CMpeg4sDecMediaObject
MEDIASUBTYPE_WVP2, WMVideo Decoder DMO, CLSID_CWMVDecMediaObject
MEDIASUBTYPE_mp42, Mpeg4 Decoder DMO, CLSID_CMpeg4DecMediaObject
MEDIASUBTYPE_MP42, Mpeg4 Decoder DMO, CLSID_CMpeg4DecMediaObject
MEDIASUBTYPE_WMV1, WMVideo Decoder DMO, CLSID_CWMVDecMediaObject
MEDIASUBTYPE_MSS1, WMV Screen decoder DMO, CLSID_CMSSCDecMediaObject
MEDIASUBTYPE_WVC1, WMVideo Decoder DMO, CLSID_CWMVDecMediaObject
MEDIASUBTYPE_AVC1, Microsoft DTV-DVD Video Decoder, CLSID_CMPEG2VidDecoderDS
{20637664-0000-0010-8000-00AA00389B71}, DV Video Decoder, CLSID_DVVideoCodec
MEDIASUBTYPE_MPEG_LOAS, Microsoft DTV-DVD Audio Decoder, CLSID_CMPEG2AudDecoderDS
MEDIASUBTYPE_MPEG_ADTS_AAC, Microsoft DTV-DVD Audio Decoder, CLSID_CMPEG2AudDecoderDS
MEDIASUBTYPE_WMAUDIO_LOSSLESS, WMAudio Decoder DMO, CLSID_CWMADecMediaObject
MEDIASUBTYPE_WMAUDIO3, WMAudio Decoder DMO, CLSID_CWMADecMediaObject
WMMEDIASUBTYPE_WMAudioV8, WMAudio Decoder DMO, CLSID_CWMADecMediaObject
MEDIASUBTYPE_MSAUDIO1, WMAudio Decoder DMO, CLSID_CWMADecMediaObject
MEDIASUBTYPE_RAW_AAC1, Microsoft DTV-DVD Audio Decoder, CLSID_CMPEG2AudDecoderDS
WMMEDIASUBTYPE_MP3, MP3 Decoder DMO, CLSID_CMP3DecMediaObject
MEDIASUBTYPE_MPEG1AudioPayload, MPEG Audio Decoder, CLSID_CMpegAudioCodec
WMMEDIASUBTYPE_WMSP2, WMSpeech Decoder DMO, CLSID_CWMSPDecMediaObject
WMMEDIASUBTYPE_WMSP1, WMSpeech Decoder DMO, CLSID_CWMSPDecMediaObject



---------------------------
Media Foundation Transforms
---------------------------


[HKEY_LOCAL_MACHINE\Software\Classes\MediaFoundation\Transforms]


<category>:
  <transform friendly name>, <transform CLSID>, <flags>, [<merit>, ]<file name>, <file version>


Video Decoders:
  NVIDIA MJPEG Video Decoder MFT, {70F36578-2741-454F-B494-E8563DDD1CB4}, 0x4, 8, nvDecMFTMjpeg.dll, 10.18.0013.5362
  Microsoft MPEG Video Decoder MFT, {2D709E52-123F-49B5-9CBC-9AF5CDE28FB9}, 0x1, msmpeg2vdec.dll, 12.00.10132.0000
  DV Decoder MFT, {404A6DE5-D4D6-4260-9BC7-5A6CBD882432}, 0x1, mfdvdec.dll, 10.00.10240.16384
  Microsoft H265 Video Decoder MFT, {420A51A3-D605-430C-B4FC-45274FA6C562}, 0x1, hevcdecoder.dll, 10.00.10240.16384
  Mpeg4s Decoder MFT, CLSID_CMpeg4sDecMFT, 0x1, mp4sdecd.dll, 10.00.10240.16384
  Microsoft H264 Video Decoder MFT, CLSID_CMSH264DecoderMFT, 0x1, msmpeg2vdec.dll, 12.00.10132.0000
  WMV Screen decoder MFT, CLSID_CMSSCDecMediaObject, 0x1, wmvsdecd.dll, 10.00.10240.16384
  WMVideo Decoder MFT, CLSID_CWMVDecMediaObject, 0x1, wmvdecod.dll, 10.00.10240.16384
  MJPEG Decoder MFT, {CB17E772-E1CC-4633-8450-5617AF577905}, 0x1, mfmjpegdec.dll, 10.00.10240.16384
  Mpeg43 Decoder MFT, CLSID_CMpeg43DecMediaObject, 0x1, mp43decd.dll, 10.00.10240.16384
  Mpeg4 Decoder MFT, CLSID_CMpeg4DecMediaObject, 0x1, mpg4decd.dll, 10.00.10240.16384
Video Encoders:
  NVIDIA H.264 Encoder MFT, {60F44560-5A20-4857-BFEF-D29773CB8040}, 0x4, 8, nvEncMFTH264.dll, 10.18.0013.5362
  NVIDIA HEVC Encoder MFT, {966F107C-8EA2-425D-B822-E4A71BEF01D7}, 0x4, 8, nvEncMFThevc.dll, 10.18.0013.5362
  H264 Encoder MFT, {6CA50344-051A-4DED-9779-A43305165E35}, 0x1, mfh264enc.dll, 10.00.10240.16384
  WMVideo8 Encoder MFT, CLSID_CWMVXEncMediaObject, 0x1, wmvxencd.dll, 10.00.10240.16384
  H263 Encoder MFT, {BC47FCFE-98A0-4F27-BB07-698AF24F2B38}, 0x1, mfh263enc.dll, 10.00.10240.16384
  WMVideo9 Encoder MFT, CLSID_CWMV9EncMediaObject, 0x1, wmvencod.dll, 10.00.10240.16384
  Microsoft MPEG-2 Video Encoder MFT, {E6335F02-80B7-4DC4-ADFA-DFE7210D20D5}, 0x2, msmpeg2enc.dll, 12.00.10240.16384
  H265 Encoder MFT, {F2F84074-8BCA-40BD-9159-E880F673DD3B}, 0x1, mfh265enc.dll, 10.00.10240.16384
Video Effects:
  Frame Rate Converter, CLSID_CFrameRateConvertDmo, 0x1, mfvdsp.dll, 10.00.10240.16384
  Resizer MFT, CLSID_CResizerDMO, 0x1, vidreszr.dll, 10.00.10240.16384
  VideoStabilization MFT, {51571744-7FE4-4FF2-A498-2DC34FF74F1B}, 0x1, MSVideoDSP.dll, 10.00.10240.16384
  Color Control, CLSID_CColorControlDmo, 0x1, mfvdsp.dll, 10.00.10240.16384
  Color Converter MFT, CLSID_CColorConvertDMO, 0x1, colorcnv.dll, 10.00.10240.16384
Video Processor:
  Microsoft Video Processor MFT, {88753B26-5B24-49BD-B2E7-0C445C78C982}, 0x1, msvproc.dll, 12.00.10240.16384
Audio Decoders:
  Microsoft Dolby Digital Plus Decoder MFT, {177C0AFE-900B-48D4-9E4C-57ADD250B3D4}, 0x1, DolbyDecMFT.dll, 10.00.10240.16384
  MS AMRNB Decoder MFT, {265011AE-5481-4F77-A295-ABB6FFE8D63E}, 0x1, MSAMRNBDecoder.dll, 10.00.10240.16384
  WMAudio Decoder MFT, CLSID_CWMADecMediaObject, 0x1, WMADMOD.DLL, 10.00.10240.16384
  Microsoft AAC Audio Decoder MFT, CLSID_CMSAACDecMFT, 0x1, MSAudDecMFT.dll, 10.00.10240.16384
  A-law Wrapper MFT, {36CB6E0C-78C1-42B2-9943-846262F31786}, 0x1, mfcore.dll, 12.00.10240.16431
  GSM ACM Wrapper MFT, {4A76B469-7B66-4DD4-BA2D-DDF244C766DC}, 0x1, mfcore.dll, 12.00.10240.16431
  WMAPro over S/PDIF MFT, CLSID_CWMAudioSpdTxDMO, 0x1, WMADMOD.DLL, 10.00.10240.16384
  Microsoft FLAC Audio Decoder MFT, {6B0B3E6B-A2C5-4514-8055-AFE8A95242D9}, 0x1, MSFlacDecoder.dll, 10.00.10240.16384
  Microsoft MPEG Audio Decoder MFT, {70707B39-B2CA-4015-ABEA-F8447D22D88B}, 0x1, MSAudDecMFT.dll, 10.00.10240.16384
  WMSpeech Decoder DMO, CLSID_CWMSPDecMediaObject, 0x1, WMSPDMOD.DLL, 10.00.10240.16384
  G711 Wrapper MFT, {92B66080-5E2D-449E-90C4-C41F268E5514}, 0x1, mfcore.dll, 12.00.10240.16431
  IMA ADPCM ACM Wrapper MFT, {A16E1BFF-A80D-48AD-AECD-A35C005685FE}, 0x1, mfcore.dll, 12.00.10240.16431
  MP3 Decoder MFT, CLSID_CMP3DecMediaObject, 0x1, mp3dmod.dll, 10.00.10240.16384
  Microsoft ALAC Audio Decoder MFT, {C0CD7D12-31FC-4BBC-B363-7322EE3E1879}, 0x1, MSAlacDecoder.dll, 10.00.10240.16384
  ADPCM ACM Wrapper MFT, {CA34FE0A-5722-43AD-AF23-05F7650257DD}, 0x1, mfcore.dll, 12.00.10240.16431
Audio Encoders:
  LPCM DVD-Audio MFT, {068A8476-9229-4CC0-9D49-2FC699DCD30A}, 0x1, winmde.dll, 12.00.10240.16412
  MP3 Encoder ACM Wrapper MFT, {11103421-354C-4CCA-A7A3-1AFF9A5B6701}, 0x1, mfcore.dll, 12.00.10240.16431
  Microsoft FLAC Audio Encoder MFT, {128509E9-C44E-45DC-95E9-C255B8F466A6}, 0x1, MSFlacEncoder.dll, 10.00.10240.16384
  WM Speech Encoder DMO, CLSID_CWMSPEncMediaObject2, 0x1, WMSPDMOE.DLL, 10.00.10240.16384
  MS AMRNB Encoder MFT, {2FAE8AFE-04A3-423A-A814-85DB454712B0}, 0x1, MSAMRNBEncoder.dll, 10.00.10240.16384
  Microsoft MPEG-2 Audio Encoder MFT, {46A4DD5C-73F8-4304-94DF-308F760974F4}, 0x1, msmpeg2enc.dll, 12.00.10240.16384
  WMAudio Encoder MFT, CLSID_CWMAEncMediaObject, 0x1, WMADMOE.DLL, 10.00.10240.16384
  Microsoft AAC Audio Encoder MFT, {93AF0C51-2275-45D2-A35B-F2BA21CAED00}, 0x1, mfAACEnc.dll, 10.00.10240.16384
  Microsoft ALAC Audio Encoder MFT, {9AB6A28C-748E-4B6A-BFFF-CC443B8E8FB4}, 0x1, MSAlacEncoder.dll, 10.00.10240.16384
  Microsoft Dolby Digital Encoder MFT, {AC3315C9-F481-45D7-826C-0B406C1F64B8}, 0x1, msac3enc.dll, 10.00.10240.16384
Audio Effects:
  AEC, CLSID_CWMAudioAEC, 0x1, mfwmaaec.dll, 10.00.10240.16384
  Resampler MFT, CLSID_CResamplerMediaObject, 0x1, resampledmo.dll, 10.00.10240.16384
Multiplexers:
  Microsoft MPEG2 Multiplexer MFT, {AB300F71-01AB-46D2-AB6C-64906CB03258}, 0x2, mfmpeg2srcsnk.dll, 12.00.10240.16412
Others:
  Microsoft H264 Video Remux (MPEG2TSToMP4) MFT, {05A47EBB-8BF0-4CBF-AD2F-3B71D75866F5}, 0x1, msmpeg2vdec.dll, 12.00.10132.0000



--------------------------------------------
Media Foundation Enabled Hardware Categories
--------------------------------------------


[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Media Foundation\HardwareMFT]


EnableEncoders = 1
EnableDecoders = 1
EnableVideoProcessors = 1



-------------------------------------
Media Foundation Byte Stream Handlers
-------------------------------------


[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Media Foundation\ByteStreamHandlers]
[HKEY_LOCAL_MACHINE\Software\Classes\MediaFoundation\MediaSources\Preferred]


<file ext. or MIME type>, <handler CLSID>, <brief description>[, Preferred]


.3g2, {271C3902-6095-4C45-A22F-20091816EE9E}, MPEG4 Byte Stream Handler, Preferred
.3gp, {271C3902-6095-4C45-A22F-20091816EE9E}, MPEG4 Byte Stream Handler, Preferred
.3gp2, {271C3902-6095-4C45-A22F-20091816EE9E}, MPEG4 Byte Stream Handler, Preferred
.3gpp, {271C3902-6095-4C45-A22F-20091816EE9E}, MPEG4 Byte Stream Handler, Preferred
.aac, {926F41F7-003E-4382-9E84-9E953BE10562}, ADTS Byte Stream Handler, Preferred
.ac3, {46031BA1-083F-47D9-8369-23C92BDAB2FF}, AC-3 Byte Stream Handler, Preferred
.adt, {926F41F7-003E-4382-9E84-9E953BE10562}, ADTS Byte Stream Handler, Preferred
.adts, {926F41F7-003E-4382-9E84-9E953BE10562}, ADTS Byte Stream Handler, Preferred
.am?, {EFE6208A-0A2C-49FA-8A01-3768B559B6DA}, MF AMRNB Media Source ByteStreamHandler
.amr, {EFE6208A-0A2C-49FA-8A01-3768B559B6DA}, MF AMRNB Media Source ByteStreamHandler, Preferred
.asf, {41457294-644C-4298-A28A-BD69F2C0CF3B}, ASF Byte Stream Handler, Preferred
.avi, {7AFA253E-F823-42F6-A5D9-714BDE467412}, AVI Byte Stream Handler, Preferred
.dvr-ms, {65964407-A5D8-4060-85B0-1CCD63F768E2}, dvr-ms Byte Stream Handler, Preferred
.dvr-ms, {A8721937-E2FB-4D7A-A9EE-4EB08C890B6E}, MF SBE Source ByteStreamHandler
.ec3, {46031BA1-083F-47D9-8369-23C92BDAB2FF}, AC-3 Byte Stream Handler, Preferred
.flac, {0E41CFB8-0506-40F4-A516-77CC23642D91}, MF FLAC Media Source ByteStreamHandler, Preferred
.m2t, {40871C59-AB40-471F-8DC3-1F259D862479}, MPEG2 Byte Stream Handler, Preferred
.m2ts, {40871C59-AB40-471F-8DC3-1F259D862479}, MPEG2 Byte Stream Handler, Preferred
.m4a, {271C3902-6095-4C45-A22F-20091816EE9E}, MPEG4 Byte Stream Handler, Preferred
.m4v, {271C3902-6095-4C45-A22F-20091816EE9E}, MPEG4 Byte Stream Handler, Preferred
.mk3d, {1F9A2C18-D89E-463E-B4F4-BB90152ACC64}, MKV Byte Stream Handler, Preferred
.mka, {1F9A2C18-D89E-463E-B4F4-BB90152ACC64}, MKV Byte Stream Handler, Preferred
.mks, {1F9A2C18-D89E-463E-B4F4-BB90152ACC64}, MKV Byte Stream Handler, Preferred
.mkv, {1F9A2C18-D89E-463E-B4F4-BB90152ACC64}, MKV Byte Stream Handler, Preferred
.mod, {40871C59-AB40-471F-8DC3-1F259D862479}, MPEG2 Byte Stream Handler, Preferred
.mov, {271C3902-6095-4C45-A22F-20091816EE9E}, MPEG4 Byte Stream Handler, Preferred
.mp2v, {40871C59-AB40-471F-8DC3-1F259D862479}, MPEG2 Byte Stream Handler, Preferred
.mp3, {A82E50BA-8E92-41EB-9DF2-433F50EC2993}, MP3 Byte Stream Handler, Preferred
.mp4, {271C3902-6095-4C45-A22F-20091816EE9E}, MPEG4 Byte Stream Handler, Preferred
.mp4v, {271C3902-6095-4C45-A22F-20091816EE9E}, MPEG4 Byte Stream Handler, Preferred
.mpa, {A82E50BA-8E92-41EB-9DF2-433F50EC2993}, MP3 Byte Stream Handler, Preferred
.mpeg, {40871C59-AB40-471F-8DC3-1F259D862479}, MPEG2 Byte Stream Handler, Preferred
.mpg, {40871C59-AB40-471F-8DC3-1F259D862479}, MPEG2 Byte Stream Handler, Preferred
.mts, {40871C59-AB40-471F-8DC3-1F259D862479}, MPEG2 Byte Stream Handler, Preferred
.nsc, {B084785C-DDE0-4D30-8CA8-05A373E185BE}, NSC Byte Stream Handler, Preferred
.sami, {7A56C4CB-D678-4188-85A8-BA2EF68FA10D}, SAMI Byte Stream Handler, Preferred
.smi, {7A56C4CB-D678-4188-85A8-BA2EF68FA10D}, SAMI Byte Stream Handler, Preferred
.tod, {40871C59-AB40-471F-8DC3-1F259D862479}, MPEG2 Byte Stream Handler, Preferred
.ts, {40871C59-AB40-471F-8DC3-1F259D862479}, MPEG2 Byte Stream Handler, Preferred
.tts, {40871C59-AB40-471F-8DC3-1F259D862479}, MPEG2 Byte Stream Handler, Preferred
.uvu, {271C3902-6095-4C45-A22F-20091816EE9E}, MPEG4 Byte Stream Handler, Preferred
.vob, {40871C59-AB40-471F-8DC3-1F259D862479}, MPEG2 Byte Stream Handler, Preferred
.wav, {42C9B9F5-16FC-47EF-AF22-DA05F7C842E3}, WAV Byte Stream Handler, Preferred
.wm, {41457294-644C-4298-A28A-BD69F2C0CF3B}, ASF Byte Stream Handler, Preferred
.wma, {41457294-644C-4298-A28A-BD69F2C0CF3B}, ASF Byte Stream Handler, Preferred
.wmv, {41457294-644C-4298-A28A-BD69F2C0CF3B}, ASF Byte Stream Handler, Preferred
.wtv, {65964407-A5D8-4060-85B0-1CCD63F768E2}, WTV Byte Stream Handler, Preferred
audio/3gpp, {271C3902-6095-4C45-A22F-20091816EE9E}, MPEG4 Byte Stream Handler, Preferred
audio/3gpp2, {271C3902-6095-4C45-A22F-20091816EE9E}, MPEG4 Byte Stream Handler, Preferred
audio/aac, {926F41F7-003E-4382-9E84-9E953BE10562}, ADTS Byte Stream Handler, Preferred
audio/aacp, {926F41F7-003E-4382-9E84-9E953BE10562}, ADTS Byte Stream Handler, Preferred
audio/eac3, {46031BA1-083F-47D9-8369-23C92BDAB2FF}, AC-3 Byte Stream Handler, Preferred
audio/L16, {3FFB3B8C-EB99-472B-8902-E1C1B05F07CF}, LPCM Byte Stream Handler, Preferred
audio/mp3, {A82E50BA-8E92-41EB-9DF2-433F50EC2993}, MP3 Byte Stream Handler, Preferred
audio/mp4, {271C3902-6095-4C45-A22F-20091816EE9E}, MPEG4 Byte Stream Handler, Preferred
audio/MP4A-LATM, {271C3902-6095-4C45-A22F-20091816EE9E}, MPEG4 Byte Stream Handler, Preferred
audio/mpa, {A82E50BA-8E92-41EB-9DF2-433F50EC2993}, MP3 Byte Stream Handler, Preferred
audio/mpeg, {A82E50BA-8E92-41EB-9DF2-433F50EC2993}, MP3 Byte Stream Handler, Preferred
audio/mpeg3, {A82E50BA-8E92-41EB-9DF2-433F50EC2993}, MP3 Byte Stream Handler, Preferred
audio/vnd.dlna.adts, {926F41F7-003E-4382-9E84-9E953BE10562}, ADTS Byte Stream Handler, Preferred
audio/vnd.dolby.dd-raw, {46031BA1-083F-47D9-8369-23C92BDAB2FF}, AC-3 Byte Stream Handler, Preferred
audio/wav, {42C9B9F5-16FC-47EF-AF22-DA05F7C842E3}, WAV Byte Stream Handler, Preferred
audio/x-aac, {926F41F7-003E-4382-9E84-9E953BE10562}, ADTS Byte Stream Handler, Preferred
audio/x-m4a, {271C3902-6095-4C45-A22F-20091816EE9E}, MPEG4 Byte Stream Handler, Preferred
audio/x-matroska, {1F9A2C18-D89E-463E-B4F4-BB90152ACC64}, MKV Byte Stream Handler, Preferred
audio/x-mp3, {A82E50BA-8E92-41EB-9DF2-433F50EC2993}, MP3 Byte Stream Handler, Preferred
audio/x-mpeg, {A82E50BA-8E92-41EB-9DF2-433F50EC2993}, MP3 Byte Stream Handler, Preferred
audio/x-ms-wma, {41457294-644C-4298-A28A-BD69F2C0CF3B}, ASF Byte Stream Handler, Preferred
audio/x-wav, {42C9B9F5-16FC-47EF-AF22-DA05F7C842E3}, WAV Byte Stream Handler, Preferred
video/3gpp, {271C3902-6095-4C45-A22F-20091816EE9E}, MPEG4 Byte Stream Handler, Preferred
video/3gpp2, {271C3902-6095-4C45-A22F-20091816EE9E}, MPEG4 Byte Stream Handler, Preferred
video/avi, {7AFA253E-F823-42F6-A5D9-714BDE467412}, AVI Byte Stream Handler, Preferred
video/mp4, {271C3902-6095-4C45-A22F-20091816EE9E}, MPEG4 Byte Stream Handler, Preferred
video/mpeg, {40871C59-AB40-471F-8DC3-1F259D862479}, MPEG2 Byte Stream Handler, Preferred
video/msvideo, {7AFA253E-F823-42F6-A5D9-714BDE467412}, AVI Byte Stream Handler, Preferred
video/vnd.dece.mp4, {271C3902-6095-4C45-A22F-20091816EE9E}, MPEG4 Byte Stream Handler, Preferred
video/vnd.dlna.mpeg-tts, {40871C59-AB40-471F-8DC3-1F259D862479}, MPEG2 Byte Stream Handler, Preferred
video/x-m4v, {271C3902-6095-4C45-A22F-20091816EE9E}, MPEG4 Byte Stream Handler, Preferred
video/x-matroska, {1F9A2C18-D89E-463E-B4F4-BB90152ACC64}, MKV Byte Stream Handler, Preferred
video/x-ms-asf, {41457294-644C-4298-A28A-BD69F2C0CF3B}, ASF Byte Stream Handler, Preferred
video/x-ms-wm, {41457294-644C-4298-A28A-BD69F2C0CF3B}, ASF Byte Stream Handler, Preferred
video/x-ms-wmv, {41457294-644C-4298-A28A-BD69F2C0CF3B}, ASF Byte Stream Handler, Preferred
video/x-msvideo, {7AFA253E-F823-42F6-A5D9-714BDE467412}, AVI Byte Stream Handler, Preferred



--------------------------------
Media Foundation Scheme Handlers
--------------------------------


[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Media Foundation\SchemeHandlers]
[HKEY_LOCAL_MACHINE\Software\Classes\MediaFoundation\MediaSources\Preferred]


<URL type>, <handler CLSID>, <brief description>[, Preferred]


file:, {477EC299-1421-4BDD-971F-7CCB933F21AD}, File Scheme Handler, Preferred
http:, {44CB442B-9DA9-49DF-B3FD-023777B16E50}, Http Scheme Handler
http:, {9EC4B4F9-3029-45AD-947B-344DE2A249E2}, Urlmon Scheme Handler
http:, {E9F4EBAB-D97B-463E-A2B1-C54EE3F9414D}, Net Scheme Handler, Preferred
httpd:, {44CB442B-9DA9-49DF-B3FD-023777B16E50}, Http Scheme Handler, Preferred
httpnd:, {2EEEED04-0908-4CDB-AF8F-AC5B768A34C9}, Drm Scheme Handler, Preferred
https:, {37A61C8B-7F8E-4D08-B12B-248D73E9AB4F}, Secure Http Scheme Handler, Preferred
httpsd:, {37A61C8B-7F8E-4D08-B12B-248D73E9AB4F}, Secure Http Scheme Handler, Preferred
httpt:, {E9F4EBAB-D97B-463E-A2B1-C54EE3F9414D}, Net Scheme Handler, Preferred
httpu:, {E9F4EBAB-D97B-463E-A2B1-C54EE3F9414D}, Net Scheme Handler, Preferred
mcast:, {E9F4EBAB-D97B-463E-A2B1-C54EE3F9414D}, Net Scheme Handler, Preferred
mcrecv:, {FA6D33D4-9405-4BA5-9983-12604AC8E77A}, Miracast Sink Scheme Handler, Preferred
mms:, {E9F4EBAB-D97B-463E-A2B1-C54EE3F9414D}, Net Scheme Handler, Preferred
ms-appdata:, {CFC81939-3886-4ACF-9692-DA58037AE716}, MsAppData Scheme Handler, Preferred
ms-appx-web:, {8DB0224B-3D65-4F6F-8E12-BEB4B78B8974}, MsAppxWeb Scheme Handler, Preferred
ms-appx:, {8DB0224B-3D65-4F6F-8E12-BEB4B78B8974}, MsAppx Scheme Handler, Preferred
ms-winsoundevent:, {F79A6BF9-7415-4CF3-AE10-4559509ABC3C}, Sound Event Scheme Handler, Preferred
rtsp:, {E9F4EBAB-D97B-463E-A2B1-C54EE3F9414D}, Net Scheme Handler, Preferred
rtspt:, {E9F4EBAB-D97B-463E-A2B1-C54EE3F9414D}, Net Scheme Handler, Preferred
rtspu:, {E9F4EBAB-D97B-463E-A2B1-C54EE3F9414D}, Net Scheme Handler, Preferred
sdp:, {E9F4EBAB-D97B-463E-A2B1-C54EE3F9414D}, Net Scheme Handler, Preferred



-------------------------------------
Preferred Media Foundation Transforms
-------------------------------------


[HKEY_LOCAL_MACHINE\Software\Classes\MediaFoundation\Transforms\Preferred]


<media subtype GUID>, [<transform friendly name>, ]<transform CLSID>


{E06D802C-DB46-11CF-B4D1-00805F6CBBEA}, Microsoft Dolby Digital Plus Decoder MFT, {177C0AFE-900B-48D4-9E4C-57ADD250B3D4}
MFVideoFormat_MPEG2, Microsoft MPEG Video Decoder MFT, {2D709E52-123F-49B5-9CBC-9AF5CDE28FB9}
MEDIASUBTYPE_DOLBY_DDPLUS, Microsoft Dolby Digital Plus Decoder MFT, {177C0AFE-900B-48D4-9E4C-57ADD250B3D4}
{7634706D-0000-0010-8000-00AA00389B71}, Mpeg4s Decoder MFT, CLSID_CMpeg4sDecMFT
{73616D72-767A-494D-B478-F29D25DC9037}, MS AMRNB Decoder MFT, {265011AE-5481-4F77-A295-ABB6FFE8D63E}
MEDIASUBTYPE_mp4s, Mpeg4s Decoder MFT, CLSID_CMpeg4sDecMFT
MFVideoFormat_DVSL, DV Decoder MFT, {404A6DE5-D4D6-4260-9BC7-5A6CBD882432}
MFVideoFormat_DVSD, DV Decoder MFT, {404A6DE5-D4D6-4260-9BC7-5A6CBD882432}
MFVideoFormat_DVHD, DV Decoder MFT, {404A6DE5-D4D6-4260-9BC7-5A6CBD882432}
{63616C61-0000-0010-8000-00AA00389B71}, Microsoft ALAC Audio Decoder MFT, {C0CD7D12-31FC-4BBC-B363-7322EE3E1879}
MFVideoFormat_MP4V, Mpeg4s Decoder MFT, CLSID_CMpeg4sDecMFT
{53564548-0000-0010-8000-00AA00389B71}, Microsoft H265 Video Decoder MFT, {420A51A3-D605-430C-B4FC-45274FA6C562}
MFVideoFormat_MP4S, Mpeg4s Decoder MFT, CLSID_CMpeg4sDecMFT
{53314356-0000-0010-8000-00AA00389B71}, WMVideo Decoder MFT, CLSID_CWMVDecMediaObject
MEDIASUBTYPE_WMVR, WMVideo Decoder MFT, CLSID_CWMVDecMediaObject
MEDIASUBTYPE_WMVP, WMVideo Decoder MFT, CLSID_CWMVDecMediaObject
MFVideoFormat_MJPG, MJPEG Decoder MFT, {CB17E772-E1CC-4633-8450-5617AF577905}
{43564548-0000-0010-8000-00AA00389B71}, Microsoft H265 Video Decoder MFT, {420A51A3-D605-430C-B4FC-45274FA6C562}
MEDIASUBTYPE_WMVA, WMVideo Decoder MFT, CLSID_CWMVDecMediaObject
{3F40F4F0-5622-4FF8-B6D8-A17A584BEE5E}, Microsoft H264 Video Decoder MFT, CLSID_CMSH264DecoderMFT
MEDIASUBTYPE_mpg4, Mpeg4 Decoder MFT, CLSID_CMpeg4DecMediaObject
MEDIASUBTYPE_MPG4, Mpeg4 Decoder MFT, CLSID_CMpeg4DecMediaObject
MFVideoFormat_H264, Microsoft H264 Video Decoder MFT, CLSID_CMSH264DecoderMFT
MFVideoFormat_WMV3, WMVideo Decoder MFT, CLSID_CWMVDecMediaObject
{33363248-0000-0010-8000-00AA00389B71}, Mpeg4s Decoder MFT, CLSID_CMpeg4sDecMFT
MEDIASUBTYPE_mp43, Mpeg43 Decoder MFT, CLSID_CMpeg43DecMediaObject
MFVideoFormat_MP43, Mpeg43 Decoder MFT, CLSID_CMpeg43DecMediaObject
MEDIASUBTYPE_m4s2, Mpeg4s Decoder MFT, CLSID_CMpeg4sDecMFT
MFVideoFormat_WMV2, WMVideo Decoder MFT, CLSID_CWMVDecMediaObject
MFVideoFormat_MSS2, WMV Screen decoder MFT, CLSID_CMSSCDecMediaObject
MFVideoFormat_M4S2, Mpeg4s Decoder MFT, CLSID_CMpeg4sDecMFT
MEDIASUBTYPE_WVP2, WMVideo Decoder MFT, CLSID_CWMVDecMediaObject
MEDIASUBTYPE_mp42, Mpeg4 Decoder MFT, CLSID_CMpeg4DecMediaObject
MEDIASUBTYPE_MP42, Mpeg4 Decoder MFT, CLSID_CMpeg4DecMediaObject
MFVideoFormat_WMV1, WMVideo Decoder MFT, CLSID_CWMVDecMediaObject
MFVideoFormat_MSS1, WMV Screen decoder MFT, CLSID_CMSSCDecMediaObject
MFVideoFormat_MPG1, Microsoft MPEG Video Decoder MFT, {2D709E52-123F-49B5-9CBC-9AF5CDE28FB9}
MFVideoFormat_WVC1, WMVideo Decoder MFT, CLSID_CWMVDecMediaObject
MFVideoFormat_DVC, DV Decoder MFT, {404A6DE5-D4D6-4260-9BC7-5A6CBD882432}
{0000F1AC-0000-0010-8000-00AA00389B71}, Microsoft FLAC Audio Decoder MFT, {6B0B3E6B-A2C5-4514-8055-AFE8A95242D9}
{00007361-0000-0010-8000-00AA00389B71}, MS AMRNB Decoder MFT, {265011AE-5481-4F77-A295-ABB6FFE8D63E}
{00002000-0000-0010-8000-00AA00389B71}, Microsoft Dolby Digital Plus Decoder MFT, {177C0AFE-900B-48D4-9E4C-57ADD250B3D4}
MFAudioFormat_AAC, Microsoft AAC Audio Decoder MFT, CLSID_CMSAACDecMFT
MFAudioFormat_WMAudio_Lossless, WMAudio Decoder MFT, CLSID_CWMADecMediaObject
MFAudioFormat_WMAudioV9, WMAudio Decoder MFT, CLSID_CWMADecMediaObject
MFAudioFormat_WMAudioV8, WMAudio Decoder MFT, CLSID_CWMADecMediaObject
MEDIASUBTYPE_MSAUDIO1, WMAudio Decoder MFT, CLSID_CWMADecMediaObject
MEDIASUBTYPE_RAW_AAC1, Microsoft AAC Audio Decoder MFT, CLSID_CMSAACDecMFT
MFAudioFormat_MP3, MP3 Decoder MFT, CLSID_CMP3DecMediaObject
MFAudioFormat_MPEG, Microsoft MPEG Audio Decoder MFT, {70707B39-B2CA-4015-ABEA-F8447D22D88B}
{00000031-0000-0010-8000-00AA00389B71}, GSM ACM Wrapper MFT, {4A76B469-7B66-4DD4-BA2D-DDF244C766DC}
{00000011-0000-0010-8000-00AA00389B71}, IMA ADPCM ACM Wrapper MFT, {A16E1BFF-A80D-48AD-AECD-A35C005685FE}
WMMEDIASUBTYPE_WMSP2, WMSpeech Decoder DMO, CLSID_CWMSPDecMediaObject
MFAudioFormat_MSP1, WMSpeech Decoder DMO, CLSID_CWMSPDecMediaObject
KSDATAFORMAT_SUBTYPE_MULAW, G711 Wrapper MFT, {92B66080-5E2D-449E-90C4-C41F268E5514}
{00000006-0000-0010-8000-00AA00389B71}, A-law Wrapper MFT, {36CB6E0C-78C1-42B2-9943-846262F31786}
KSDATAFORMAT_SUBTYPE_ADPCM, ADPCM ACM Wrapper MFT, {CA34FE0A-5722-43AD-AF23-05F7650257DD}



-------------------------------------
Disabled Media Foundation Transforms
-------------------------------------


[HKEY_LOCAL_MACHINE\Software\Classes\MediaFoundation\Transforms\DoNotUse]


<transform CLSID>






------------------------
Disabled Media Sources
------------------------


[HKEY_LOCAL_MACHINE\Software\Classes\MediaFoundation\MediaSources\DoNotUse]


<media source CLSID>



---------------
EVR Power Information
---------------
Current Setting: {5C67A112-A4C9-483F-B4A7-1D473BECAFDC} (Quality) 
  Quality Flags: 2576
    Enabled:
    Force throttling
    Allow half deinterlace
    Allow scaling
    Decode Power Usage: 100
  Balanced Flags: 1424
    Enabled:
    Force throttling
    Allow batching
    Force half deinterlace
    Force scaling
    Decode Power Usage: 50
  PowerFlags: 1424
    Enabled:
    Force throttling
    Allow batching
    Force half deinterlace
    Force scaling
    Decode Power Usage: 0


---------------
Diagnostics
---------------


Windows Error Reporting:
+++ WER0 +++:
Fault bucket , type 0


Event Name: APPCRASH


Response: Not available


Cab Id: 0






Problem signature:


P1: UE4-ShooterGame


P2: 4.5.1.0


P3: 55e8d4a5


P4: KERNELBASE.dll


P5: 10.0.10240.16384


P6: 559f38c3


P7: 00000001


P8: 000000000002A1C8


P9: !!AssertLog="Ensure condition failed: GameViewportWindow.IsValid() [File:F:\UE4\UnrealEngine\Engine\Source\Runtime\Engine\Private\GameEngine.cpp] [Line: 336] ##"


P10: UE4!D:/SteamLibrary/steamapps/common/ARK/ShooterGame/Binaries/Win64/!Game!0







+++ WER1 +++:
Fault bucket , type 0


Event Name: APPCRASH


Response: Not available


Cab Id: 0






Problem signature:


P1: UE4-ShooterGame


P2: 4.5.1.0


P3: 55e8d4a5


P4: KERNELBASE.dll


P5: 10.0.10240.16384


P6: 559f38c3


P7: 00000001


P8: 000000000002A1C8


P9: !!AssertLog="Ensure condition failed: GameViewportWindow.IsValid() [File:F:\UE4\UnrealEngine\Engine\Source\Runtime\Engine\Private\GameEngine.cpp] [Line: 336] ##"


P10: UE4!D:/SteamLibrary/steamapps/common/ARK/ShooterGame/Binaries/Win64/!Game!0







+++ WER2 +++:
Fault bucket , type 0


Event Name: APPCRASH


Response: Not available


Cab Id: 0






Problem signature:


P1: UE4-ShooterGame


P2: 4.5.1.0


P3: 55e8d4a5


P4: KERNELBASE.dll


P5: 10.0.10240.16384


P6: 559f38c3


P7: 00000001


P8: 000000000002A1C8


P9: !!AssertLog="Ensure condition failed: GameViewportWindow.IsValid() [File:F:\UE4\UnrealEngine\Engine\Source\Runtime\Engine\Private\GameEngine.cpp] [Line: 336] ##"


P10: UE4!D:/SteamLibrary/steamapps/common/ARK/ShooterGame/Binaries/Win64/!Game!0







+++ WER3 +++:
Fault bucket , type 0


Event Name: APPCRASH


Response: Not available


Cab Id: 0






Problem signature:


P1: UE4-ShooterGame


P2: 4.5.1.0


P3: 55e8d4a5


P4: KERNELBASE.dll


P5: 10.0.10240.16384


P6: 559f38c3


P7: 00000001


P8: 000000000002A1C8


P9: !!AssertLog="Ensure condition failed: GameViewportWindow.IsValid() [File:F:\UE4\UnrealEngine\Engine\Source\Runtime\Engine\Private\GameEngine.cpp] [Line: 336] ##"


P10: UE4!D:/SteamLibrary/steamapps/common/ARK/ShooterGame/Binaries/Win64/!Game!0







+++ WER4 +++:
Fault bucket , type 0


Event Name: APPCRASH


Response: Not available


Cab Id: 0






Problem signature:


P1: UE4-ShooterGame


P2: 4.5.1.0


P3: 55e8d4a5


P4: KERNELBASE.dll


P5: 10.0.10240.16384


P6: 559f38c3


P7: 00000001


P8: 000000000002A1C8


P9: !!AssertLog="Ensure condition failed: GameViewportWindow.IsValid() [File:F:\UE4\UnrealEngine\Engine\Source\Runtime\Engine\Private\GameEngine.cpp] [Line: 336] ##"


P10: UE4!D:/SteamLibrary/steamapps/common/ARK/ShooterGame/Binaries/Win64/!Game!0







+++ WER5 +++:
Fault bucket , type 0


Event Name: APPCRASH


Response: Not available


Cab Id: 0






Problem signature:


P1: UE4-ShooterGame


P2: 4.5.1.0


P3: 55e8d4a5


P4: KERNELBASE.dll


P5: 10.0.10240.16384


P6: 559f38c3


P7: 00000001


P8: 000000000002A1C8


P9: !!AssertLog="Ensure condition failed: GameViewportWindow.IsValid() [File:F:\UE4\UnrealEngine\Engine\Source\Runtime\Engine\Private\GameEngine.cpp] [Line: 336] ##"


P10: UE4!D:/SteamLibrary/steamapps/common/ARK/ShooterGame/Binaries/Win64/!Game!0







+++ WER6 +++:
Fault bucket , type 0


Event Name: APPCRASH


Response: Not available


Cab Id: 0






Problem signature:


P1: UE4-ShooterGame


P2: 4.5.1.0


P3: 55e8d4a5


P4: KERNELBASE.dll


P5: 10.0.10240.16384


P6: 559f38c3


P7: 00000001


P8: 000000000002A1C8


P9: !!AssertLog="Ensure condition failed: GameViewportWindow.IsValid() [File:F:\UE4\UnrealEngine\Engine\Source\Runtime\Engine\Private\GameEngine.cpp] [Line: 336] ##"


P10: UE4!D:/SteamLibrary/steamapps/common/ARK/ShooterGame/Binaries/Win64/!Game!0







+++ WER7 +++:
Fault bucket 124752789637, type 5


Event Name: NuiSpeechRecognitionCollection


Response: Not available


Cab Id: 0






Problem signature:


P1: en-US


P2: en-US


P3: 360


P4: 10.0.10240.16461


P5: KWS_R


P6: Windows.Desktop


P7: 0


P8: 


P9: 


P10: 







+++ WER8 +++:
Fault bucket , type 0


Event Name: APPCRASH


Response: Not available


Cab Id: 0






Problem signature:


P1: UE4-ShooterGame


P2: 4.5.1.0


P3: 55e8d4a5


P4: KERNELBASE.dll


P5: 10.0.10240.16384


P6: 559f38c3


P7: 00000001


P8: 000000000002A1C8


P9: !!AssertLog="Ensure condition failed: GameViewportWindow.IsValid() [File:F:\UE4\UnrealEngine\Engine\Source\Runtime\Engine\Private\GameEngine.cpp] [Line: 336] ##"


P10: UE4!D:/SteamLibrary/steamapps/common/ARK/ShooterGame/Binaries/Win64/!Game!0







+++ WER9 +++:
Fault bucket , type 0


Event Name: NuiSpeechRecognitionCollection


Response: Not available


Cab Id: 0






Problem signature:


P1: en-US


P2: en-US


P3: 360


P4: 10.0.10240.16461


P5: KWS_R


P6: Windows.Desktop


P7: 0


P8: 


P9: 


P10: 









```

Any help would be greatly appreciated!

---

