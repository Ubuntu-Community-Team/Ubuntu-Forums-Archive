---
title: "After Installation - Kernel Error - Please Help"
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by C4U53 on 2007-07-26
What my problem is right now---

Ok so I got it all installed after several other problems that will be explained. I get happy and goto boot. on the splash screen it freezes at almost 2 1/2 bars exact. I tried then run it in the recovery console. Same thing. I then used the advanced boot method ( using e then b etc.. ) This isn't exact but very close. 

Kernel Panic : syncing kernel-i386 failed on scidi1((( ubuntu. or something of the sort ))

Before all of this - I made 2 1/2 coasters. The first coaster was my own fault and didn't realize I had it on max speed(may have been the problem though the second coaster turned the same results at a 2x speed) - It would go to start then start spiting off something like 197.238950 I/O Error Buffer (etc.. ) and would just keep incrementing up with the same error message and different numbers. I then downloaded the 3 gig DvD. it ran into another problem. I can't remember exactly what now but then I got the text installer to work (thank god) after changing it out of VGA to a 1280 x 1024 reso ( when it was in VGA it flashed real crazy and I had to restart ). So we are installing.. installing I'm happy . Get all the way to the end of installing base and I get a kernel error. I restart the install this time it allows me to select the kernel. I stuck with the one it recomended (linux-generic) and it ran into the same problem and wouldn't install. so I took the same step but this time selected the linux-386 kernel. it finishes installing as I go through some other steps until finally I end up where I am now.

Any help is appreciated.. Main reason I posted the history of everything that happend is to perhaps help others that may have run into similarities and/or developers.

DxDiag after this line ----------- Also please remember I am poor

------------------
System Information
------------------
Time of this report: 7/26/2007, 04:43:41
       Machine name: CHRIS-PC
   Operating System: Windows Vista&#8482; Home Basic (6.0, Build 6000) (6000.vista_rtm.061101-2205)
           Language: English (Regional Setting: English)
System Manufacturer: HP Pavilion 061
       System Model: PX759AA-ABA a1120n
               BIOS: BIOS Date: 03/31/05 20:06:54 Ver: 08.00.10
          Processor: Intel(R) Pentium(R) 4 CPU 3.06GHz, ~3.1GHz
             Memory: 1526MB RAM
          Page File: 553MB used, 2751MB available
        Windows Dir: C:\Windows
    DirectX Version: DirectX 10
DX Setup Parameters: Not found
     DxDiag Version: 6.00.6000.16386 32bit Unicode

------------
DxDiag Notes
------------
      Display Tab 1: No problems found.
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
        Card name: NVIDIA GeForce FX 5200
     Manufacturer: NVIDIA
        Chip type: GeForce FX 5200
         DAC type: Integrated RAMDAC
       Device Key: Enum\PCI\VEN_10DE&DEV_0322&SUBSYS_01AD196E&REV_A1
   Display Memory: 525 MB
 Dedicated Memory: 254 MB
    Shared Memory: 271 MB
     Current Mode: 1024 x 768 (32 bit) (70Hz)
          Monitor: Generic PnP Monitor
      Driver Name: nvd3dum.dll
   Driver Version: 7.15.0010.9685 (English)
      DDI Version: 9Ex
Driver Attributes: Final Retail
 Driver Date/Size: 10/9/2006 21:55:00, 3022848 bytes
      WHQL Logo'd: Yes
  WHQL Date Stamp: 
Device Identifier: {D7B71E3E-4062-11CF-0B5F-A72101C2CA35}
        Vendor ID: 0x10DE
        Device ID: 0x0322
        SubSys ID: 0x01AD196E
      Revision ID: 0x00A1
      Revision ID: 0x00A1
      Video Accel: ModeMPEG2_A ModeMPEG2_C 
 Deinterlace Caps: {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                   {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(UYVY,UYVY) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                   {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(UYVY,UYVY) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YV12,0x32315659) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                   {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(YV12,0x32315659) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                   {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(IMC1,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                   {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(IMC1,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(IMC2,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                   {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(IMC2,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(IMC3,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                   {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(IMC3,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(IMC4,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                   {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(IMC4,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(S340,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                   {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(S340,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(S342,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
                   {5A54A0C9-C7EC-4BD9-8EDE-F3C75DC4393B}: Format(In/Out)=(S342,UNKNOWN) Frames(Prev/Fwd/Back)=(0,0,0) Caps=
     DDraw Status: Enabled
       D3D Status: Enabled
       AGP Status: Enabled

-------------
Sound Devices
-------------
            Description: Speakers (High Definition Audio Device)
 Default Sound Playback: Yes
 Default Voice Playback: Yes
            Hardware ID: HDAUDIO\FUNC_01&VEN_10EC&DEV_0880&SUBSYS_08800000&REV_0905
        Manufacturer ID: 1
             Product ID: 100
                   Type: WDM
            Driver Name: HdAudio.sys
         Driver Version: 6.00.5840.16387 (English)
      Driver Attributes: Final Retail
            WHQL Logo'd: Yes
          Date and Size: 11/2/2006 03:36:49, 235520 bytes
            Other Files: 
        Driver Provider: Microsoft
         HW Accel Level: Basic
              Cap Flags: 0xF1F
    Min/Max Sample Rate: 100, 200000
Static/Strm HW Mix Bufs: 1, 0
 Static/Strm HW 3D Bufs: 0, 0
              HW Memory: 0
       Voice Management: No
 EAX(tm) 2.0 Listen/Src: No, No
   I3DL2(tm) Listen/Src: No, No
Sensaura(tm) ZoomFX(tm): No

            Description: Headphones (High Definition Audio Device)
 Default Sound Playback: No
 Default Voice Playback: No
            Hardware ID: HDAUDIO\FUNC_01&VEN_10EC&DEV_0880&SUBSYS_08800000&REV_0905
        Manufacturer ID: 1
             Product ID: 100
                   Type: WDM
            Driver Name: HdAudio.sys
         Driver Version: 6.00.5840.16387 (English)
      Driver Attributes: Final Retail
            WHQL Logo'd: Yes
          Date and Size: 11/2/2006 03:36:49, 235520 bytes
            Other Files: 
        Driver Provider: Microsoft
         HW Accel Level: Basic
              Cap Flags: 0xF1F
    Min/Max Sample Rate: 100, 200000
Static/Strm HW Mix Bufs: 1, 0
 Static/Strm HW 3D Bufs: 0, 0
              HW Memory: 0
       Voice Management: No
 EAX(tm) 2.0 Listen/Src: No, No
   I3DL2(tm) Listen/Src: No, No
Sensaura(tm) ZoomFX(tm): No

            Description: Digital Output Device (SPDIF) (High Definition Audio Device)
 Default Sound Playback: No
 Default Voice Playback: No
            Hardware ID: HDAUDIO\FUNC_01&VEN_10EC&DEV_0880&SUBSYS_08800000&REV_0905
        Manufacturer ID: 1
             Product ID: 100
                   Type: WDM
            Driver Name: HdAudio.sys
         Driver Version: 6.00.5840.16387 (English)
      Driver Attributes: Final Retail
            WHQL Logo'd: Yes
          Date and Size: 11/2/2006 03:36:49, 235520 bytes
            Other Files: 
        Driver Provider: Microsoft
         HW Accel Level: Basic
              Cap Flags: 0xF1F
    Min/Max Sample Rate: 100, 200000
Static/Strm HW Mix Bufs: 1, 0
 Static/Strm HW 3D Bufs: 0, 0
              HW Memory: 0
       Voice Management: No
 EAX(tm) 2.0 Listen/Src: No, No
   I3DL2(tm) Listen/Src: No, No
Sensaura(tm) ZoomFX(tm): No

---------------------
Sound Capture Devices
---------------------
            Description: Microphone (High Definition Audio Device)
  Default Sound Capture: Yes
  Default Voice Capture: Yes
            Driver Name: HdAudio.sys
         Driver Version: 6.00.5840.16387 (English)
      Driver Attributes: Final Retail
          Date and Size: 11/2/2006 03:36:49, 235520 bytes
              Cap Flags: 0x1
           Format Flags: 0xFFFFF

            Description: Microphone (High Definition Audio Device)
  Default Sound Capture: No
  Default Voice Capture: No
            Driver Name: HdAudio.sys
         Driver Version: 6.00.5840.16387 (English)
      Driver Attributes: Final Retail
          Date and Size: 11/2/2006 03:36:49, 235520 bytes
              Cap Flags: 0x1
           Format Flags: 0xFFFFF

            Description: Line In (High Definition Audio Device)
  Default Sound Capture: No
  Default Voice Capture: No
            Driver Name: HdAudio.sys
         Driver Version: 6.00.5840.16387 (English)
      Driver Attributes: Final Retail
          Date and Size: 11/2/2006 03:36:49, 235520 bytes
              Cap Flags: 0x1
           Format Flags: 0xFFFFF

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

Poll w/ Interrupt: No

-----------
USB Devices
-----------
+ USB Root Hub
| Vendor/Product ID: 0x8086, 0x2658
| Matching Device ID: usb\root_hub
| Service: usbhub
| Driver: usbhub.sys, 11/2/2006 04:55:21, 191488 bytes
| Driver: usbd.sys, 11/2/2006 04:55:00, 5888 bytes
| 
+-+ USB Human Interface Device
| | Vendor/Product ID: 0x046D, 0xC016
| | Location: Port_#0002.Hub_#0001
| | Matching Device ID: usb\class_03&subclass_01
| | Service: HidUsb
| | Driver: hidusb.sys, 11/2/2006 04:55:01, 12288 bytes
| | Driver: hidclass.sys, 11/2/2006 04:55:01, 38912 bytes
| | Driver: hidparse.sys, 11/2/2006 04:55:00, 25472 bytes
| | 
| +-+ HID-compliant mouse
| | | Vendor/Product ID: 0x046D, 0xC016
| | | Matching Device ID: hid_device_system_mouse
| | | Service: mouhid
| | | Driver: mouhid.sys, 11/2/2006 04:51:12, 15872 bytes
| | | Driver: mouclass.sys, 11/2/2006 05:49:54, 31848 bytes

----------------
Gameport Devices
----------------

------------
PS/2 Devices
------------
+ Standard 101/102-Key or Microsoft Natural PS/2 Keyboard
| Matching Device ID: *pnp0303
| Service: i8042prt
| Driver: i8042prt.sys, 11/2/2006 04:51:13, 54784 bytes
| Driver: kbdclass.sys, 11/2/2006 05:49:57, 32872 bytes
| 
+ Terminal Server Keyboard Driver
| Matching Device ID: root\rdp_kbd
| Upper Filters: kbdclass
| Service: TermDD
| Driver: i8042prt.sys, 11/2/2006 04:51:13, 54784 bytes
| Driver: kbdclass.sys, 11/2/2006 05:49:57, 32872 bytes
| 
+ Terminal Server Mouse Driver
| Matching Device ID: root\rdp_mou
| Upper Filters: mouclass
| Service: TermDD
| Driver: termdd.sys, 11/2/2006 05:50:28, 50792 bytes
| Driver: sermouse.sys, 11/2/2006 04:51:11, 19968 bytes
| Driver: mouclass.sys, 11/2/2006 05:49:54, 31848 bytes

------------------------
Disk & DVD/CD-ROM Drives
------------------------
      Drive: C:
 Free Space: 31.9 GB
Total Space: 148.4 GB
File System: NTFS
      Model: ST3200822AS ATA Device

      Drive: D:
      Model: HP DVD Writer 640c ATA Device
     Driver: c:\windows\system32\drivers\cdrom.sys, 6.00.6000.16386 (English), 11/2/2006 04:51:44, 67072 bytes

      Drive: J:
      Model: IDE-CD   CROM6048 ATA Device
     Driver: c:\windows\system32\drivers\cdrom.sys, 6.00.6000.16386 (English), 11/2/2006 04:51:44, 67072 bytes

      Drive: K:
      Model: RB5539B NHU939F SCSI CdRom Device
     Driver: c:\windows\system32\drivers\cdrom.sys, 6.00.6000.16386 (English), 11/2/2006 04:51:44, 67072 bytes

--------------
System Devices
--------------
     Name: Intel(R) 82801FB/FBM Ultra ATA Storage Controllers - 266F
Device ID: PCI\VEN_8086&DEV_266F&SUBSYS_2A0A103C&REV_03\3&11583659&0&F9
   Driver: C:\Windows\system32\DRIVERS\intelide.sys, 6.00.6000.16386 (English), 11/2/2006 05:49:24, 14952 bytes
   Driver: C:\Windows\system32\DRIVERS\pciidex.sys, 6.00.6000.16386 (English), 11/2/2006 05:50:18, 42600 bytes
   Driver: C:\Windows\system32\DRIVERS\atapi.sys, 6.00.6000.16386 (English), 11/2/2006 05:49:36, 19048 bytes
   Driver: C:\Windows\system32\DRIVERS\ataport.sys, 6.00.6000.16386 (English), 11/2/2006 05:50:41, 107112 bytes

     Name: Intel(R) 82801FB/FBM SMBus Controller - 266A
Device ID: PCI\VEN_8086&DEV_266A&SUBSYS_2A0A103C&REV_03\3&11583659&0&FB
   Driver: n/a

     Name: High Definition Audio Controller
Device ID: PCI\VEN_8086&DEV_2668&SUBSYS_2A09103C&REV_03\3&11583659&0&D8
   Driver: C:\Windows\system32\DRIVERS\hdaudbus.sys, 6.00.6000.16386 (English), 7/12/2007 03:04:40, 53760 bytes

     Name: Intel(R) 82801FB/FBM PCI Express Root Port - 2660
Device ID: PCI\VEN_8086&DEV_2660&SUBSYS_2A0A103C&REV_03\3&11583659&0&E0
   Driver: C:\Windows\system32\DRIVERS\pci.sys, 6.00.6000.16386 (English), 11/2/2006 05:50:57, 140392 bytes

     Name: Intel(R) 82801FB/FBM USB2 Enhanced Host Controller - 265C
Device ID: PCI\VEN_8086&DEV_265C&SUBSYS_2A0A103C&REV_03\3&11583659&0&EF
   Driver: C:\Windows\system32\drivers\usbehci.sys, 6.00.6000.16386 (English), 11/2/2006 04:55:04, 38400 bytes
   Driver: C:\Windows\system32\drivers\usbport.sys, 6.00.6000.16386 (English), 11/2/2006 04:55:11, 223744 bytes
   Driver: C:\Windows\system32\drivers\usbhub.sys, 6.00.6000.16386 (English), 11/2/2006 04:55:21, 191488 bytes
   Driver: C:\Windows\system32\hccoin.dll, 6.00.6000.16386 (English), 11/2/2006 05:46:05, 8704 bytes

     Name: Intel(R) 82801FB/FBM USB Universal Host Controller - 265B
Device ID: PCI\VEN_8086&DEV_265B&SUBSYS_2A0A103C&REV_03\3&11583659&0&EB
   Driver: C:\Windows\system32\drivers\usbuhci.sys, 6.00.6000.16386 (English), 11/2/2006 04:55:05, 22528 bytes
   Driver: C:\Windows\system32\drivers\usbport.sys, 6.00.6000.16386 (English), 11/2/2006 04:55:11, 223744 bytes
   Driver: C:\Windows\system32\drivers\usbhub.sys, 6.00.6000.16386 (English), 11/2/2006 04:55:21, 191488 bytes

     Name: Intel(R) 82801FB/FBM USB Universal Host Controller - 265A
Device ID: PCI\VEN_8086&DEV_265A&SUBSYS_2A0A103C&REV_03\3&11583659&0&EA
   Driver: C:\Windows\system32\drivers\usbuhci.sys, 6.00.6000.16386 (English), 11/2/2006 04:55:05, 22528 bytes
   Driver: C:\Windows\system32\drivers\usbport.sys, 6.00.6000.16386 (English), 11/2/2006 04:55:11, 223744 bytes
   Driver: C:\Windows\system32\drivers\usbhub.sys, 6.00.6000.16386 (English), 11/2/2006 04:55:21, 191488 bytes

     Name: Intel(R) 82801FB/FBM USB Universal Host Controller - 2659
Device ID: PCI\VEN_8086&DEV_2659&SUBSYS_2A0A103C&REV_03\3&11583659&0&E9
   Driver: C:\Windows\system32\drivers\usbuhci.sys, 6.00.6000.16386 (English), 11/2/2006 04:55:05, 22528 bytes
   Driver: C:\Windows\system32\drivers\usbport.sys, 6.00.6000.16386 (English), 11/2/2006 04:55:11, 223744 bytes
   Driver: C:\Windows\system32\drivers\usbhub.sys, 6.00.6000.16386 (English), 11/2/2006 04:55:21, 191488 bytes

     Name: Intel(R) 82801FB/FBM USB Universal Host Controller - 2658
Device ID: PCI\VEN_8086&DEV_2658&SUBSYS_2A0A103C&REV_03\3&11583659&0&E8
   Driver: C:\Windows\system32\drivers\usbuhci.sys, 6.00.6000.16386 (English), 11/2/2006 04:55:05, 22528 bytes
   Driver: C:\Windows\system32\drivers\usbport.sys, 6.00.6000.16386 (English), 11/2/2006 04:55:11, 223744 bytes
   Driver: C:\Windows\system32\drivers\usbhub.sys, 6.00.6000.16386 (English), 11/2/2006 04:55:21, 191488 bytes

     Name: Intel(R) 82801FB Ultra ATA Storage Controllers - 2651
Device ID: PCI\VEN_8086&DEV_2651&SUBSYS_2A0A103C&REV_03\3&11583659&0&FA
   Driver: C:\Windows\system32\DRIVERS\intelide.sys, 6.00.6000.16386 (English), 11/2/2006 05:49:24, 14952 bytes
   Driver: C:\Windows\system32\DRIVERS\pciidex.sys, 6.00.6000.16386 (English), 11/2/2006 05:50:18, 42600 bytes
   Driver: C:\Windows\system32\DRIVERS\atapi.sys, 6.00.6000.16386 (English), 11/2/2006 05:49:36, 19048 bytes
   Driver: C:\Windows\system32\DRIVERS\ataport.sys, 6.00.6000.16386 (English), 11/2/2006 05:50:41, 107112 bytes

     Name: Intel(R) 82801FB LPC Interface Controller - 2640
Device ID: PCI\VEN_8086&DEV_2640&SUBSYS_2A0A103C&REV_03\3&11583659&0&F8
   Driver: C:\Windows\system32\DRIVERS\msisadrv.sys, 6.00.6000.16386 (English), 11/2/2006 05:49:20, 13928 bytes

     Name: Intel(R) 82915G/GV/910GL Express Chipset Family (Microsoft Corporation - XDDM)
Device ID: PCI\VEN_8086&DEV_2582&SUBSYS_2A08103C&REV_04\3&11583659&0&10
   Driver: C:\Windows\system32\DRIVERS\ialmnt5.sys, 6.14.0010.4656 (English), 11/2/2006 03:36:45, 1302492 bytes
   Driver: C:\Windows\system32\ialmrnt5.dll, 6.14.0010.4656 (English), 11/2/2006 05:39:29, 36990 bytes
   Driver: C:\Windows\system32\ialmdnt5.dll, 6.14.0010.4656 (English), 11/2/2006 05:39:29, 118395 bytes
   Driver: C:\Windows\system32\ialmdev5.dll, 6.14.0010.4656 (English), 11/2/2006 05:39:29, 213274 bytes
   Driver: C:\Windows\system32\ialmdd5.dll, 6.14.0010.4656 (English), 11/2/2006 05:39:29, 902266 bytes
   Driver: C:\Windows\system32\igxpxa32.cpa, 9/18/2006 17:29:22, 524850 bytes
   Driver: C:\Windows\system32\igxpxa32.vp, 9/18/2006 17:29:22, 929 bytes
   Driver: C:\Windows\system32\igxpxk32.vp, 9/18/2006 17:29:22, 58704 bytes
   Driver: C:\Windows\system32\igxpxs32.vp, 9/18/2006 17:29:22, 24704 bytes

     Name: Intel(R) 915G/P/GV/GL/PL/910GE/GL Processor to I/O Controller - 2580
Device ID: PCI\VEN_8086&DEV_2580&SUBSYS_2A08103C&REV_04\3&11583659&0&00
   Driver: n/a

     Name: Intel(R) 82801 PCI Bridge - 244E
Device ID: PCI\VEN_8086&DEV_244E&SUBSYS_2A0A103C&REV_D3\3&11583659&0&F0
   Driver: C:\Windows\system32\DRIVERS\pci.sys, 6.00.6000.16386 (English), 11/2/2006 05:50:57, 140392 bytes

     Name: Agere Systems PCI Soft Modem
Device ID: PCI\VEN_11C1&DEV_048C&SUBSYS_044C11C1&REV_03\4&254543F0&0&20F0
   Driver: C:\Windows\system32\DRIVERS\AGRSM.sys, 2.01.0077.0000 (English), 11/28/2006 20:11:00, 1161888 bytes
   Driver: C:\Windows\system32\agrsmsvc.exe, 1.00.0000.0004 (English), 10/5/2006 17:10:12, 9216 bytes
   Driver: C:\Windows\agrsmdel.exe, 2.02.0000.0000 (English), 10/26/2006 18:08:44, 50752 bytes
   Driver: C:\Windows\system32\agrscoin.dll, 1.00.0000.0004 (English), 9/11/2006 19:34:46, 13312 bytes

     Name: VIA OHCI Compliant IEEE 1394 Host Controller
Device ID: PCI\VEN_1106&DEV_3044&SUBSYS_2A0C103C&REV_80\4&254543F0&0&08F0
   Driver: C:\Windows\system32\DRIVERS\ohci1394.sys, 6.00.6000.16386 (English), 11/2/2006 04:55:16, 62080 bytes
   Driver: C:\Windows\system32\DRIVERS\1394bus.sys, 6.00.6000.16386 (English), 11/2/2006 04:55:12, 53376 bytes

     Name: Realtek RTL8139/810x Family Fast Ethernet NIC
Device ID: PCI\VEN_10EC&DEV_8139&SUBSYS_2A0B103C&REV_10\4&254543F0&0&10F0
   Driver: C:\Windows\system32\DRIVERS\Rtnicxp.sys, 6.103.0123.2007 (English), 1/23/2007 11:01:00, 50176 bytes

     Name: NVIDIA GeForce FX 5200
Device ID: PCI\VEN_10DE&DEV_0322&SUBSYS_01AD196E&REV_A1\4&254543F0&0&18F0
   Driver: C:\Windows\system32\DRIVERS\nvlddmkm.sys, 7.15.0010.9685 (English), 10/9/2006 21:55:00, 4428160 bytes
   Driver: C:\Windows\system32\nvd3dum.dll, 7.15.0010.9685 (English), 10/9/2006 21:55:00, 3022848 bytes
   Driver: C:\Windows\system32\nvapi.dll, 7.15.0010.9685 (English), 10/9/2006 21:55:00, 286720 bytes
   Driver: C:\Windows\system32\nvoglv32.dll, 7.15.0010.9685 (English), 10/9/2006 21:55:00, 5685248 bytes
   Driver: C:\Windows\system32\nvcpl.dll, 7.15.0010.9685 (English), 10/9/2006 21:55:00, 7741440 bytes
   Driver: C:\Windows\system32\nvsvc.dll, 7.15.0010.9685 (English), 10/9/2006 21:55:00, 90191 bytes
   Driver: C:\Windows\system32\nvmctray.dll, 7.15.0010.9685 (English), 10/9/2006 21:55:00, 81920 bytes
   Driver: C:\Windows\system32\nvdisps.dll, 7.15.0010.9685 (English), 10/9/2006 21:55:00, 5611520 bytes
   Driver: C:\Windows\system32\nvdispsr.dll, 7.15.0010.9685 (English), 10/9/2006 21:55:00, 5226496 bytes
   Driver: C:\Windows\system32\nvgames.dll, 7.15.0010.9685 (English), 10/9/2006 21:55:00, 3051520 bytes
   Driver: C:\Windows\system32\nvgamesr.dll, 7.15.0010.9685 (English), 10/9/2006 21:55:00, 2945024 bytes
   Driver: C:\Windows\system32\nvmccss.dll, 7.15.0010.9685 (English), 10/9/2006 21:55:00, 188416 bytes
   Driver: C:\Windows\system32\nvmccssr.dll, 7.15.0010.9685 (English), 10/9/2006 21:55:00, 458752 bytes
   Driver: C:\Windows\system32\nvmobls.dll, 7.15.0010.9685 (English), 10/9/2006 21:55:00, 888832 bytes
   Driver: C:\Windows\system32\nvmoblsr.dll, 7.15.0010.9685 (English), 10/9/2006 21:55:00, 2854912 bytes
   Driver: C:\Windows\system32\nvvitvs.dll, 7.15.0010.9685 (English), 10/9/2006 21:55:00, 2924544 bytes
   Driver: C:\Windows\system32\nvvitvsr.dll, 7.15.0010.9685 (English), 10/9/2006 21:55:00, 2969600 bytes
   Driver: C:\Windows\system32\nvmccs.dll, 7.15.0010.9685 (English), 10/9/2006 21:55:00, 229376 bytes
   Driver: C:\Windows\system32\nvmccsrs.dll, 7.15.0010.9685 (Arabic), 10/9/2006 21:55:00, 45056 bytes
   Driver: C:\Windows\system32\nvcpluir.dll, 1.03.0009.0001 (English), 10/9/2006 21:55:00, 1015808 bytes
   Driver: C:\Windows\system32\nvexpbar.dll, 1.03.0009.0001 (English), 10/9/2006 21:55:00, 307200 bytes
   Driver: C:\Windows\system32\nvcpl.cpl, 1.03.0009.0001 (English), 10/9/2006 21:55:00, 69632 bytes
   Driver: C:\Windows\system32\nvcolor.exe, 7.15.0010.9685 (English), 10/9/2006 21:55:00, 147456 bytes
   Driver: C:\Windows\system32\nvcplui.exe, 1.03.0009.0001 (English), 10/9/2006 21:55:00, 806912 bytes
   Driver: C:\Windows\system32\nvudisp.exe, 1.00.0001.0056 (English), 10/9/2006 21:55:00, 356352 bytes
   Driver: C:\Windows\system32\nvapps.xml, 10/9/2006 21:55:00, 87549 bytes
   Driver: C:\Windows\system32\nvwsapps.xml, 10/9/2006 21:55:00, 70770 bytes
   Driver: C:\Windows\help\nvcpl\nvcpl.chm, 10/9/2006 21:55:00, 104248 bytes
   Driver: C:\Windows\help\nvcpl\nvdsp.chm, 10/9/2006 21:55:00, 182371 bytes
   Driver: C:\Windows\help\nvcpl\nv3d.chm, 10/9/2006 21:55:00, 99664 bytes
   Driver: C:\Windows\help\nvcpl\nvmob.chm, 10/9/2006 21:55:00, 54878 bytes

------------------
DirectShow Filters
------------------

DirectShow Filters:
WMAudio Decoder DMO,0x00800800,1,1,,
WMAPro over S/PDIF DMO,0x00600800,1,1,,
WMSpeech Decoder DMO,0x00600800,1,1,,
MP3 Decoder DMO,0x00600800,1,1,,
Mpeg4s Decoder DMO,0x00800001,1,1,,
WMV Screen decoder DMO,0x00600800,1,1,,
WMVideo Decoder DMO,0x00800001,1,1,,
Mpeg43 Decoder DMO,0x00800001,1,1,,
Mpeg4 Decoder DMO,0x00800001,1,1,,
Full Screen Renderer,0x00200000,1,0,,6.06.6000.16386
Multiple File Output,0x00200000,2,2,WMM2FILT.dll,
WMT Black Frame Generator,0x00200000,1,1,WMM2FILT.dll,
WMT Import Filter,0x00200000,0,1,WMM2FILT.dll,
DV Muxer,0x00400000,0,0,,6.06.6000.16386
Elecard MPEG Demultiplexer,0x00800200,1,2,empgdmx.ax,1.00.0077.60823
Color Space Converter,0x00400001,1,1,,6.06.6000.16386
VFW Sample Grabber,0x00200000,1,1,P0620Vfw.dll,1.01.0001.6784
WMT Interlacer,0x00200000,1,1,WMM2FILT.dll,
LogMeIn Video Encoder,0x00400000,1,1,racodec.ax,
WM ASF Reader,0x00400000,0,0,,11.00.6000.6324
Screen Capture filter,0x00200000,0,1,wmpsrcwp.dll,11.00.6000.6324
AVI Splitter,0x00600000,1,1,,6.06.6000.16386
VGA 16 Color Ditherer,0x00400000,1,1,,6.06.6000.16386
AC3 Parser Filter,0x00600000,1,1,mpg2splt.ax,6.06.6000.16386
WMT Format Conversion,0x00200000,1,1,WMM2FILT.dll,
9x8Resize,0x00200000,1,1,WMM2FILT.dll,
StreamBufferSink,0x00200000,0,0,sbe.dll,6.06.6000.16386
WMT Virtual Source,0x00200000,0,1,WMM2FILT.dll,
MJPEG Decompressor,0x00600000,1,1,,6.06.6000.16386
MPEG-I Stream Splitter,0x00600000,1,2,,6.06.6000.16386
SAMI (CC) Parser,0x00400000,1,1,,6.06.6000.16386
VBI Codec,0x00600000,1,4,VBICodec.ax,6.06.6000.16386
MPEG-2 Splitter,0x005fffff,1,0,mpg2splt.ax,6.06.6000.16386
WMT AudioAnalyzer,0x00200000,1,1,WMM2FILT.dll,
LogMeIn Video Decoder,0x00800000,1,1,racodec.ax,
Stretch Video,0x00200000,1,1,WMM2FILT.dll,
Internal Script Command Renderer,0x00800001,1,0,,6.06.6000.16386
MPEG Audio Decoder,0x03680001,1,1,,6.06.6000.16386
DV Splitter,0x00600000,1,2,,6.06.6000.16386
Video Mixing Renderer 9,0x00200000,1,0,,6.06.6000.16386
Frame Eater,0x00200000,1,1,WMM2FILT.dll,
Elecard NWSource-Plus,0x00200000,0,0,enwsplus.ax,1.01.0015.60823
Allocator Fix,0x00200000,1,1,WMM2FILT.dll,
Elecard MPEG Push Demultiplexer,0x00200000,1,2,empgpdmx.ax,1.00.0049.60828
ACM Wrapper,0x00600000,1,1,,6.06.6000.16386
Video Renderer,0x00800001,1,0,,6.06.6000.16386
MPEG-2 Video Stream Analyzer,0x00200000,0,0,sbe.dll,6.06.6000.16386
Capture ASF Writer,0x00200000,0,0,WMM2FILT.dll,
Line 21 Decoder,0x00600000,1,1,,6.06.6000.16386
Video Port Manager,0x00600000,2,1,,6.06.6000.16386
Elecard RTSP NetSource,0x00200000,0,1,ertspnws.ax,1.00.0025.60818
Video Renderer,0x00400000,1,0,,6.06.6000.16386
Bitmap Generate,0x00200000,1,1,WMM2FILT.dll,
Proxy Sink,0x00200000,1,0,WMM2FILT.dll,
DivX Decoder Filter,0xff800000,1,1,divxdec.ax,6.06.0001.0004
Proxy Source,0x00200000,0,1,WMM2FILT.dll,
WM ASF Writer,0x00400000,0,0,,11.00.6000.6324
VBI Surface Allocator,0x00600000,1,1,vbisurf.ax,6.00.6000.16386
WMT Sample Information Filter,0x00200000,1,1,WMM2FILT.dll,
DivX Demux,0x00600000,1,0,DivXMedia.ax,0.00.0000.0028
File writer,0x00200000,1,0,,6.06.6000.16386
DVD Navigator,0x00200000,0,3,,6.06.6000.16386
WMT DV Extract,0x00200000,1,1,WMM2FILT.dll,
Overlay Mixer2,0x00200000,1,1,,6.06.6000.16386
VFW Null Render Filter,0x00200000,1,0,P0620Vfw.dll,1.01.0001.6784
AVI Draw,0x00600064,9,1,,6.06.6000.16386
WST Pager,0x00800000,1,1,WSTPager.ax,6.06.6000.16386
MPEG-2 Demultiplexer,0x00600000,1,1,mpg2splt.ax,6.06.6000.16386
Record Queue,0x00200000,1,1,WMM2FILT.dll,
DV Video Decoder,0x00800000,1,1,,6.06.6000.16386
DivX Subtitle Decoder,0x00600000,1,1,DivXMedia.ax,0.00.0000.0028
Elecard MPEG-2 Video Decoder,0x00800001,2,2,em2vd.ax,1.00.0197.60322
SampleGrabber,0x00200000,1,1,qedit.dll,6.06.6000.16386
Null Renderer,0x00200000,1,0,qedit.dll,6.06.6000.16386
WMT Log Filter,0x00200000,1,1,WMM2FILT.dll,
MPEG-2 Sections and Tables,0x005fffff,1,0,Mpeg2Data.ax,6.06.6000.16386
WMT Virtual Renderer,0x00200000,1,0,WMM2FILT.dll,
StreamBufferSource,0x00200000,0,0,sbe.dll,6.06.6000.16386
Ligos MPEG Video Decoder,0x00800000,1,1,Mpeg2Decoder.ax,1.02.0000.0079
Smart Tee,0x00200000,1,2,,6.06.6000.16386
Overlay Mixer,0x00200000,0,0,,6.06.6000.16386
AVI Decompressor,0x00600000,1,1,,6.06.6000.16386
WMT MuxDeMux Filter,0x00200000,0,0,WMM2FILT.dll,
AVI/WAV File Source,0x00400000,0,2,,6.06.6000.16386
WMT Volume,0x00200000,1,1,WMM2FILT.dll,
Wave Parser,0x00400000,1,1,,6.06.6000.16386
MIDI Parser,0x00400000,1,1,,6.06.6000.16386
Multi-file Parser,0x00400000,1,1,,6.06.6000.16386
File stream renderer,0x00400000,1,1,,6.06.6000.16386
Elecard Stream Parser,0x00400000,1,2,empgdmx.ax,1.00.0077.60823
WMT VIH2 Fix,0x00200000,1,1,WMM2FILT.dll,
AVI Mux,0x00200000,1,0,,6.06.6000.16386
Line 21 Decoder 2,0x00600002,1,1,,6.06.6000.16386
File Source (Async.),0x00400000,0,1,,6.06.6000.16386
File Source (URL),0x00400000,0,1,,6.06.6000.16386
AudioRecorder WAV Dest,0x00200000,0,0,,6.00.6000.16386
AudioRecorder Wave Form,0x00200000,0,0,,6.00.6000.16386
SoundRecorder Null Renderer,0x00200000,0,0,,6.00.6000.16386
Elecard Audio Decoder,0x50000000,1,1,elaudec.ax,1.05.0340.60302
Infinite Pin Tee Filter,0x00200000,1,1,,6.06.6000.16386
WMT Switch Filter,0x00200000,1,1,WMM2FILT.dll,
Enhanced Video Renderer,0x00200000,1,0,evr.dll,5.00.0001.0001
Uncompressed Domain Shot Detection Filter,0x00200000,1,1,WMM2FILT.dll,
BDA MPEG2 Transport Information Filter,0x00200000,2,0,psisrndr.ax,6.06.6000.16386
MPEG Video Decoder,0x40000001,1,1,,6.06.6000.16386
Ligos MPEG Splitter,0x00800000,1,1,Mpeg2Parser.ax,1.02.0000.0079

WDM Streaming Tee/Splitter Devices:
Tee/Sink-to-Sink Converter,0x00200000,1,1,,6.00.6000.16386

WDM Streaming Data Transforms:
Microsoft Kernel DRM Audio Descrambler,0x00200000,1,1,,6.00.6000.16386

Video Compressors:
WMVideo8 Encoder DMO,0x00600800,1,1,,
WMVideo9 Encoder DMO,0x00600800,1,1,,
MSScreen 9 encoder DMO,0x00600800,1,1,,
DV Video Encoder,0x00200000,0,0,,6.06.6000.16386
LogMeIn Video Encoder,0x00400000,1,1,racodec.ax,
MJPEG Compressor,0x00200000,0,0,,6.06.6000.16386
Cinepak Codec by Radius,0x00200000,1,1,,6.06.6000.16386
DivX® 6.5.1 Codec (1 Logical CPU),0x00200000,1,1,,6.06.6000.16386
Intel IYUV codec,0x00200000,1,1,,6.06.6000.16386
Intel IYUV codec,0x00200000,1,1,,6.06.6000.16386
Microsoft RLE,0x00200000,1,1,,6.06.6000.16386
Microsoft Video 1,0x00200000,1,1,,6.06.6000.16386
DivX® 6.5.1 YV12 Decoder,0x00200000,1,1,,6.06.6000.16386

Audio Compressors:
WM Speech Encoder DMO,0x00600800,1,1,,
WMAudio Encoder DMO,0x00600800,1,1,,
IMA ADPCM,0x00200000,1,1,,6.06.6000.16386
PCM,0x00200000,1,1,,6.06.6000.16386
Microsoft ADPCM,0x00200000,1,1,,6.06.6000.16386
GSM 6.10,0x00200000,1,1,,6.06.6000.16386
CCITT A-Law,0x00200000,1,1,,6.06.6000.16386
CCITT u-Law,0x00200000,1,1,,6.06.6000.16386
MPEG Layer-3,0x00200000,1,1,,6.06.6000.16386

Audio Capture Sources:
Microphone (High Definition Aud,0x00200000,0,0,,6.06.6000.16386
Line In (High Definition Audio ,0x00200000,0,0,,6.06.6000.16386

Midi Renderers:
Default MidiOut Device,0x00800000,1,0,,6.06.6000.16386
Microsoft GS Wavetable Synth,0x00200000,1,0,,6.06.6000.16386

WDM Streaming Capture Devices:
HD Audio Line in,0x00200000,1,1,,6.00.6000.16386
HD Audio Microphone 2,0x00200000,1,1,,6.00.6000.16386
HD Audio Microphone,0x00200000,1,1,,6.00.6000.16386

WDM Streaming Rendering Devices:
HD Audio Headphone,0x00200000,1,1,,6.00.6000.16386
HD Audio Speaker,0x00200000,1,1,,6.00.6000.16386
HD Audio SPDIF out,0x00200000,1,1,,6.00.6000.16386

BDA Network Providers:
Microsoft ATSC Network Provider,0x00200000,0,1,MSDvbNP.ax,6.06.6000.16386
Microsoft DVBC Network Provider,0x00200000,0,1,MSDvbNP.ax,6.06.6000.16386
Microsoft DVBS Network Provider,0x00200000,0,1,MSDvbNP.ax,6.06.6000.16386
Microsoft DVBT Network Provider,0x00200000,0,1,MSDvbNP.ax,6.06.6000.16386
Microsoft Network Provider,0x00200000,0,1,MSNP.ax,6.06.6000.16386

Video Capture Sources:
Creative WebCam Instant (VFW),0x00200000,0,0,,6.06.6000.16386

Multi-Instance Capable VBI Codecs:
VBI Codec,0x00600000,1,4,VBICodec.ax,6.06.6000.16386

BDA Transport Information Renderers:
BDA MPEG2 Transport Information Filter,0x00600000,2,0,psisrndr.ax,6.06.6000.16386
MPEG-2 Sections and Tables,0x00600000,1,0,Mpeg2Data.ax,6.06.6000.16386

BDA CP/CA Filters:
Decrypt/Tag,0x00600000,1,0,EncDec.dll,6.06.6000.16386
Encrypt/Tag,0x00200000,0,0,EncDec.dll,6.06.6000.16386
XDS Codec,0x00200000,0,0,EncDec.dll,6.06.6000.16386

WDM Streaming Communication Transforms:
Tee/Sink-to-Sink Converter,0x00200000,1,1,,6.00.6000.16386

Audio Renderers:
Speakers (High Definition Audio,0x00200000,1,0,,6.06.6000.16386
Default DirectSound Device,0x00800000,1,0,,6.06.6000.16386
Default WaveOut Device,0x00200000,1,0,,6.06.6000.16386
Digital Output Device (SPDIF) (,0x00200000,1,0,,6.06.6000.16386
DirectSound: Digital Output Device (SPDIF) (High Definition Audio Device),0x00200000,1,0,,6.06.6000.16386
DirectSound: Headphones (High Definition Audio Device),0x00200000,1,0,,6.06.6000.16386
DirectSound: Speakers (High Definition Audio Device),0x00200000,1,0,,6.06.6000.16386
Headphones (High Definition Aud,0x00200000,1,0,,6.06.6000.16386

---

### Post by C4U53 on 2007-07-26
I was reading another post and it also reminded me.. I did a check sum on all disk I made. On the 2 that are coasters I tried to verify it at the boot up menu and it reported bad files also I tried to boot in "safe mode" from the live cd. I didn't try and verify the dvd as the text installer eventually worked.

---

### Post by C4U53 on 2007-07-26
This isn't solved I've doing tons of reading (though most of the reading has been on this site)  and havn't even come accross something to try and re-install a different kernel - I was kind of expecting an answer like that but perhaps I posted way to late.. or.. early ( 5 am for me ) and it just got lost before anybody came on... Anyway.. anyhelp is truely appreciated.. I've heard alot of things about your OS and though I am a newb I messed around with linux alot back in the day. Even purchased one of the first commercial mandrakes but I never got to far. Though I allways preferred linux windows has stole the market or tried. Linux is coming back again and I've been alot of great open source programs that solved my conflicts.. one being the different window emulators that have been developed over the years.. unfournately alot of the early ones didn't work so well =p..

Anyway. I'm glad most of you stuck with linux and help bring it is where it is now. if everyone was like me and just "didn't have time" for it then It definetly wouldn't be where it is today. 

again.. any help appreciated

---

