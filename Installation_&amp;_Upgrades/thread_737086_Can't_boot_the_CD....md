---
title: "Can't boot the CD..."
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by RSahlgren on 2008-03-27
I have burned a CD as the "Howto" told. I restart, choose to start my boot menu. Chooses the CD and wait... And then loads XP and here I am.. I burned with diffrent programs, and alternate installation. Nothing works. I did this with another CD to a other computer there i could  boot but not install. But that CD is 32 bit. And the ones i tried on this computer is 64 bit. Because I have a AMD 64 processor and I want to use that "power".

Any ideas that might help me?

Dxdiag:
```
Time of this report: 3/27/2008, 14:48:34
       Machine name: RICKARDSDATOR
   Operating System: Windows XP Home Edition (5.1, Build 2600) Service Pack 2 (2600.xpsp_sp2_gdr.070227-2254)
           Language: Swedish (Regional Setting: Swedish)
System Manufacturer: HP Pavilion 061
       System Model: RA988AA-B1U d4580.se-a
               BIOS: BIOS Ver: A7225NH5 V3.13 07/18/06 14:31:38
          Processor: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+,  MMX,  3DNow (2 CPUs), ~2.6GHz
             Memory: 2048MB RAM
          Page File: 447MB used, 3490MB available
        Windows Dir: C:\WINDOWS
    DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
     DxDiag Version: 5.03.2600.2180 32bit Unicode
```


```
---------------
Display Devices
---------------
        Card name: NVIDIA GeForce 8800 GTS
     Manufacturer: NVIDIA
        Chip type: GeForce 8800 GTS
         DAC type: Integrated RAMDAC
       Device Key: Enum\PCI\VEN_10DE&DEV_0193&SUBSYS_228919F1&REV_A2
   Display Memory: 640.0 MB
     Current Mode: 1920 x 1200 (32 bit) (60Hz)
          Monitor: Plug and Play-bildskärm
  Monitor Max Res: 1600,1200
      Driver Name: nv4_disp.dll
   Driver Version: 6.14.0011.6371 (English)
      DDI Version: 9 (or higher)
Driver Attributes: Final Retail
 Driver Date/Size: 9/17/2007 00:07:00, 5783040 bytes
      WHQL Logo'd: Yes
  WHQL Date Stamp: n/a
              VDD: Saknas
         Mini VDD: nv4_mini.sys
    Mini VDD Date: 9/17/2007 00:07:00, 6853088 bytes
Device Identifier: {D7B71E3E-42D3-11CF-A262-820203C2CB35}
        Vendor ID: 0x10DE
        Device ID: 0x0193
        SubSys ID: 0x228919F1
      Revision ID: 0x00A2
      Revision ID: 0x00A2
      Video Accel: ModeMPEG2_A ModeMPEG2_B ModeMPEG2_C ModeMPEG2_D ModeWMV9_B ModeWMV9_A 
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
```

---

### Post by Geowilky on 2008-03-27
I'm not possitive on this, but I believe you can go to the bios and only allow a boot from the cd drive.  That way XP won't boot.  After Ubuntu loads then reenable the hard drive to boot.

---

