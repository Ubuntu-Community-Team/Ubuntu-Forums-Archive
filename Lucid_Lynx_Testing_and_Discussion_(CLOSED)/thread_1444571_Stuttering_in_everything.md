---
title: "Stuttering in everything"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Revord on 2010-04-01
I recently downloaded the new Wubi and ran it in XP Pro. Everything worked fine, in fact, it took less than an hour and a half to download and install the entire Lucid distro. 

What Im wondering is this: I have a gig and a half of ram. Im using an Athlon x64 chip, so wubi detected that, and installed the 64 bit version of Lucid. So far, I like it all, however, the stuttering affects everything, from browsing to typing, videos, and video games. Am I having a problem with not enough ram? Or is my problem related to something else? I have never used a 64bit os before, so this is new for me.

---

### Post by metallica1788 on 2010-04-02
i dont think that is has anything to do with your system,
it maybe a bug in lucid. Start the program system monitor and look at the cpu usage, it could be a process that takes alot cpu load because of a bug.

In the past i ran ubuntu on an old P3 with 256MB ram and it ran pretty good,so specs are mostly not the problemen with ubuntu.

---

### Post by NightwishFan on 2010-04-02
If you are not adverse to using the terminal (Applications -> Accessories -> Terminal) then please run this command and post the output here using the CODE "#" tags.
```
top
```

---

### Post by clhsharky on 2010-04-02
HI Revord


> the stuttering affects everything

I can only guess with out more info. -hardware, drivers-

Sharky

---

### Post by Revord on 2010-04-02
Can do. I will edit this post when I get my comp restarted in Ubuntu and run the code.

Edit: Ok heres my top output. It appears I dont have enough ram to run lucid in 64 bit mode

```
top - 07:27:55 up 8 min,  2 users,  load average: 0.00, 0.17, 0.14
Tasks: 158 total,   1 running, 157 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.3%us,  0.2%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.5%hi,  0.0%si,  0.0%st
Mem:   1539760k total,  1397708k used,   142052k free,   355168k buffers
Swap:   261112k total,        0k used,   261112k free,   504780k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1025 root      20   0  121m  26m 8708 S    0  1.8   0:25.01 Xorg               
 1608 revord    20   0  209m  15m  11m S    0  1.0   0:00.77 gnome-terminal     
 1627 revord    20   0 19216 1412 1032 R    0  0.1   0:00.35 top                
    1 root      20   0 23688 1876 1248 S    0  0.1   0:00.47 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      20   0     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      20   0     0    0    0 S    0  0.0   0:00.08 events/1           
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset             
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper            
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 netns              
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr      
```

---

### Post by NightwishFan on 2010-04-02
That output looks fine. You aren't even touching the swap. It does not seem to be resource management. Any more specifics you noticed?

---

### Post by Revord on 2010-04-02
Well, if its not my ram, then honestly I am at a loss. XP runs more than fine on this system, so the only other thing I can do to help find the problem is give the dxdiag report. I dont know how to bring up the hardware/driver specifics on linux. If other info is needed, I can gladly provide it. I dont mind using the terminal, but I dont know any of the commands to do so.

DXDIAG REPORT
```
------------------
System Information
------------------
Time of this report: 4/2/2010, 11:06:53
       Machine name: GAME-1
   Operating System: Windows XP Professional (5.1, Build 2600) Service Pack 3 (2600.xpsp_sp3_gdr.091208-2036)
           Language: English (Regional Setting: English)
System Manufacturer: System manufacturer
       System Model: System Product Name
               BIOS: BIOS Date: 06/20/06 15:18:48 Ver: 08.00.12
          Processor: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+,  MMX,  3DNow (2 CPUs), ~2.2GHz
             Memory: 1536MB RAM
          Page File: 823MB used, 2607MB available
        Windows Dir: C:\WINDOWS
    DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
     DxDiag Version: 5.03.2600.5512 32bit Unicode

------------
DxDiag Notes
------------
  DirectX Files Tab: No problems found.
      Display Tab 1: The file ati2dvag.dll is not digitally signed, which means that it has not been tested by Microsoft's Windows Hardware Quality Labs (WHQL).  You may be able to get a WHQL logo'd driver from the hardware manufacturer.
        Sound Tab 1: The file cmudax3.sys is not digitally signed, which means that it has not been tested by Microsoft's Windows Hardware Quality Labs (WHQL).  You may be able to get a WHQL logo'd driver from the hardware manufacturer.
          Music Tab: No problems found.
          Input Tab: No problems found.
        Network Tab: No problems found.

--------------------
DirectX Debug Levels
--------------------
Direct3D:    0/4 (n/a)
DirectDraw:  0/4 (retail)
DirectInput: 0/5 (n/a)
DirectMusic: 0/5 (n/a)
DirectPlay:  0/9 (retail)
DirectSound: 0/5 (retail)
DirectShow:  0/6 (retail)

---------------
Display Devices
---------------
        Card name: Radeon X1650 Series (Omega 3.8.442)   
     Manufacturer: ATI Technologies Inc. (Omega 3.8.442)
        Chip type: ATI Radeon Graphics Processor AGP (0x7293)
         DAC type: Internal DAC(400MHz)
       Device Key: Enum\PCI\VEN_1002&DEV_7293&SUBSYS_210317AF&REV_9A
   Display Memory: 512.0 MB
     Current Mode: 1024 x 768 (32 bit) (60Hz)
          Monitor: Plug and Play Monitor
  Monitor Max Res: 1600,1200
      Driver Name: ati2dvag.dll
   Driver Version: 6.14.0010.6755 (English)
      DDI Version: 9 (or higher)
Driver Attributes: Final Retail
 Driver Date/Size: 12/4/2007 20:04:08, 269312 bytes
      WHQL Logo'd: No
  WHQL Date Stamp: None
              VDD: n/a
         Mini VDD: ati2mtag.sys
    Mini VDD Date: 12/4/2007 22:26:40, 2782208 bytes
Device Identifier: {D7B71EE2-31D3-11CF-7C6E-09013BC2CB35}
        Vendor ID: 0x1002
        Device ID: 0x7293
        SubSys ID: 0x210317AF
      Revision ID: 0x009A
      Revision ID: 0x009A
      Video Accel: ModeMPEG2_C ModeMPEG2_D ModeWMV8_B ModeWMV8_A ModeWMV9_B ModeWMV9_A 
 Deinterlace Caps: {6E8329FF-B642-418B-BCF0-BCB6591E255F}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,1) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                   {3C5323C1-6FB7-44F5-9081-056BF2EE449D}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,2) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {552C0DAD-CCBC-420B-83C8-74943CF9F1A6}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,2) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {6E8329FF-B642-418B-BCF0-BCB6591E255F}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,1) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
         Registry: OK
     DDraw Status: Enabled
       D3D Status: Enabled
       AGP Status: Enabled
DDraw Test Result: Not run
 D3D7 Test Result: Not run
 D3D8 Test Result: Not run
 D3D9 Test Result: Not run

-------------
Sound Devices
-------------
            Description: Turtle Beach Riviera Wave
 Default Sound Playback: Yes
 Default Voice Playback: Yes
            Hardware ID: PCI\VEN_13F6&DEV_0111&SUBSYS_011113F6&REV_10
        Manufacturer ID: 1
             Product ID: 100
                   Type: WDM
            Driver Name: cmudax3.sys
         Driver Version: 5.12.0001.0008 (English)
      Driver Attributes: Final Debug
            WHQL Logo'd: No
          Date and Size: 6/28/2007 11:43:40, 1404288 bytes
            Other Files: 
        Driver Provider: Turtle Beach, Inc.
         HW Accel Level: Full
              Cap Flags: 0xF5F
    Min/Max Sample Rate: 100, 96000
Static/Strm HW Mix Bufs: 66, 64
 Static/Strm HW 3D Bufs: 65, 63
              HW Memory: 0
       Voice Management: No
 EAX(tm) 2.0 Listen/Src: Yes, Yes
   I3DL2(tm) Listen/Src: Yes, Yes
Sensaura(tm) ZoomFX(tm): No
               Registry: OK
      Sound Test Result: Not run

---------------------
Sound Capture Devices
---------------------
            Description: Turtle Beach Riviera Wave
  Default Sound Capture: Yes
  Default Voice Capture: Yes
            Driver Name: cmudax3.sys
         Driver Version: 5.12.0001.0008 (English)
      Driver Attributes: Final Debug
          Date and Size: 6/28/2007 11:43:40, 1404288 bytes
              Cap Flags: 0x41
           Format Flags: 0xCC0

-----------
DirectMusic
-----------
        DLS Path: C:\WINDOWS\SYSTEM32\drivers\GM.DLS
     DLS Version: 1.00.0016.0002
    Acceleration: n/a
           Ports: Microsoft Synthesizer, Software (Not Kernel Mode), Output, DLS, Internal, Default Port
                  Turtle Beach Riviera Wave, Software (Kernel Mode), Output, DLS, Internal
                  Microsoft MIDI Mapper [Emulated], Hardware (Not Kernel Mode), Output, No DLS, Internal
                  Microsoft GS Wavetable SW Synth [Emulated], Hardware (Not Kernel Mode), Output, No DLS, Internal
        Registry: OK
     Test Result: Not run

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

      Device Name: USB-compliant keyboard
         Attached: 1
    Controller ID: 0x0
Vendor/Product ID: 0x0518, 0x0001
        FF Driver: n/a

      Device Name: USB-compliant keyboard
         Attached: 1
    Controller ID: 0x0
Vendor/Product ID: 0x0518, 0x0001
        FF Driver: n/a

Poll w/ Interrupt: No
         Registry: OK

-----------
USB Devices
-----------
+ USB Root Hub
| Vendor/Product ID: 0x1106, 0x3038
| Matching Device ID: usb\root_hub
| Service: usbhub
| Driver: usbhub.sys, 4/14/2008 00:15:38, 59520 bytes
| Driver: usbd.sys, 8/4/2004 05:00:00, 4736 bytes
| 
+-+ Logitech USB MX320 Laser Mouse
| | Vendor/Product ID: 0x046D, 0xC043
| | Location: USB-PS/2 Optical Mouse
| | Matching Device ID: usb\vid_046d&pid_c043
| | Lower Filters: LUsbFilt
| | Service: HidUsb
| | Driver: hidusb.sys, 4/14/2008 01:15:28, 10368 bytes
| | Driver: hidclass.sys, 4/14/2008 01:15:28, 36864 bytes
| | Driver: hidparse.sys, 4/14/2008 01:15:24, 24960 bytes
| | Driver: hid.dll, 4/14/2008 05:41:56, 20992 bytes
| | Driver: LUsbFilt.sys, 11/10/2009 04:55:32, 28560 bytes
| | Driver: LkmdfCoInst.dll, 11/10/2009 04:55:00, 1581072 bytes
| | 
| +-+ Logitech HID-compliant MX320 Laser Mouse
| | | Vendor/Product ID: 0x046D, 0xC043
| | | Matching Device ID: hid\vid_046d&pid_c043
| | | Upper Filters: LMouFilt
| | | Lower Filters: LHidFilt
| | | Service: mouhid
| | | Driver: mouhid.sys, 8/17/2001 14:48:00, 12160 bytes
| | | Driver: mouclass.sys, 4/14/2008 01:09:48, 23040 bytes
| | | Driver: LHidFilt.Sys, 11/10/2009 04:54:52, 35984 bytes
| | | Driver: LMouFilt.Sys, 11/10/2009 04:55:08, 37392 bytes
| | | Driver: LkmdfCoInst.dll, 11/10/2009 04:55:00, 1581072 bytes
| | | Driver: LMouFiltCoInst.dll, 11/10/2009 04:55:16, 52240 bytes

----------------
Gameport Devices
----------------
+ VIA Standard PCI to ISA Bridge
| Location: PCI bus 0, device 17, function 0
| Matching Device ID: pci\ven_1106&dev_3287
| Service: isapnp
| Driver: isapnp.sys, 4/14/2008 00:06:42, 37248 bytes
| 
+-+ Standard Game Port
| | Matching Device ID: *pnpb02f
| | Service: gameenum
| | Driver: gameenum.sys, 4/14/2008 00:15:30, 10624 bytes

------------
PS/2 Devices
------------
+ USB KeyMaestro Multimedia Keyboard(Windows XP)
| Vendor/Product ID: 0x0518, 0x0001
| Matching Device ID: hid\vid_0518&pid_0001&mi_00
| Service: kbdhid
| Driver: kbdhid.sys, 4/14/2008 00:09:50, 14592 bytes
| Driver: kbdclass.sys, 4/14/2008 00:09:48, 24576 bytes
| Driver: SetupKey.exe, 12/4/2003 13:47:10, 6060 bytes
| Driver: Coinstal.dll, 4/6/2005 10:47:42, 4504 bytes
| 
+ Terminal Server Keyboard Driver
| Matching Device ID: root\rdp_kbd
| Upper Filters: kbdclass
| Service: TermDD
| Driver: termdd.sys, 4/14/2008 05:43:22, 40840 bytes
| Driver: kbdclass.sys, 4/14/2008 00:09:48, 24576 bytes
| 
+ HID-compliant mouse
| Vendor/Product ID: 0x0518, 0x0001
| Matching Device ID: hid_device_system_mouse
| Service: mouhid
| Driver: mouclass.sys, 4/14/2008 01:09:48, 23040 bytes
| Driver: mouhid.sys, 8/17/2001 14:48:00, 12160 bytes
| 
+ Terminal Server Mouse Driver
| Matching Device ID: root\rdp_mou
| Upper Filters: mouclass
| Service: TermDD
| Driver: termdd.sys, 4/14/2008 05:43:22, 40840 bytes
| Driver: mouclass.sys, 4/14/2008 01:09:48, 23040 bytes

----------------------------
DirectPlay Service Providers
----------------------------
DirectPlay8 Modem Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.5512)
DirectPlay8 Serial Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.5512)
DirectPlay8 IPX Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.5512)
DirectPlay8 TCP/IP Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.5512)
Internet TCP/IP Connection For DirectPlay - Registry: OK, File: dpwsockx.dll (5.03.2600.5512)
IPX Connection For DirectPlay - Registry: OK, File: dpwsockx.dll (5.03.2600.5512)
Modem Connection For DirectPlay - Registry: OK, File: dpmodemx.dll (5.03.2600.5512)
Serial Connection For DirectPlay - Registry: OK, File: dpmodemx.dll (5.03.2600.5512)

DirectPlay Voice Wizard Tests: Full Duplex: Not run, Half Duplex: Not run, Mic: Not run
DirectPlay Test Result: Not run
Registry: OK

-------------------
DirectPlay Adapters
-------------------
DirectPlay8 Modem Service Provider: Standard Modem
DirectPlay8 TCP/IP Service Provider: Local Area Connection - IPv4 - 

-----------------------
DirectPlay Voice Codecs
-----------------------
Voxware VR12 1.4kbit/s
Voxware SC06 6.4kbit/s
Voxware SC03 3.2kbit/s
MS-PCM 64 kbit/s
MS-ADPCM 32.8 kbit/s
Microsoft GSM 6.10 13 kbit/s
TrueSpeech(TM) 8.6 kbit/s

-------------------------
DirectPlay Lobbyable Apps
-------------------------

------------------------
Disk & DVD/CD-ROM Drives
------------------------
      Drive: C:
 Free Space: 1.1 GB
Total Space: 20.9 GB
File System: NTFS
      Model: n/a

      Drive: D:
 Free Space: 31.0 GB
Total Space: 169.9 GB
File System: NTFS
      Model: n/a

      Drive: K:
 Free Space: 7.4 GB
Total Space: 58.6 GB
File System: NTFS
      Model: IC35L060AVV207-0

      Drive: E:
      Model: Memorex DVD16+/-DL4RWlD2
     Driver: c:\windows\system32\drivers\cdrom.sys, 5.01.2600.5593 (English), 5/2/2008 03:49:39, 62976 bytes

      Drive: F:
      Model: CD-ROM Drive
     Driver: c:\windows\system32\drivers\cdrom.sys, 5.01.2600.5593 (English), 5/2/2008 03:49:39, 62976 bytes

      Drive: G:
      Model: ULIB MZ01UNO SCSI CdRom Device
     Driver: c:\windows\system32\drivers\cdrom.sys, 5.01.2600.5593 (English), 5/2/2008 03:49:39, 62976 bytes

--------------
System Devices
--------------
     Name: Turtle Beach Riviera Wave
Device ID: PCI\VEN_13F6&DEV_0111&SUBSYS_011113F6&REV_10\4&176304AC&0&6099
   Driver: C:\WINDOWS\system32\drivers\drmk.sys, 5.01.2600.5512 (English), 4/14/2008 00:15:16, 60160 bytes
   Driver: C:\WINDOWS\system32\drivers\portcls.sys, 5.01.2600.5512 (English), 4/14/2008 00:49:42, 146048 bytes
   Driver: C:\WINDOWS\system32\drivers\stream.sys, 5.03.0001.0904 (English), 7/9/2004 04:27:28, 48512 bytes
   Driver: C:\WINDOWS\system32\wdmaud.drv, 5.01.2600.5512 (English), 4/14/2008 05:42:46, 23552 bytes
   Driver: C:\WINDOWS\system32\ksuser.dll, 5.03.0000.0900 (English), 12/12/2002 00:14:32, 4096 bytes
   Driver: C:\WINDOWS\system32\drivers\cmudax3.sys, 5.12.0001.0008 (English), 6/28/2007 11:43:40, 1404288 bytes
   Driver: C:\WINDOWS\system32\cmudax3.DLL, 5.12.0001.0120 (Chinese), 2/26/2007 20:30:32, 36864 bytes

     Name: VIA CPU to AGP Controller
Device ID: PCI\VEN_1106&DEV_B188&SUBSYS_00000000&REV_00\3&267A616A&0&08
   Driver: C:\WINDOWS\system32\DRIVERS\GAGP30KX.SYS, 5.01.2600.5512 (English), 4/14/2008 00:06:42, 46464 bytes

     Name: VIA Standard Host Bridge
Device ID: PCI\VEN_1106&DEV_7282&SUBSYS_00000000&REV_00\3&267A616A&0&07
   Driver: n/a

     Name: VIA Standard Host Bridge
Device ID: PCI\VEN_1106&DEV_4282&SUBSYS_00000000&REV_00\3&267A616A&0&04
   Driver: n/a

     Name: VIA Standard PCI to ISA Bridge
Device ID: PCI\VEN_1106&DEV_3287&SUBSYS_00000000&REV_00\3&267A616A&0&88
   Driver: C:\WINDOWS\system32\DRIVERS\isapnp.sys, 5.01.2600.5512 (English), 4/14/2008 00:06:42, 37248 bytes

     Name: VIA Standard Host Bridge
Device ID: PCI\VEN_1106&DEV_3282&SUBSYS_00000000&REV_00\3&267A616A&0&03
   Driver: n/a

     Name: VIA USB Enhanced Host Controller
Device ID: PCI\VEN_1106&DEV_3104&SUBSYS_31041106&REV_90\3&267A616A&0&84
   Driver: C:\WINDOWS\system32\drivers\usbehci.sys, 5.01.2600.5512 (English), 4/14/2008 00:15:36, 30208 bytes
   Driver: C:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.5512 (English), 4/14/2008 00:15:38, 143872 bytes
   Driver: C:\WINDOWS\system32\usbui.dll, 5.01.2600.5512 (English), 4/14/2008 05:42:10, 74240 bytes
   Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.5512 (English), 4/14/2008 00:15:38, 59520 bytes
   Driver: C:\WINDOWS\system32\hccoin.dll, 5.01.2600.5512 (English), 4/14/2008 05:41:56, 7168 bytes

     Name: VIA Rhine II Fast Ethernet Adapter
Device ID: PCI\VEN_1106&DEV_3065&SUBSYS_80ED1043&REV_7C\3&267A616A&0&90
   Driver: C:\WINDOWS\system32\DRIVERS\fetnd5bv.sys, 3.41.0000.0426 (English), 12/15/2004 22:36:30, 42496 bytes
   Driver: C:\WINDOWS\system32\vuins32.dll, 1.04.0000.0009 (English), 9/17/2004 02:37:42, 61440 bytes

     Name: VIA Rev 5 or later USB Universal Host Controller
Device ID: PCI\VEN_1106&DEV_3038&SUBSYS_30381106&REV_90\3&267A616A&0&83
   Driver: C:\WINDOWS\system32\drivers\usbuhci.sys, 5.01.2600.5512 (English), 4/14/2008 00:15:36, 20608 bytes
   Driver: C:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.5512 (English), 4/14/2008 00:15:38, 143872 bytes
   Driver: C:\WINDOWS\system32\usbui.dll, 5.01.2600.5512 (English), 4/14/2008 05:42:10, 74240 bytes
   Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.5512 (English), 4/14/2008 00:15:38, 59520 bytes

     Name: VIA Rev 5 or later USB Universal Host Controller
Device ID: PCI\VEN_1106&DEV_3038&SUBSYS_30381106&REV_90\3&267A616A&0&82
   Driver: C:\WINDOWS\system32\drivers\usbuhci.sys, 5.01.2600.5512 (English), 4/14/2008 00:15:36, 20608 bytes
   Driver: C:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.5512 (English), 4/14/2008 00:15:38, 143872 bytes
   Driver: C:\WINDOWS\system32\usbui.dll, 5.01.2600.5512 (English), 4/14/2008 05:42:10, 74240 bytes
   Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.5512 (English), 4/14/2008 00:15:38, 59520 bytes

     Name: VIA Rev 5 or later USB Universal Host Controller
Device ID: PCI\VEN_1106&DEV_3038&SUBSYS_30381106&REV_90\3&267A616A&0&81
   Driver: C:\WINDOWS\system32\drivers\usbuhci.sys, 5.01.2600.5512 (English), 4/14/2008 00:15:36, 20608 bytes
   Driver: C:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.5512 (English), 4/14/2008 00:15:38, 143872 bytes
   Driver: C:\WINDOWS\system32\usbui.dll, 5.01.2600.5512 (English), 4/14/2008 05:42:10, 74240 bytes
   Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.5512 (English), 4/14/2008 00:15:38, 59520 bytes

     Name: VIA Rev 5 or later USB Universal Host Controller
Device ID: PCI\VEN_1106&DEV_3038&SUBSYS_30381106&REV_90\3&267A616A&0&80
   Driver: C:\WINDOWS\system32\drivers\usbuhci.sys, 5.01.2600.5512 (English), 4/14/2008 00:15:36, 20608 bytes
   Driver: C:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.5512 (English), 4/14/2008 00:15:38, 143872 bytes
   Driver: C:\WINDOWS\system32\usbui.dll, 5.01.2600.5512 (English), 4/14/2008 05:42:10, 74240 bytes
   Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.5512 (English), 4/14/2008 00:15:38, 59520 bytes

     Name: VIA Ultra VLINK Controller
Device ID: PCI\VEN_1106&DEV_287E&SUBSYS_00000000&REV_00\3&267A616A&0&8F
   Driver: n/a

     Name: VIA Standard PCIE Root Port
Device ID: PCI\VEN_1106&DEV_287D&SUBSYS_00000000&REV_00\4&237FA511&0&0198
   Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.5512 (English), 4/14/2008 00:06:46, 68224 bytes

     Name: VIA Standard PCIE Root Port
Device ID: PCI\VEN_1106&DEV_287C&SUBSYS_00000000&REV_00\4&237FA511&0&0098
   Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.5512 (English), 4/14/2008 00:06:46, 68224 bytes

     Name: VIA Standard PCI to PCIE Bridge
Device ID: PCI\VEN_1106&DEV_287B&SUBSYS_00000000&REV_00\3&267A616A&0&98
   Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.5512 (English), 4/14/2008 00:06:46, 68224 bytes

     Name: VIA Standard PCI to PCI Bridge
Device ID: PCI\VEN_1106&DEV_287A&SUBSYS_00000000&REV_00\3&267A616A&0&99
   Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.5512 (English), 4/14/2008 00:06:46, 68224 bytes

     Name: VIA Standard Host Bridge
Device ID: PCI\VEN_1106&DEV_2282&SUBSYS_00000000&REV_00\3&267A616A&0&02
   Driver: n/a

     Name: VIA Standard Host Bridge
Device ID: PCI\VEN_1106&DEV_1282&SUBSYS_00000000&REV_00\3&267A616A&0&01
   Driver: n/a

     Name: VIA Bus Master IDE Controller
Device ID: PCI\VEN_1106&DEV_0571&SUBSYS_05711106&REV_07\3&267A616A&0&78
   Driver: C:\WINDOWS\system32\DRIVERS\viaide.sys, 1.00.0001.0001 (English), 4/14/2008 00:10:32, 5376 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\pciidex.sys, 5.01.2600.5512 (English), 4/14/2008 00:10:30, 24960 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\atapi.sys, 5.01.2600.5512 (English), 4/14/2008 00:10:32, 96512 bytes

     Name: VIA Standard Host Bridge
Device ID: PCI\VEN_1106&DEV_0282&SUBSYS_00000000&REV_00\3&267A616A&0&00
   Driver: n/a

     Name: PCI standard host CPU bridge
Device ID: PCI\VEN_1022&DEV_1103&SUBSYS_00000000&REV_00\3&267A616A&0&C3
   Driver: n/a

     Name: PCI standard host CPU bridge
Device ID: PCI\VEN_1022&DEV_1102&SUBSYS_00000000&REV_00\3&267A616A&0&C2
   Driver: n/a

     Name: PCI standard host CPU bridge
Device ID: PCI\VEN_1022&DEV_1101&SUBSYS_00000000&REV_00\3&267A616A&0&C1
   Driver: n/a

     Name: PCI standard host CPU bridge
Device ID: PCI\VEN_1022&DEV_1100&SUBSYS_00000000&REV_00\3&267A616A&0&C0
   Driver: n/a

     Name: Radeon X1650 Series Secondary (Omega 3.8.442)   
Device ID: PCI\VEN_1002&DEV_72B3&SUBSYS_210217AF&REV_9A\4&3600494A&0&0108
   Driver: C:\WINDOWS\system32\DRIVERS\ati2mtag.sys, 6.14.0010.6755 (English), 12/4/2007 22:26:40, 2782208 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ati2erec.dll, 1.00.0000.0012 (English), 12/4/2007 19:16:37, 49152 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ativvpxx.vp, 9/8/2007 20:37:03, 47360 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ativckxx.vp, 5/30/2007 10:43:05, 2096 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ativcaxx.vp, 4/18/2007 06:19:24, 929 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ativcaxx.cpa, 4/18/2007 06:19:24, 1311202 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ativdkxx.vp, 4/18/2007 05:19:50, 2096 bytes
   Driver: C:\WINDOWS\system32\ati2dvag.dll, 6.14.0010.6755 (English), 12/4/2007 20:04:08, 269312 bytes
   Driver: C:\WINDOWS\system32\ati2cqag.dll, 6.14.0010.0359 (English), 12/4/2007 19:11:18, 499712 bytes
   Driver: C:\WINDOWS\system32\Ati2mdxx.exe, 6.14.0010.2495 (English), 12/4/2007 19:55:42, 26112 bytes
   Driver: C:\WINDOWS\system32\ati3duag.dll, 6.14.0010.0510 (English), 6/26/2007 18:41:08, 2940992 bytes
   Driver: C:\WINDOWS\system32\ativvaxx.dll, 6.14.0010.0174 (English), 12/4/2007 19:33:47, 1640192 bytes
   Driver: C:\WINDOWS\system32\atiicdxx.dat, 11/6/2007 07:19:00, 158080 bytes
   Driver: C:\WINDOWS\system32\ativvaxx.dat, 12/4/2007 19:33:27, 3107788 bytes
   Driver: C:\WINDOWS\system32\ativva5x.dat, 12/4/2007 19:33:27, 3107788 bytes
   Driver: C:\WINDOWS\system32\ativva6x.dat, 12/4/2007 19:33:27, 887724 bytes
   Driver: C:\WINDOWS\system32\ATIDDC.DLL, 6.14.0010.0008 (English), 12/4/2007 19:53:09, 53248 bytes
   Driver: C:\WINDOWS\system32\atitvo32.dll, 6.14.0010.4200 (English), 12/4/2007 19:17:21, 17408 bytes
   Driver: C:\WINDOWS\system32\ativcoxx.dll, 6.13.0010.0005 (English), 11/9/2001 09:01:04, 24064 bytes
   Driver: C:\WINDOWS\system32\ati2evxx.exe, 6.14.0010.4183 (English), 12/4/2007 19:53:58, 495616 bytes
   Driver: C:\WINDOWS\system32\ati2evxx.dll, 6.14.0010.4176 (English), 12/4/2007 19:55:20, 122880 bytes
   Driver: C:\WINDOWS\system32\atipdlxx.dll, 6.14.0010.2526 (English), 12/4/2007 19:56:02, 147456 bytes
   Driver: C:\WINDOWS\system32\Oemdspif.dll, 6.15.0002.0000 (English), 12/4/2007 19:55:50, 122880 bytes
   Driver: C:\WINDOWS\system32\ati2edxx.dll, 6.14.0010.2513 (English), 12/4/2007 19:55:34, 43520 bytes
   Driver: C:\WINDOWS\system32\atikvmag.dll, 6.14.0010.0069 (English), 12/4/2007 19:19:14, 385024 bytes
   Driver: C:\WINDOWS\system32\atifglpf.xml, 8/31/2007 07:20:49, 7167 bytes
   Driver: C:\WINDOWS\system32\ATIDEMGX.dll, 2.00.2894.39756 (English), 12/4/2007 20:05:14, 368640 bytes
   Driver: C:\WINDOWS\system32\atfchtxx.hlx, 2/21/2006 18:05:00, 24589 bytes
   Driver: C:\WINDOWS\system32\atfchsxx.hlx, 2/21/2006 18:05:00, 26864 bytes
   Driver: C:\WINDOWS\system32\atfaraxx.hlx, 2/21/2006 18:05:00, 24652 bytes
   Driver: C:\WINDOWS\system32\atfcsyxx.hlx, 2/21/2006 18:05:00, 24569 bytes
   Driver: C:\WINDOWS\system32\atfdanxx.hlx, 2/21/2006 18:05:00, 24065 bytes
   Driver: C:\WINDOWS\system32\atfdeuxx.hlx, 2/21/2006 18:05:00, 24557 bytes
   Driver: C:\WINDOWS\system32\atfellxx.hlx, 2/21/2006 18:05:00, 25224 bytes
   Driver: C:\WINDOWS\system32\atfenuxx.hlx, 2/21/2006 18:05:00, 23224 bytes
   Driver: C:\WINDOWS\system32\atfespxx.hlx, 2/21/2006 18:05:00, 24382 bytes
   Driver: C:\WINDOWS\system32\atffinxx.hlx, 2/21/2006 18:05:00, 24260 bytes
   Driver: C:\WINDOWS\system32\atffraxx.hlx, 2/21/2006 18:05:00, 24640 bytes
   Driver: C:\WINDOWS\system32\atfhebxx.hlx, 2/21/2006 18:05:00, 27697 bytes
   Driver: C:\WINDOWS\system32\atfhunxx.hlx, 2/21/2006 18:05:00, 24892 bytes
   Driver: C:\WINDOWS\system32\atfitaxx.hlx, 2/21/2006 18:05:00, 24506 bytes
   Driver: C:\WINDOWS\system32\atfjpnxx.hlx, 2/21/2006 18:05:00, 49807 bytes
   Driver: C:\WINDOWS\system32\atfkorxx.hlx, 2/21/2006 18:05:00, 66161 bytes
   Driver: C:\WINDOWS\system32\atfnldxx.hlx, 2/21/2006 18:05:00, 24186 bytes
   Driver: C:\WINDOWS\system32\atfnorxx.hlx, 2/21/2006 18:05:00, 24229 bytes
   Driver: C:\WINDOWS\system32\atfplkxx.hlx, 2/21/2006 18:05:00, 26138 bytes
   Driver: C:\WINDOWS\system32\atfptbxx.hlx, 2/21/2006 18:05:00, 24712 bytes
   Driver: C:\WINDOWS\system32\atfrusxx.hlx, 2/21/2006 18:05:00, 25327 bytes
   Driver: C:\WINDOWS\system32\atfsvexx.hlx, 2/21/2006 18:05:00, 23980 bytes
   Driver: C:\WINDOWS\system32\atfthaxx.hlx, 2/21/2006 18:05:00, 24873 bytes
   Driver: C:\WINDOWS\system32\atftrkxx.hlx, 2/21/2006 18:05:00, 48174 bytes
   Driver: C:\WINDOWS\system32\atiicdxx.dll, 6.14.0010.3045 (English), 2/22/2006 01:14:58, 380928 bytes
   Driver: C:\WINDOWS\system32\atiicdxx.sys, 6.13.0010.1005 (English), 2/22/2006 01:13:54, 6144 bytes
   Driver: C:\WINDOWS\system32\atiicdxx.vxd, 4/14/2003 23:07:14, 7849 bytes
   Driver: C:\WINDOWS\system32\Atiiprxx.exe, 2/21/2006 18:05:00, 36864 bytes
   Driver: C:\WINDOWS\system32\atipdsxx.dll, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 274432 bytes
   Driver: C:\WINDOWS\system32\atiphexx.exe, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 61440 bytes
   Driver: C:\WINDOWS\system32\atippaxx.dll, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 114688 bytes
   Driver: C:\WINDOWS\system32\atiprbxx.exe, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 139264 bytes
   Driver: C:\WINDOWS\system32\atiptaxx.exe, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 344064 bytes
   Driver: C:\WINDOWS\system32\atipuixx.dll, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 2060288 bytes
   Driver: C:\WINDOWS\system32\atmaraxx.cnt, 2/21/2006 18:05:00, 2220 bytes
   Driver: C:\WINDOWS\system32\atmaraxx.hlx, 2/21/2006 18:05:00, 155364 bytes
   Driver: C:\WINDOWS\system32\atmchsxx.cnt, 2/21/2006 18:05:00, 2047 bytes
   Driver: C:\WINDOWS\system32\atmchsxx.hlx, 2/21/2006 18:05:00, 189356 bytes
   Driver: C:\WINDOWS\system32\atmchtxx.cnt, 2/21/2006 18:05:00, 2070 bytes
   Driver: C:\WINDOWS\system32\atmchtxx.hlx, 2/21/2006 18:05:00, 145421 bytes
   Driver: C:\WINDOWS\system32\atmcsyxx.cnt, 2/21/2006 18:05:00, 2615 bytes
   Driver: C:\WINDOWS\system32\atmcsyxx.hlx, 2/21/2006 18:05:00, 145641 bytes
   Driver: C:\WINDOWS\system32\atmdanxx.cnt, 2/21/2006 18:05:00, 2704 bytes
   Driver: C:\WINDOWS\system32\atmdanxx.hlx, 2/21/2006 18:05:00, 142359 bytes
   Driver: C:\WINDOWS\system32\atmdeuxx.cnt, 2/21/2006 18:05:00, 2849 bytes
   Driver: C:\WINDOWS\system32\atmdeuxx.hlx, 2/21/2006 18:05:00, 147444 bytes
   Driver: C:\WINDOWS\system32\atmellxx.cnt, 2/21/2006 18:05:00, 2759 bytes
   Driver: C:\WINDOWS\system32\atmellxx.hlx, 2/21/2006 18:05:00, 148083 bytes
   Driver: C:\WINDOWS\system32\atmenuxx.cnt, 2/21/2006 18:05:00, 2610 bytes
   Driver: C:\WINDOWS\system32\atmenuxx.hlx, 2/21/2006 18:05:00, 136272 bytes
   Driver: C:\WINDOWS\system32\atmespxx.cnt, 2/21/2006 18:05:00, 2887 bytes
   Driver: C:\WINDOWS\system32\atmespxx.hlx, 2/21/2006 18:05:00, 140040 bytes
   Driver: C:\WINDOWS\system32\atmfinxx.cnt, 2/21/2006 18:05:00, 2822 bytes
   Driver: C:\WINDOWS\system32\atmfinxx.hlx, 2/21/2006 18:05:00, 144213 bytes
   Driver: C:\WINDOWS\system32\atmfraxx.cnt, 2/21/2006 18:05:00, 2917 bytes
   Driver: C:\WINDOWS\system32\atmfraxx.hlx, 2/21/2006 18:05:00, 145090 bytes
   Driver: C:\WINDOWS\system32\atmhebxx.cnt, 2/21/2006 18:05:00, 2411 bytes
   Driver: C:\WINDOWS\system32\atmhebxx.hlx, 2/21/2006 18:05:00, 144323 bytes
   Driver: C:\WINDOWS\system32\atmhunxx.cnt, 2/21/2006 18:05:00, 2729 bytes
   Driver: C:\WINDOWS\system32\atmhunxx.hlx, 2/21/2006 18:05:00, 148616 bytes
   Driver: C:\WINDOWS\system32\atmitaxx.cnt, 2/21/2006 18:05:00, 2884 bytes
   Driver: C:\WINDOWS\system32\atmitaxx.hlx, 2/21/2006 18:05:00, 140646 bytes
   Driver: C:\WINDOWS\system32\atmjpnxx.cnt, 2/21/2006 18:05:00, 2453 bytes
   Driver: C:\WINDOWS\system32\atmjpnxx.hlx, 2/21/2006 18:05:00, 399936 bytes
   Driver: C:\WINDOWS\system32\atmkorxx.cnt, 2/21/2006 18:05:00, 2633 bytes
   Driver: C:\WINDOWS\system32\atmkorxx.hlx, 2/21/2006 18:05:00, 473475 bytes
   Driver: C:\WINDOWS\system32\atmnldxx.cnt, 2/21/2006 18:05:00, 2767 bytes
   Driver: C:\WINDOWS\system32\atmnldxx.hlx, 2/21/2006 18:05:00, 139835 bytes
   Driver: C:\WINDOWS\system32\atmnorxx.cnt, 2/21/2006 18:05:00, 2545 bytes
   Driver: C:\WINDOWS\system32\atmnorxx.hlx, 2/21/2006 18:05:00, 139810 bytes
   Driver: C:\WINDOWS\system32\atmplkxx.cnt, 2/21/2006 18:05:00, 2763 bytes
   Driver: C:\WINDOWS\system32\atmplkxx.hlx, 2/21/2006 18:05:00, 148498 bytes
   Driver: C:\WINDOWS\system32\atmptbxx.cnt, 2/21/2006 18:05:00, 2776 bytes
   Driver: C:\WINDOWS\system32\atmptbxx.hlx, 2/21/2006 18:05:00, 140307 bytes
   Driver: C:\WINDOWS\system32\atmrusxx.cnt, 2/21/2006 18:05:00, 2560 bytes
   Driver: C:\WINDOWS\system32\atmrusxx.hlx, 2/21/2006 18:05:00, 353829 bytes
   Driver: C:\WINDOWS\system32\atmsvexx.cnt, 2/21/2006 18:05:00, 2577 bytes
   Driver: C:\WINDOWS\system32\atmsvexx.hlx, 2/21/2006 18:05:00, 141746 bytes
   Driver: C:\WINDOWS\system32\atmthaxx.cnt, 2/21/2006 18:05:00, 2430 bytes
   Driver: C:\WINDOWS\system32\atmthaxx.hlx, 2/21/2006 18:05:00, 370049 bytes
   Driver: C:\WINDOWS\system32\atmtrkxx.cnt, 2/21/2006 18:05:00, 2653 bytes
   Driver: C:\WINDOWS\system32\atmtrkxx.hlx, 2/21/2006 18:05:00, 356937 bytes
   Driver: C:\WINDOWS\system32\atricdxx.dft, 6.14.0010.2046 (English), 2/22/2006 01:13:28, 73728 bytes
   Driver: C:\WINDOWS\system32\atricdxx.enu, 6.14.0010.2046 (English), 2/22/2006 01:13:28, 73728 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.ara, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 147456 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.chs, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 106496 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.cht, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 106496 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.csy, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 151552 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.dan, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 151552 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.deu, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 159744 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.ell, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 163840 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.enu, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 147456 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.esp, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 159744 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.fin, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 151552 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.fra, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 159744 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.heb, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 143360 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.hun, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 155648 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.ita, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 159744 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.jpn, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 118784 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.kor, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 114688 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.nld, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 155648 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.nor, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 151552 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.plk, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 155648 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.ptb, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 155648 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.rus, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 155648 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.sve, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 151552 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.tha, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 151552 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.trk, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 151552 bytes
   Driver: C:\WINDOWS\system32\attaraxx.hlx, 2/21/2006 18:05:00, 43070 bytes
   Driver: C:\WINDOWS\system32\attchsxx.hlx, 2/21/2006 18:05:00, 45991 bytes
   Driver: C:\WINDOWS\system32\attchtxx.hlx, 2/21/2006 18:05:00, 44635 bytes
   Driver: C:\WINDOWS\system32\attcsyxx.hlx, 2/21/2006 18:05:00, 44514 bytes
   Driver: C:\WINDOWS\system32\attdanxx.hlx, 2/21/2006 18:05:00, 44687 bytes
   Driver: C:\WINDOWS\system32\attdeuxx.hlx, 2/21/2006 18:05:00, 44814 bytes
   Driver: C:\WINDOWS\system32\attellxx.hlx, 2/21/2006 18:05:00, 45762 bytes
   Driver: C:\WINDOWS\system32\attenuxx.hlx, 2/21/2006 18:05:00, 40651 bytes
   Driver: C:\WINDOWS\system32\attespxx.hlx, 2/21/2006 18:05:00, 44980 bytes
   Driver: C:\WINDOWS\system32\attfinxx.hlx, 2/21/2006 18:05:00, 43310 bytes
   Driver: C:\WINDOWS\system32\attfraxx.hlx, 2/21/2006 18:05:00, 45411 bytes
   Driver: C:\WINDOWS\system32\atthebxx.hlx, 2/21/2006 18:05:00, 45632 bytes
   Driver: C:\WINDOWS\system32\atthunxx.hlx, 2/21/2006 18:05:00, 45716 bytes
   Driver: C:\WINDOWS\system32\attitaxx.hlx, 2/21/2006 18:05:00, 44109 bytes
   Driver: C:\WINDOWS\system32\attjpnxx.hlx, 2/21/2006 18:05:00, 124376 bytes
   Driver: C:\WINDOWS\system32\attkorxx.hlx, 2/21/2006 18:05:00, 141754 bytes
   Driver: C:\WINDOWS\system32\attnldxx.hlx, 2/21/2006 18:05:00, 43526 bytes
   Driver: C:\WINDOWS\system32\attnorxx.hlx, 2/21/2006 18:05:00, 43288 bytes
   Driver: C:\WINDOWS\system32\attplkxx.hlx, 2/21/2006 18:05:00, 44430 bytes
   Driver: C:\WINDOWS\system32\attptbxx.hlx, 2/21/2006 18:05:00, 45352 bytes
   Driver: C:\WINDOWS\system32\attrusxx.hlx, 2/21/2006 18:05:00, 45580 bytes
   Driver: C:\WINDOWS\system32\attsvexx.hlx, 2/21/2006 18:05:00, 41265 bytes
   Driver: C:\WINDOWS\system32\attthaxx.hlx, 2/21/2006 18:05:00, 41943 bytes
   Driver: C:\WINDOWS\system32\atttrkxx.hlx, 2/21/2006 18:05:00, 120302 bytes
   Driver: C:\WINDOWS\system32\atiiprxx.exe, 2/21/2006 18:05:00, 36864 bytes
   Driver: C:\WINDOWS\system32\atiicdxx.ini, 2/5/2000 16:02:16, 11 bytes
   Driver: C:\WINDOWS\system32\ATI_CUBE.ICO, 2/21/2006 18:05:00, 20254 bytes
   Driver: C:\WINDOWS\system32\omega_drivers.ico, 12/22/2007 14:33:07, 370070 bytes
   Driver: C:\WINDOWS\system32\omega_drivers.bmp, 9/14/2004 19:42:10, 34920 bytes
   Driver: C:\WINDOWS\system32\SmartGart.lnk, 4/26/2004 14:40:38, 1439 bytes
   Driver: C:\WINDOWS\system32\atiadaxx.exe, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 1830912 bytes
   Driver: C:\WINDOWS\system32\aticds10.dll, 6.14.0010.2087 (English), 2/22/2006 01:13:48, 348160 bytes
   Driver: C:\WINDOWS\system32\atiicdxx.msi, 2/13/2006 18:29:24, 43008 bytes
   Driver: C:\WINDOWS\system32\atioglxx.dll, 6.14.0010.7169 (English), 12/4/2007 19:19:34, 5435392 bytes
   Driver: C:\WINDOWS\system32\atiok3x2.dll, 6.14.0010.7169 (English), 12/4/2007 19:14:59, 180224 bytes
   Driver: C:\WINDOWS\system32\atioglx2.dll, 6.14.0010.7169 (English), 12/4/2007 19:48:51, 9535488 bytes
   Driver: C:\WINDOWS\system32\atiiiexx.dll, 6.14.0010.4005 (English), 9/28/2007 19:49:19, 307200 bytes
   Driver: C:\WINDOWS\atiogl.xml, 11/28/2007 14:50:12, 11717 bytes
   Driver: C:\WINDOWS\system32\DIRECTX.CPL, 5.04.0000.3900 (English), 9/30/2004 08:17:14, 135168 bytes

     Name: Radeon X1650 Series (Omega 3.8.442)   
Device ID: PCI\VEN_1002&DEV_7293&SUBSYS_210317AF&REV_9A\4&3600494A&0&0008
   Driver: C:\WINDOWS\system32\DRIVERS\ati2mtag.sys, 6.14.0010.6755 (English), 12/4/2007 22:26:40, 2782208 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ati2erec.dll, 1.00.0000.0012 (English), 12/4/2007 19:16:37, 49152 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ativvpxx.vp, 9/8/2007 20:37:03, 47360 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ativckxx.vp, 5/30/2007 10:43:05, 2096 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ativcaxx.vp, 4/18/2007 06:19:24, 929 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ativcaxx.cpa, 4/18/2007 06:19:24, 1311202 bytes
   Driver: C:\WINDOWS\system32\DRIVERS\ativdkxx.vp, 4/18/2007 05:19:50, 2096 bytes
   Driver: C:\WINDOWS\system32\ati2dvag.dll, 6.14.0010.6755 (English), 12/4/2007 20:04:08, 269312 bytes
   Driver: C:\WINDOWS\system32\ati2cqag.dll, 6.14.0010.0359 (English), 12/4/2007 19:11:18, 499712 bytes
   Driver: C:\WINDOWS\system32\Ati2mdxx.exe, 6.14.0010.2495 (English), 12/4/2007 19:55:42, 26112 bytes
   Driver: C:\WINDOWS\system32\ati3duag.dll, 6.14.0010.0510 (English), 6/26/2007 18:41:08, 2940992 bytes
   Driver: C:\WINDOWS\system32\ativvaxx.dll, 6.14.0010.0174 (English), 12/4/2007 19:33:47, 1640192 bytes
   Driver: C:\WINDOWS\system32\atiicdxx.dat, 11/6/2007 07:19:00, 158080 bytes
   Driver: C:\WINDOWS\system32\ativvaxx.dat, 12/4/2007 19:33:27, 3107788 bytes
   Driver: C:\WINDOWS\system32\ativva5x.dat, 12/4/2007 19:33:27, 3107788 bytes
   Driver: C:\WINDOWS\system32\ativva6x.dat, 12/4/2007 19:33:27, 887724 bytes
   Driver: C:\WINDOWS\system32\ATIDDC.DLL, 6.14.0010.0008 (English), 12/4/2007 19:53:09, 53248 bytes
   Driver: C:\WINDOWS\system32\atitvo32.dll, 6.14.0010.4200 (English), 12/4/2007 19:17:21, 17408 bytes
   Driver: C:\WINDOWS\system32\ativcoxx.dll, 6.13.0010.0005 (English), 11/9/2001 09:01:04, 24064 bytes
   Driver: C:\WINDOWS\system32\ati2evxx.exe, 6.14.0010.4183 (English), 12/4/2007 19:53:58, 495616 bytes
   Driver: C:\WINDOWS\system32\ati2evxx.dll, 6.14.0010.4176 (English), 12/4/2007 19:55:20, 122880 bytes
   Driver: C:\WINDOWS\system32\atipdlxx.dll, 6.14.0010.2526 (English), 12/4/2007 19:56:02, 147456 bytes
   Driver: C:\WINDOWS\system32\Oemdspif.dll, 6.15.0002.0000 (English), 12/4/2007 19:55:50, 122880 bytes
   Driver: C:\WINDOWS\system32\ati2edxx.dll, 6.14.0010.2513 (English), 12/4/2007 19:55:34, 43520 bytes
   Driver: C:\WINDOWS\system32\atikvmag.dll, 6.14.0010.0069 (English), 12/4/2007 19:19:14, 385024 bytes
   Driver: C:\WINDOWS\system32\atifglpf.xml, 8/31/2007 07:20:49, 7167 bytes
   Driver: C:\WINDOWS\system32\ATIDEMGX.dll, 2.00.2894.39756 (English), 12/4/2007 20:05:14, 368640 bytes
   Driver: C:\WINDOWS\system32\atfchtxx.hlx, 2/21/2006 18:05:00, 24589 bytes
   Driver: C:\WINDOWS\system32\atfchsxx.hlx, 2/21/2006 18:05:00, 26864 bytes
   Driver: C:\WINDOWS\system32\atfaraxx.hlx, 2/21/2006 18:05:00, 24652 bytes
   Driver: C:\WINDOWS\system32\atfcsyxx.hlx, 2/21/2006 18:05:00, 24569 bytes
   Driver: C:\WINDOWS\system32\atfdanxx.hlx, 2/21/2006 18:05:00, 24065 bytes
   Driver: C:\WINDOWS\system32\atfdeuxx.hlx, 2/21/2006 18:05:00, 24557 bytes
   Driver: C:\WINDOWS\system32\atfellxx.hlx, 2/21/2006 18:05:00, 25224 bytes
   Driver: C:\WINDOWS\system32\atfenuxx.hlx, 2/21/2006 18:05:00, 23224 bytes
   Driver: C:\WINDOWS\system32\atfespxx.hlx, 2/21/2006 18:05:00, 24382 bytes
   Driver: C:\WINDOWS\system32\atffinxx.hlx, 2/21/2006 18:05:00, 24260 bytes
   Driver: C:\WINDOWS\system32\atffraxx.hlx, 2/21/2006 18:05:00, 24640 bytes
   Driver: C:\WINDOWS\system32\atfhebxx.hlx, 2/21/2006 18:05:00, 27697 bytes
   Driver: C:\WINDOWS\system32\atfhunxx.hlx, 2/21/2006 18:05:00, 24892 bytes
   Driver: C:\WINDOWS\system32\atfitaxx.hlx, 2/21/2006 18:05:00, 24506 bytes
   Driver: C:\WINDOWS\system32\atfjpnxx.hlx, 2/21/2006 18:05:00, 49807 bytes
   Driver: C:\WINDOWS\system32\atfkorxx.hlx, 2/21/2006 18:05:00, 66161 bytes
   Driver: C:\WINDOWS\system32\atfnldxx.hlx, 2/21/2006 18:05:00, 24186 bytes
   Driver: C:\WINDOWS\system32\atfnorxx.hlx, 2/21/2006 18:05:00, 24229 bytes
   Driver: C:\WINDOWS\system32\atfplkxx.hlx, 2/21/2006 18:05:00, 26138 bytes
   Driver: C:\WINDOWS\system32\atfptbxx.hlx, 2/21/2006 18:05:00, 24712 bytes
   Driver: C:\WINDOWS\system32\atfrusxx.hlx, 2/21/2006 18:05:00, 25327 bytes
   Driver: C:\WINDOWS\system32\atfsvexx.hlx, 2/21/2006 18:05:00, 23980 bytes
   Driver: C:\WINDOWS\system32\atfthaxx.hlx, 2/21/2006 18:05:00, 24873 bytes
   Driver: C:\WINDOWS\system32\atftrkxx.hlx, 2/21/2006 18:05:00, 48174 bytes
   Driver: C:\WINDOWS\system32\atiicdxx.dll, 6.14.0010.3045 (English), 2/22/2006 01:14:58, 380928 bytes
   Driver: C:\WINDOWS\system32\atiicdxx.sys, 6.13.0010.1005 (English), 2/22/2006 01:13:54, 6144 bytes
   Driver: C:\WINDOWS\system32\atiicdxx.vxd, 4/14/2003 23:07:14, 7849 bytes
   Driver: C:\WINDOWS\system32\Atiiprxx.exe, 2/21/2006 18:05:00, 36864 bytes
   Driver: C:\WINDOWS\system32\atipdsxx.dll, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 274432 bytes
   Driver: C:\WINDOWS\system32\atiphexx.exe, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 61440 bytes
   Driver: C:\WINDOWS\system32\atippaxx.dll, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 114688 bytes
   Driver: C:\WINDOWS\system32\atiprbxx.exe, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 139264 bytes
   Driver: C:\WINDOWS\system32\atiptaxx.exe, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 344064 bytes
   Driver: C:\WINDOWS\system32\atipuixx.dll, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 2060288 bytes
   Driver: C:\WINDOWS\system32\atmaraxx.cnt, 2/21/2006 18:05:00, 2220 bytes
   Driver: C:\WINDOWS\system32\atmaraxx.hlx, 2/21/2006 18:05:00, 155364 bytes
   Driver: C:\WINDOWS\system32\atmchsxx.cnt, 2/21/2006 18:05:00, 2047 bytes
   Driver: C:\WINDOWS\system32\atmchsxx.hlx, 2/21/2006 18:05:00, 189356 bytes
   Driver: C:\WINDOWS\system32\atmchtxx.cnt, 2/21/2006 18:05:00, 2070 bytes
   Driver: C:\WINDOWS\system32\atmchtxx.hlx, 2/21/2006 18:05:00, 145421 bytes
   Driver: C:\WINDOWS\system32\atmcsyxx.cnt, 2/21/2006 18:05:00, 2615 bytes
   Driver: C:\WINDOWS\system32\atmcsyxx.hlx, 2/21/2006 18:05:00, 145641 bytes
   Driver: C:\WINDOWS\system32\atmdanxx.cnt, 2/21/2006 18:05:00, 2704 bytes
   Driver: C:\WINDOWS\system32\atmdanxx.hlx, 2/21/2006 18:05:00, 142359 bytes
   Driver: C:\WINDOWS\system32\atmdeuxx.cnt, 2/21/2006 18:05:00, 2849 bytes
   Driver: C:\WINDOWS\system32\atmdeuxx.hlx, 2/21/2006 18:05:00, 147444 bytes
   Driver: C:\WINDOWS\system32\atmellxx.cnt, 2/21/2006 18:05:00, 2759 bytes
   Driver: C:\WINDOWS\system32\atmellxx.hlx, 2/21/2006 18:05:00, 148083 bytes
   Driver: C:\WINDOWS\system32\atmenuxx.cnt, 2/21/2006 18:05:00, 2610 bytes
   Driver: C:\WINDOWS\system32\atmenuxx.hlx, 2/21/2006 18:05:00, 136272 bytes
   Driver: C:\WINDOWS\system32\atmespxx.cnt, 2/21/2006 18:05:00, 2887 bytes
   Driver: C:\WINDOWS\system32\atmespxx.hlx, 2/21/2006 18:05:00, 140040 bytes
   Driver: C:\WINDOWS\system32\atmfinxx.cnt, 2/21/2006 18:05:00, 2822 bytes
   Driver: C:\WINDOWS\system32\atmfinxx.hlx, 2/21/2006 18:05:00, 144213 bytes
   Driver: C:\WINDOWS\system32\atmfraxx.cnt, 2/21/2006 18:05:00, 2917 bytes
   Driver: C:\WINDOWS\system32\atmfraxx.hlx, 2/21/2006 18:05:00, 145090 bytes
   Driver: C:\WINDOWS\system32\atmhebxx.cnt, 2/21/2006 18:05:00, 2411 bytes
   Driver: C:\WINDOWS\system32\atmhebxx.hlx, 2/21/2006 18:05:00, 144323 bytes
   Driver: C:\WINDOWS\system32\atmhunxx.cnt, 2/21/2006 18:05:00, 2729 bytes
   Driver: C:\WINDOWS\system32\atmhunxx.hlx, 2/21/2006 18:05:00, 148616 bytes
   Driver: C:\WINDOWS\system32\atmitaxx.cnt, 2/21/2006 18:05:00, 2884 bytes
   Driver: C:\WINDOWS\system32\atmitaxx.hlx, 2/21/2006 18:05:00, 140646 bytes
   Driver: C:\WINDOWS\system32\atmjpnxx.cnt, 2/21/2006 18:05:00, 2453 bytes
   Driver: C:\WINDOWS\system32\atmjpnxx.hlx, 2/21/2006 18:05:00, 399936 bytes
   Driver: C:\WINDOWS\system32\atmkorxx.cnt, 2/21/2006 18:05:00, 2633 bytes
   Driver: C:\WINDOWS\system32\atmkorxx.hlx, 2/21/2006 18:05:00, 473475 bytes
   Driver: C:\WINDOWS\system32\atmnldxx.cnt, 2/21/2006 18:05:00, 2767 bytes
   Driver: C:\WINDOWS\system32\atmnldxx.hlx, 2/21/2006 18:05:00, 139835 bytes
   Driver: C:\WINDOWS\system32\atmnorxx.cnt, 2/21/2006 18:05:00, 2545 bytes
   Driver: C:\WINDOWS\system32\atmnorxx.hlx, 2/21/2006 18:05:00, 139810 bytes
   Driver: C:\WINDOWS\system32\atmplkxx.cnt, 2/21/2006 18:05:00, 2763 bytes
   Driver: C:\WINDOWS\system32\atmplkxx.hlx, 2/21/2006 18:05:00, 148498 bytes
   Driver: C:\WINDOWS\system32\atmptbxx.cnt, 2/21/2006 18:05:00, 2776 bytes
   Driver: C:\WINDOWS\system32\atmptbxx.hlx, 2/21/2006 18:05:00, 140307 bytes
   Driver: C:\WINDOWS\system32\atmrusxx.cnt, 2/21/2006 18:05:00, 2560 bytes
   Driver: C:\WINDOWS\system32\atmrusxx.hlx, 2/21/2006 18:05:00, 353829 bytes
   Driver: C:\WINDOWS\system32\atmsvexx.cnt, 2/21/2006 18:05:00, 2577 bytes
   Driver: C:\WINDOWS\system32\atmsvexx.hlx, 2/21/2006 18:05:00, 141746 bytes
   Driver: C:\WINDOWS\system32\atmthaxx.cnt, 2/21/2006 18:05:00, 2430 bytes
   Driver: C:\WINDOWS\system32\atmthaxx.hlx, 2/21/2006 18:05:00, 370049 bytes
   Driver: C:\WINDOWS\system32\atmtrkxx.cnt, 2/21/2006 18:05:00, 2653 bytes
   Driver: C:\WINDOWS\system32\atmtrkxx.hlx, 2/21/2006 18:05:00, 356937 bytes
   Driver: C:\WINDOWS\system32\atricdxx.dft, 6.14.0010.2046 (English), 2/22/2006 01:13:28, 73728 bytes
   Driver: C:\WINDOWS\system32\atricdxx.enu, 6.14.0010.2046 (English), 2/22/2006 01:13:28, 73728 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.ara, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 147456 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.chs, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 106496 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.cht, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 106496 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.csy, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 151552 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.dan, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 151552 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.deu, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 159744 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.ell, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 163840 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.enu, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 147456 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.esp, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 159744 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.fin, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 151552 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.fra, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 159744 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.heb, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 143360 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.hun, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 155648 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.ita, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 159744 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.jpn, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 118784 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.kor, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 114688 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.nld, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 155648 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.nor, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 151552 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.plk, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 155648 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.ptb, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 155648 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.rus, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 155648 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.sve, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 151552 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.tha, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 151552 bytes
   Driver: C:\WINDOWS\system32\atrpuixx.trk, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 151552 bytes
   Driver: C:\WINDOWS\system32\attaraxx.hlx, 2/21/2006 18:05:00, 43070 bytes
   Driver: C:\WINDOWS\system32\attchsxx.hlx, 2/21/2006 18:05:00, 45991 bytes
   Driver: C:\WINDOWS\system32\attchtxx.hlx, 2/21/2006 18:05:00, 44635 bytes
   Driver: C:\WINDOWS\system32\attcsyxx.hlx, 2/21/2006 18:05:00, 44514 bytes
   Driver: C:\WINDOWS\system32\attdanxx.hlx, 2/21/2006 18:05:00, 44687 bytes
   Driver: C:\WINDOWS\system32\attdeuxx.hlx, 2/21/2006 18:05:00, 44814 bytes
   Driver: C:\WINDOWS\system32\attellxx.hlx, 2/21/2006 18:05:00, 45762 bytes
   Driver: C:\WINDOWS\system32\attenuxx.hlx, 2/21/2006 18:05:00, 40651 bytes
   Driver: C:\WINDOWS\system32\attespxx.hlx, 2/21/2006 18:05:00, 44980 bytes
   Driver: C:\WINDOWS\system32\attfinxx.hlx, 2/21/2006 18:05:00, 43310 bytes
   Driver: C:\WINDOWS\system32\attfraxx.hlx, 2/21/2006 18:05:00, 45411 bytes
   Driver: C:\WINDOWS\system32\atthebxx.hlx, 2/21/2006 18:05:00, 45632 bytes
   Driver: C:\WINDOWS\system32\atthunxx.hlx, 2/21/2006 18:05:00, 45716 bytes
   Driver: C:\WINDOWS\system32\attitaxx.hlx, 2/21/2006 18:05:00, 44109 bytes
   Driver: C:\WINDOWS\system32\attjpnxx.hlx, 2/21/2006 18:05:00, 124376 bytes
   Driver: C:\WINDOWS\system32\attkorxx.hlx, 2/21/2006 18:05:00, 141754 bytes
   Driver: C:\WINDOWS\system32\attnldxx.hlx, 2/21/2006 18:05:00, 43526 bytes
   Driver: C:\WINDOWS\system32\attnorxx.hlx, 2/21/2006 18:05:00, 43288 bytes
   Driver: C:\WINDOWS\system32\attplkxx.hlx, 2/21/2006 18:05:00, 44430 bytes
   Driver: C:\WINDOWS\system32\attptbxx.hlx, 2/21/2006 18:05:00, 45352 bytes
   Driver: C:\WINDOWS\system32\attrusxx.hlx, 2/21/2006 18:05:00, 45580 bytes
   Driver: C:\WINDOWS\system32\attsvexx.hlx, 2/21/2006 18:05:00, 41265 bytes
   Driver: C:\WINDOWS\system32\attthaxx.hlx, 2/21/2006 18:05:00, 41943 bytes
   Driver: C:\WINDOWS\system32\atttrkxx.hlx, 2/21/2006 18:05:00, 120302 bytes
   Driver: C:\WINDOWS\system32\atiiprxx.exe, 2/21/2006 18:05:00, 36864 bytes
   Driver: C:\WINDOWS\system32\atiicdxx.ini, 2/5/2000 16:02:16, 11 bytes
   Driver: C:\WINDOWS\system32\ATI_CUBE.ICO, 2/21/2006 18:05:00, 20254 bytes
   Driver: C:\WINDOWS\system32\omega_drivers.ico, 12/22/2007 14:33:07, 370070 bytes
   Driver: C:\WINDOWS\system32\omega_drivers.bmp, 9/14/2004 19:42:10, 34920 bytes
   Driver: C:\WINDOWS\system32\SmartGart.lnk, 4/26/2004 14:40:38, 1439 bytes
   Driver: C:\WINDOWS\system32\atiadaxx.exe, 6.14.0010.5183 (English), 2/21/2006 18:05:00, 1830912 bytes
   Driver: C:\WINDOWS\system32\aticds10.dll, 6.14.0010.2087 (English), 2/22/2006 01:13:48, 348160 bytes
   Driver: C:\WINDOWS\system32\atiicdxx.msi, 2/13/2006 18:29:24, 43008 bytes
   Driver: C:\WINDOWS\system32\atioglxx.dll, 6.14.0010.7169 (English), 12/4/2007 19:19:34, 5435392 bytes
   Driver: C:\WINDOWS\system32\atiok3x2.dll, 6.14.0010.7169 (English), 12/4/2007 19:14:59, 180224 bytes
   Driver: C:\WINDOWS\system32\atioglx2.dll, 6.14.0010.7169 (English), 12/4/2007 19:48:51, 9535488 bytes
   Driver: C:\WINDOWS\system32\atiiiexx.dll, 6.14.0010.4005 (English), 9/28/2007 19:49:19, 307200 bytes
   Driver: C:\WINDOWS\atiogl.xml, 11/28/2007 14:50:12, 11717 bytes
   Driver: C:\WINDOWS\system32\DIRECTX.CPL, 5.04.0000.3900 (English), 9/30/2004 08:17:14, 135168 bytes

------------------
DirectX Components
------------------
   ddraw.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:52 279552 bytes
 ddrawex.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:52 27136 bytes
   dxapi.sys: 5.01.2600.0000 English Final Retail 8/4/2004 05:00:00 10496 bytes
    d3d8.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:52 1179648 bytes
 d3d8thk.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:52 8192 bytes
    d3d9.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:52 1689088 bytes
   d3dim.dll: 5.01.2600.0000 English Final Retail 8/4/2004 05:00:00 436224 bytes
d3dim700.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:52 824320 bytes
 d3dramp.dll: 5.01.2600.0000 English Final Retail 8/4/2004 05:00:00 590336 bytes
   d3drm.dll: 5.01.2600.0000 English Final Retail 8/4/2004 05:00:00 350208 bytes
  d3dxof.dll: 5.01.2600.0000 English Final Retail 8/4/2004 05:00:00 47616 bytes
d3dpmesh.dll: 5.01.2600.0000 English Final Retail 8/4/2004 05:00:00 34816 bytes
   dplay.dll: 5.00.2134.0001 English Final Retail 8/4/2004 05:00:00 33040 bytes
  dplayx.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 229888 bytes
dpmodemx.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 23552 bytes
 dpwsock.dll: 5.00.2134.0001 English Final Retail 8/4/2004 05:00:00 42768 bytes
dpwsockx.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 57344 bytes
dplaysvr.exe: 5.03.2600.5512 English Final Retail 4/14/2008 05:42:18 29696 bytes
  dpnsvr.exe: 5.03.2600.5512 English Final Retail 4/14/2008 05:42:18 17920 bytes
   dpnet.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 375296 bytes
dpnlobby.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:39:22 3072 bytes
 dpnaddr.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:39:20 3072 bytes
 dpvoice.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 212480 bytes
dpvsetup.exe: 5.03.2600.5512 English Final Retail 4/14/2008 05:42:20 83456 bytes
  dpvvox.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 116736 bytes
  dpvacm.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 21504 bytes
dpnhpast.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 35328 bytes
dpnhupnp.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 60928 bytes
dpserial.dll: 5.00.2134.0001 English Final Retail 8/4/2004 05:00:00 53520 bytes
  dinput.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 158720 bytes
 dinput8.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 181760 bytes
   dimap.dll: 5.01.2600.0000 English Final Retail 8/4/2004 05:00:00 44032 bytes
diactfrm.dll: 5.01.2600.0000 English Final Retail 8/4/2004 05:00:00 394240 bytes
     joy.cpl: 5.03.2600.5512 English Final Retail 4/14/2008 05:42:42 68608 bytes
   gcdef.dll: 5.01.2600.0000 English Final Retail 8/4/2004 05:00:00 76800 bytes
     pid.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:42:04 35328 bytes
gameenum.sys: 5.01.2600.5512 English Final Retail 4/14/2008 00:15:30 10624 bytes
  dsound.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 367616 bytes
dsound3d.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 1293824 bytes
  dswave.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 19456 bytes
   dsdmo.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 181248 bytes
dsdmoprp.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 71680 bytes
  dmusic.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 104448 bytes
  dmband.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 28672 bytes
dmcompos.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 61440 bytes
   dmime.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 181248 bytes
dmloader.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 35840 bytes
 dmstyle.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 105984 bytes
 dmsynth.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 103424 bytes
dmscript.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 82432 bytes
  system.dll: 1.01.4322.2443 English Final Retail 10/14/2009 03:04:20 1232896 bytes
Microsoft.DirectX.Direct3D.dll: 9.05.0132.0000 English Final Retail 4/1/2010 06:45:05 473600 bytes
Microsoft.DirectX.Direct3DX.dll: 5.04.0000.3900 English Final Retail 4/1/2010 06:44:59 2676224 bytes
Microsoft.DirectX.Direct3DX.dll: 9.04.0091.0000 English Final Retail 4/1/2010 06:45:00 2846720 bytes
Microsoft.DirectX.Direct3DX.dll: 9.05.0132.0000 English Final Retail 4/1/2010 06:45:01 563712 bytes
Microsoft.DirectX.Direct3DX.dll: 9.06.0168.0000 English Final Retail 4/1/2010 06:45:01 567296 bytes
Microsoft.DirectX.Direct3DX.dll: 9.07.0239.0000 English Final Retail 4/1/2010 06:45:02 576000 bytes
Microsoft.DirectX.Direct3DX.dll: 9.08.0299.0000 English Final Retail 4/1/2010 06:45:02 577024 bytes
Microsoft.DirectX.Direct3DX.dll: 9.09.0376.0000 English Final Retail 4/1/2010 06:45:03 577536 bytes
Microsoft.DirectX.Direct3DX.dll: 9.10.0455.0000 English Final Retail 4/1/2010 06:45:03 577536 bytes
Microsoft.DirectX.Direct3DX.dll: 9.11.0519.0000 English Final Retail 4/1/2010 06:45:04 578560 bytes
Microsoft.DirectX.Direct3DX.dll: 9.12.0589.0000 English Final Retail 4/1/2010 06:45:06 578560 bytes
Microsoft.DirectX.DirectDraw.dll: 5.04.0000.2904 English Final Retail 4/1/2010 06:45:06 145920 bytes
Microsoft.DirectX.DirectInput.dll: 5.04.0000.2904 English Final Retail 4/1/2010 06:45:06 159232 bytes
Microsoft.DirectX.DirectPlay.dll: 5.04.0000.2904 English Final Retail 4/1/2010 06:45:07 364544 bytes
Microsoft.DirectX.DirectSound.dll: 5.04.0000.2904 English Final Retail 4/1/2010 06:45:07 178176 bytes
Microsoft.DirectX.AudioVideoPlayback.dll: 5.04.0000.2904 English Final Retail 4/1/2010 06:45:05 53248 bytes
Microsoft.DirectX.Diagnostics.dll: 5.04.0000.2904 English Final Retail 4/1/2010 06:45:05 12800 bytes
Microsoft.DirectX.dll: 5.04.0000.2904 English Final Retail 4/1/2010 06:45:04 223232 bytes
   dx7vb.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 619008 bytes
   dx8vb.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 1227264 bytes
 dxdiagn.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 2113536 bytes
 directx.cpl: 5.04.0000.3900 English Final Retail 9/30/2004 08:17:14 135168 bytes
   mfc40.dll: 4.01.0000.6140 English Final Retail 8/4/2004 05:00:00 924432 bytes
   mfc42.dll: 6.02.4131.0000 English Final Retail 4/14/2008 05:41:58 1028096 bytes
 wsock32.dll: 5.01.2600.5512 English Final Retail 4/14/2008 05:42:12 22528 bytes
amstream.dll: 6.05.2600.5512 English Final Retail 4/14/2008 05:41:50 70656 bytes
 devenum.dll: 6.05.2600.5512 English Final Retail 4/14/2008 05:41:52 59904 bytes
  dxmasf.dll: 6.04.0009.1133 English Final Retail 4/14/2008 05:41:54 498742 bytes
mciqtz32.dll: 6.05.2600.5512 English Final Retail 4/14/2008 05:41:58 35328 bytes
 mpg2splt.ax: 6.05.2600.5512 English Final Retail 4/14/2008 05:42:44 148992 bytes
   msdmo.dll: 6.05.2600.5512 English Final Retail 4/14/2008 05:42:00 14336 bytes
  encapi.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:41:54 20480 bytes
    qasf.dll: 11.00.5721.5145 English Final Retail 10/18/2006 21:47:18 211456 bytes
    qcap.dll: 6.05.2600.5512 English Final Retail 4/14/2008 05:42:04 192512 bytes
     qdv.dll: 6.05.2600.5512 English Final Retail 4/14/2008 05:42:04 279040 bytes
    qdvd.dll: 6.05.2600.5512 English Final Retail 4/14/2008 05:42:04 386048 bytes
   qedit.dll: 6.05.2600.5512 English Final Retail 4/14/2008 05:42:04 562176 bytes
qedwipes.dll: 6.05.2600.5512 English Final Retail 4/13/2008 22:51:34 733696 bytes
  quartz.dll: 6.05.2600.5908 English Final Retail 11/27/2009 10:11:44 1291776 bytes
 strmdll.dll: 4.01.0000.3938 English Final Retail 8/26/2009 01:00:21 247326 bytes
 iac25_32.ax: 2.00.0005.0053 English Final Retail 4/14/2008 05:42:44 199680 bytes
  ir41_32.ax: 4.51.0016.0003 English Final Retail 4/14/2008 05:42:44 848384 bytes
 ir41_qc.dll: 4.30.0062.0002 English Final Retail 4/14/2008 05:41:56 120320 bytes
ir41_qcx.dll: 4.30.0064.0001 English Final Retail 4/14/2008 05:41:56 338432 bytes
 ir50_32.dll: 5.2562.0015.0055 English Final Retail 4/14/2008 05:41:56 755200 bytes
 ir50_qc.dll: 5.00.0063.0048 English Final Retail 4/14/2008 05:41:56 200192 bytes
ir50_qcx.dll: 5.00.0064.0048 English Final Retail 4/14/2008 05:41:56 183808 bytes
   ivfsrc.ax: 5.10.0002.0051 English Final Retail 4/14/2008 05:42:44 154624 bytes
mswebdvd.dll: 6.05.2600.5857 English Final Retail 8/5/2009 02:01:48 204800 bytes
      ks.sys: 5.03.2600.5512 English Final Retail 4/14/2008 00:46:38 141056 bytes
  ksproxy.ax: 5.03.2600.5512 English Final Retail 4/14/2008 05:42:44 129536 bytes
  ksuser.dll: 5.03.0000.0900 English Final Retail 12/12/2002 00:14:32 4096 bytes
  stream.sys: 5.03.0001.0904 English Final Retail 7/9/2004 04:27:28 48512 bytes
mspclock.sys: 5.03.2600.5512 English Final Retail 4/14/2008 00:09:52 5376 bytes
   mspqm.sys: 5.01.2600.5512 English Final Retail 4/14/2008 00:09:52 4992 bytes
 mskssrv.sys: 5.03.2600.5512 English Final Retail 4/14/2008 00:09:54 7552 bytes
  swenum.sys: 5.03.2600.5512 English Final Retail 4/14/2008 00:09:54 4352 bytes
   mstee.sys: 5.03.0000.0900 English Final Retail 12/12/2002 00:14:32 5504 bytes
 bdaplgin.ax: 5.03.0000.0900 English Final Retail 7/9/2004 04:26:38 16896 bytes
  bdasup.sys: 5.03.0000.0900 English Final Retail 7/9/2004 04:26:38 11392 bytes
  msdvbnp.ax: 6.05.0001.0900 English Final Retail 7/9/2004 04:26:38 52224 bytes
psisdecd.dll: 6.05.0001.0900 English Final Retail 7/9/2004 04:26:40 354816 bytes
 psisrndr.ax: 6.05.0001.0900 English Final Retail 7/9/2004 04:26:40 30208 bytes
   ipsink.ax: 5.03.0000.0900 English Final Retail 7/9/2004 04:26:38 14848 bytes
mpeg2data.ax: 6.05.2600.5512 English Final Retail 4/14/2008 05:42:44 118272 bytes
  ndisip.sys: 5.03.0000.0900 English Final Retail 7/9/2004 04:26:38 10112 bytes
     mpe.sys: 5.03.0000.0900 English Final Retail 7/9/2004 04:26:38 15104 bytes
streamip.sys: 5.03.0000.0900 English Final Retail 7/9/2004 04:26:40 14976 bytes
msvidctl.dll: 6.05.2600.5512 English Final Retail 4/14/2008 05:42:02 1428992 bytes
    slip.sys: 5.03.0000.0900 English Final Retail 7/9/2004 04:26:40 10880 bytes
nabtsfec.sys: 5.03.0000.0900 English Final Retail 7/9/2004 04:26:38 83968 bytes
ccdecode.sys: 5.03.0000.0900 English Final Retail 7/9/2004 04:26:38 16384 bytes
  vbisurf.ax: 5.03.2600.5512 English Final Retail 4/14/2008 05:42:44 30208 bytes
   msyuv.dll: 5.03.2600.5908 English Final Retail 11/27/2009 10:11:44 17920 bytes
 kstvtune.ax: 5.03.0001.0904 English Final Retail 7/19/2004 16:19:30 285696 bytes
   ksxbar.ax: 5.03.0001.0902 English Final Retail 7/9/2004 04:26:38 39424 bytes
 kswdmcap.ax: 5.03.0000.0900 English Final Retail 7/9/2004 04:26:40 226304 bytes
wstcodec.sys: 5.03.0000.0900 English Final Retail 7/9/2004 04:26:40 18688 bytes
wstdecod.dll: 5.03.2600.5512 English Final Retail 4/14/2008 05:42:12 50688 bytes
    msdv.sys: 5.01.2600.0000 English Final Retail 7/9/2004 04:26:38 52096 bytes

------------------
DirectShow Filters
------------------

DirectShow Filters:
QuickTime Audio Decoder Filter,0x00600800,1,1,,
WMAudio Decoder DMO,0x00800800,1,1,,
WMAPro over S/PDIF DMO,0x00600800,1,1,,
WMA Voice Decoder DMO,0x00600800,1,1,,
Mpeg4s Decoder DMO,0x00800001,1,1,,
WMV Screen decoder DMO,0x00800001,1,1,,
WMVideo Decoder DMO,0x00800001,1,1,,
QuickTime Video Decoder Filter,0x00600800,1,1,,
Mpeg43 Decoder DMO,0x00800001,1,1,,
Mpeg4 Decoder DMO,0x00800001,1,1,,
WMT MuxDeMux Filter,0x00200000,0,0,wmm2filt.dll,2.01.4026.0000
ffdshow Video Decoder,0xff800001,2,1,ffdshow.ax,1.00.0005.1659
Full Screen Renderer,0x00200000,1,0,quartz.dll,6.05.2600.5908
ffdshow raw video filter,0x00200000,2,1,ffdshow.ax,1.00.0005.1659
ffdshow Audio Decoder,0x3fffffff,1,1,ffdshow.ax,1.00.0005.1659
CyberLink DVD Navigator,0x00600000,0,3,CLNAV.ax,3.05.0000.1812
DV Muxer,0x00400000,0,0,qdv.dll,6.05.2600.5512
Color Space Converter,0x00400001,1,1,quartz.dll,6.05.2600.5908
WM ASF Reader,0x00400000,0,0,qasf.dll,11.00.5721.5145
DivX AAC Decoder,0x00800000,1,1,daac.ax,7.01.0000.0010
Screen Capture filter,0x00200000,0,1,wmpsrcwp.dll,11.00.5721.5145
AVI Splitter,0x00600000,1,1,quartz.dll,6.05.2600.5908
WMT AudioAnalyzer,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
VGA 16 Color Ditherer,0x00400000,1,1,quartz.dll,6.05.2600.5908
Indeo® video 5.10 Compression Filter,0x00200000,1,1,ir50_32.dll,5.2562.0015.0055
Windows Media Audio Decoder,0x00800001,1,1,msadds32.ax,8.00.0000.4487
RealVideo Decoder,0x00400000,1,1,RealMediaSplitter.ax,1.00.0001.0002
AC3 Parser Filter,0x00600000,1,1,mpg2splt.ax,6.05.2600.5512
WMT Format Conversion,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
StreamBufferSink,0x00200000,0,0,sbe.dll,6.05.2600.5512
WMT Black Frame Generator,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
MJPEG Decompressor,0x00600000,1,1,quartz.dll,6.05.2600.5908
Indeo® video 5.10 Decompression Filter,0x00640000,1,1,ir50_32.dll,5.2562.0015.0055
WMT Screen Capture filter,0x00200000,0,1,wmm2filt.dll,2.01.4026.0000
Microsoft Screen Video Decompressor,0x00800000,1,1,msscds32.ax,8.00.0000.4487
MPEG-I Stream Splitter,0x00600000,1,2,quartz.dll,6.05.2600.5908
SAMI (CC) Parser,0x00400000,1,1,quartz.dll,6.05.2600.5908
MPEG Layer-3 Decoder,0x00810000,1,1,l3codecx.ax,1.05.0000.0050
MPEG-2 Splitter,0x005fffff,1,0,mpg2splt.ax,6.05.2600.5512
CyberLink Audio Effect,0x00200000,1,1,claudfx.ax,3.05.0000.1228
ACELP.net Sipro Lab Audio Decoder,0x00800001,1,1,acelpdec.ax,1.04.0000.0000
File Source (MP3),0x00400000,0,1,MP3Source.ax,
FLV Splitter,0x00600000,1,1,FLVSplitter.ax,1.00.0000.0002
Internal Script Command Renderer,0x00800001,1,0,quartz.dll,6.05.2600.5908
MPEG Audio Decoder,0x03680001,1,1,quartz.dll,6.05.2600.5908
File Source (Netshow URL),0x00400000,0,1,wmpasf.dll,11.00.5721.5145
WMT Import Filter,0x00200000,0,1,wmm2filt.dll,2.01.4026.0000
DV Splitter,0x00600000,1,2,qdv.dll,6.05.2600.5512
Bitmap Generate,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Windows Media Video Decoder,0x00800000,1,1,wmvds32.ax,8.00.0000.4487
Video Mixing Renderer 9,0x00200000,1,0,quartz.dll,6.05.2600.5908
Windows Media Video Decoder,0x00800000,1,1,wmv8ds32.ax,8.00.0000.4000
CDDA Reader,0x00400000,0,1,cddareader.ax,1.00.0000.0001
Haali Media Splitter,0x00800001,0,1,splitter.ax,1.07.0189.0011
Haali Media Splitter (AR),0x00400000,1,1,splitter.ax,1.07.0189.0011
WMT VIH2 Fix,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Record Queue,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Windows Media Multiplexer,0x00600000,1,1,wmpasf.dll,11.00.5721.5145
ASX file Parser,0x00600000,1,1,wmpasf.dll,11.00.5721.5145
ASX v.2 file Parser,0x00600000,1,0,wmpasf.dll,11.00.5721.5145
NSC file Parser,0x00600000,1,1,wmpasf.dll,11.00.5721.5145
ShoutcastSource,0x00400000,0,1,shoutcastsource.ax,
ACM Wrapper,0x00600000,1,1,quartz.dll,6.05.2600.5908
Windows Media source filter,0x00600000,0,2,wmpasf.dll,11.00.5721.5145
Video Renderer,0x00800001,1,0,quartz.dll,6.05.2600.5908
Frame Eater,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
MPEG-2 Video Stream Analyzer,0x00200000,0,0,sbe.dll,6.05.2600.5512
Line 21 Decoder,0x00600000,1,1,qdvd.dll,6.05.2600.5512
Video Port Manager,0x00600000,2,1,quartz.dll,6.05.2600.5908
DivX H.264 Decoder,0x00800000,1,1,DivXDecH264.ax,8.02.0000.0026
WST Decoder,0x00600000,1,1,wstdecod.dll,5.03.2600.5512
Video Renderer,0x00400000,1,0,quartz.dll,6.05.2600.5908
Haali Video Renderer,0x00200000,1,0,dxr.dll,
RealMedia Source,0x00600000,0,0,RealMediaSplitter.ax,1.00.0001.0002
DivX Decoder Filter,0x00800000,1,1,divxdec.ax,7.00.0000.0031
WM ASF Writer,0x00400000,0,0,qasf.dll,11.00.5721.5145
FLV Video Decoder,0x00600000,1,1,FLVSplitter.ax,1.00.0000.0002
WMT Sample Information Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
VBI Surface Allocator,0x00600000,1,1,vbisurf.ax,5.03.2600.5512
Microsoft MPEG-4 Video Decompressor,0x00800000,1,1,mpg4ds32.ax,8.00.0000.4487
DivX Demux,0x00600000,1,0,DivXMedia.ax,0.00.0000.0028
File writer,0x00200000,1,0,qcap.dll,6.05.2600.5512
Haali Simple Media Splitter,0x00200000,0,1,splitter.ax,1.07.0189.0011
WMT Log Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
WMT Virtual Renderer,0x00200000,1,0,wmm2filt.dll,2.01.4026.0000
DirectVobSub,0x00200000,2,1,VSFilter.dll,1.00.0001.0004
RealAudio Decoder,0x00400000,1,1,RealMediaSplitter.ax,1.00.0001.0002
DirectVobSub (auto-loading version),0x00800002,2,1,VSFilter.dll,1.00.0001.0004
DVD Navigator,0x00200000,0,2,qdvd.dll,6.05.2600.5512
CyberLink Audio Decoder,0x00601000,1,1,claud.ax,3.05.0000.1814
CyberLink Video/SP Decoder,0x00600000,2,3,clvsd.ax,3.05.0000.1814
Overlay Mixer2,0x00400000,1,1,qdvd.dll,6.05.2600.5512
Haali Matroska Muxer,0x00200000,1,0,splitter.ax,1.07.0189.0011
DivX MKV Demux,0x00200000,0,1,DMFSource.ax,1.00.0001.0004
AVI Draw,0x00600064,9,1,quartz.dll,6.05.2600.5908
.RAM file Parser,0x00600000,1,0,wmpasf.dll,11.00.5721.5145
WMT DirectX Transform Wrapper,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
G.711 Codec,0x00200000,1,1,g711codc.ax,5.01.2600.0000
MPEG-2 Demultiplexer,0x00600000,1,1,mpg2splt.ax,6.05.2600.5512
DV Video Decoder,0x00800000,1,1,qdv.dll,6.05.2600.5512
Indeo® audio software,0x00500000,1,1,iac25_32.ax,2.00.0005.0053
Windows Media Update Filter,0x00400000,1,0,wmpasf.dll,11.00.5721.5145
ffdshow Audio Processor,0x00200000,1,1,ffdshow.ax,1.00.0005.1659
ASF DIB Handler,0x00600000,1,1,wmpasf.dll,11.00.5721.5145
ASF ACM Handler,0x00600000,1,1,wmpasf.dll,11.00.5721.5145
ASF ICM Handler,0x00600000,1,1,wmpasf.dll,11.00.5721.5145
ASF URL Handler,0x00600000,1,1,wmpasf.dll,11.00.5721.5145
ASF JPEG Handler,0x00600000,1,1,wmpasf.dll,11.00.5721.5145
ASF DJPEG Handler,0x00600000,1,1,wmpasf.dll,11.00.5721.5145
ASF embedded stuff Handler,0x00600000,1,1,wmpasf.dll,11.00.5721.5145
DivX Subtitle Decoder,0x00600000,1,1,DivXMedia.ax,0.00.0000.0028
9x8Resize,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
WIA Stream Snapshot Filter,0x00200000,1,1,wiasf.ax,1.00.0000.0000
Allocator Fix,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
SampleGrabber,0x00200000,1,1,qedit.dll,6.05.2600.5512
Null Renderer,0x00200000,1,0,qedit.dll,6.05.2600.5512
WMT Virtual Source,0x00200000,0,1,wmm2filt.dll,2.01.4026.0000
CyberLink DxVA Filter 2,0x00200000,0,3,Cldxva.ax,
MPEG-2 Sections and Tables,0x005fffff,1,0,mpeg2data.ax,6.05.2600.5512
IVF source filter,0x00600000,0,1,ivfsrc.ax,5.10.0002.0051
WMT Interlacer,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
FLV Source,0x00600000,0,0,FLVSplitter.ax,1.00.0000.0002
StreamBufferSource,0x00200000,0,0,sbe.dll,6.05.2600.5512
Smart Tee,0x00200000,1,2,qcap.dll,6.05.2600.5512
Overlay Mixer,0x00200000,0,0,qdvd.dll,6.05.2600.5512
AVI Decompressor,0x00600000,1,1,quartz.dll,6.05.2600.5908
Uncompressed Domain Shot Detection Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
DScaler Audio Decoder,0x00800000,1,1,MpegAudio.dll,0.00.0008.0000
AVI/WAV File Source,0x00400000,0,2,quartz.dll,6.05.2600.5908
Arcsoft Snapshot Filter 1.0,0x00200000,1,1,ArcSnap.ax,
QuickTime Movie Parser,0x00600000,1,1,quartz.dll,6.05.2600.5908
Wave Parser,0x00400000,1,1,quartz.dll,6.05.2600.5908
MIDI Parser,0x00400000,1,1,quartz.dll,6.05.2600.5908
Multi-file Parser,0x00400000,1,1,quartz.dll,6.05.2600.5908
File stream renderer,0x00400000,1,1,quartz.dll,6.05.2600.5908
XML Playlist,0x00400000,1,0,wmpasf.dll,11.00.5721.5145
RealMedia Splitter,0x00600000,1,1,RealMediaSplitter.ax,1.00.0001.0002
AVI Mux,0x00200000,1,0,qcap.dll,6.05.2600.5512
Line 21 Decoder 2,0x00600002,1,1,quartz.dll,6.05.2600.5908
File Source (Async.),0x00400000,0,1,quartz.dll,6.05.2600.5908
File Source (URL),0x00400000,0,1,quartz.dll,6.05.2600.5908
WMT DV Extract,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
WMT Switch Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
WMT Volume,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Haali Video Sink,0x00200000,1,0,splitter.ax,1.07.0189.0011
Stretch Video,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Infinite Pin Tee Filter,0x00200000,1,1,qcap.dll,6.05.2600.5512
DScaler Mpeg2 Video Decoder,0x00800000,1,1,MpegVideo.dll,0.00.0006.0000
BDA MPEG2 Transport Information Filter,0x00200000,1,0,psisrndr.ax,6.05.0001.0900
QT Decompressor,0x00600000,1,1,quartz.dll,6.05.2600.5908
MPEG Video Decoder,0x40000001,1,1,quartz.dll,6.05.2600.5908
Indeo® video 4.4 Decompression Filter,0x00640000,1,1,ir41_32.ax,4.51.0016.0003
Indeo® video 4.4 Compression Filter,0x00200000,1,1,ir41_32.ax,4.51.0016.0003

WDM Streaming Data Transforms:
Microsoft Kernel Acoustic Echo Canceller,0x00000000,0,0,,
Microsoft Kernel GS Wavetable Synthesizer,0x00200000,1,1,,5.03.2600.5512
Microsoft Kernel DLS Synthesizer,0x00200000,1,1,,5.03.2600.5512
Microsoft Kernel DRM Audio Descrambler,0x00200000,1,1,,5.03.2600.5512

Video Compressors:
WMVideo8 Encoder DMO,0x00600800,1,1,,
MSScreen encoder DMO,0x00600800,1,1,,
WMVideo9 Encoder DMO,0x00600800,1,1,,
MSScreen 9 encoder DMO,0x00600800,1,1,,
DV Video Encoder,0x00200000,0,0,qdv.dll,6.05.2600.5512
ffdshow video encoder,0x00100000,1,1,ffdshow.ax,1.00.0005.1659
Indeo® video 5.10 Compression Filter,0x00100000,1,1,ir50_32.dll,5.2562.0015.0055
MJPEG Compressor,0x00200000,0,0,quartz.dll,6.05.2600.5908
Cinepak Codec by Radius,0x00200000,1,1,qcap.dll,6.05.2600.5512
DivX® 6.8 Codec (1 Logical CPU),0x00200000,1,1,qcap.dll,6.05.2600.5512
ffdshow Video Codec,0x00200000,1,1,qcap.dll,6.05.2600.5512
Intel 4:2:0 Video V2.50,0x00200000,1,1,qcap.dll,6.05.2600.5512
Intel Indeo(R) Video R3.2,0x00200000,1,1,qcap.dll,6.05.2600.5512
Intel Indeo® Video 4.5,0x00200000,1,1,qcap.dll,6.05.2600.5512
Indeo® video 5.10,0x00200000,1,1,qcap.dll,6.05.2600.5512
Intel IYUV codec,0x00200000,1,1,qcap.dll,6.05.2600.5512
Microsoft H.261 Video Codec,0x00200000,1,1,qcap.dll,6.05.2600.5512
Microsoft H.263 Video Codec,0x00200000,1,1,qcap.dll,6.05.2600.5512
Microsoft RLE,0x00200000,1,1,qcap.dll,6.05.2600.5512
Microsoft Video 1,0x00200000,1,1,qcap.dll,6.05.2600.5512
Xfire Video Codec,0x00200000,1,1,qcap.dll,6.05.2600.5512
DivX® 6.8 YV12 Decoder,0x00200000,1,1,qcap.dll,6.05.2600.5512

Audio Compressors:
WMA Voice Encoder DMO,0x00600800,1,1,,
WM Speech Encoder DMO,0x00600800,1,1,,
WMAudio Encoder DMO,0x00600800,1,1,,
IAC2,0x00200000,1,1,quartz.dll,6.05.2600.5908
Lernout & Hauspie CELP 4.8kbit/s,0x00200000,1,1,quartz.dll,6.05.2600.5908
Lernout & Hauspie SBC 8kbit/s,0x00200000,1,1,quartz.dll,6.05.2600.5908
Lernout & Hauspie SBC 12kbit/s,0x00200000,1,1,quartz.dll,6.05.2600.5908
Lernout & Hauspie SBC 16kbit/s,0x00200000,1,1,quartz.dll,6.05.2600.5908
IMA ADPCM,0x00200000,1,1,quartz.dll,6.05.2600.5908
PCM,0x00200000,1,1,quartz.dll,6.05.2600.5908
Microsoft ADPCM,0x00200000,1,1,quartz.dll,6.05.2600.5908
ACELP.net,0x00200000,1,1,quartz.dll,6.05.2600.5908
DSP Group TrueSpeech(TM),0x00200000,1,1,quartz.dll,6.05.2600.5908
Windows Media Audio V1,0x00200000,1,1,quartz.dll,6.05.2600.5908
Windows Media Audio V2,0x00200000,1,1,quartz.dll,6.05.2600.5908
GSM 6.10,0x00200000,1,1,quartz.dll,6.05.2600.5908
Microsoft G.723.1,0x00200000,1,1,quartz.dll,6.05.2600.5908
CCITT A-Law,0x00200000,1,1,quartz.dll,6.05.2600.5908
CCITT u-Law,0x00200000,1,1,quartz.dll,6.05.2600.5908
MPEG Layer-3,0x00200000,1,1,quartz.dll,6.05.2600.5908

Audio Capture Sources:
Turtle Beach Riviera Wave,0x00200000,0,0,qcap.dll,6.05.2600.5512

Midi Renderers:
Default MidiOut Device,0x00800000,1,0,quartz.dll,6.05.2600.5908
Microsoft GS Wavetable SW Synth,0x00200000,1,0,quartz.dll,6.05.2600.5908

WDM Streaming Capture Devices:
Turtle Beach Riviera Wave,0x00200000,3,3,,5.03.2600.5512

WDM Streaming Rendering Devices:
Turtle Beach Riviera Wave,0x00200000,3,3,,5.03.2600.5512

BDA Network Providers:
Microsoft ATSC Network Provider,0x00200000,0,1,msdvbnp.ax,6.05.0001.0900
Microsoft DVBC Network Provider,0x00200000,0,1,msdvbnp.ax,6.05.0001.0900
Microsoft DVBS Network Provider,0x00200000,0,1,msdvbnp.ax,6.05.0001.0900
Microsoft DVBT Network Provider,0x00200000,0,1,msdvbnp.ax,6.05.0001.0900

BDA Transport Information Renderers:
BDA MPEG2 Transport Information Filter,0x00600000,1,0,psisrndr.ax,6.05.0001.0900
MPEG-2 Sections and Tables,0x00600000,1,0,mpeg2data.ax,6.05.2600.5512

WDM Streaming Mixer Devices:
Microsoft Kernel Wave Audio Mixer,0x00000000,0,0,,

BDA CP/CA Filters:
Decrypt/Tag,0x00600000,1,0,encdec.dll,6.05.2600.5512
Encrypt/Tag,0x00200000,0,0,encdec.dll,6.05.2600.5512
XDS Codec,0x00200000,0,0,encdec.dll,6.05.2600.5512

Audio Renderers:
Turtle Beach Riviera Wave,0x00200000,1,0,quartz.dll,6.05.2600.5908
Default DirectSound Device,0x00800000,1,0,quartz.dll,6.05.2600.5908
Default WaveOut Device,0x00200000,1,0,quartz.dll,6.05.2600.5908
DirectSound: Turtle Beach Riviera Wave,0x00200000,1,0,quartz.dll,6.05.2600.5908

WDM Streaming System Devices:
Turtle Beach Riviera Wave,0x00200000,8,3,,5.03.2600.5512


```

---

### Post by NightwishFan on 2010-04-02
It might be a display related issue. Do you have desktop effects enabled? If so, your driver has to be working well, try disabling them. If performance is good with effects off, leave them off for now. Perhaps try the proprietary driver in System -> Administration -> Hardware Drivers.

Also does sound skip when it plays? If so, you might have installed using a bad cd, place the one you installed ubuntu with in the drive, reboot and run check for errors.

---

### Post by Revord on 2010-04-02
I turned off desktop effects, and ran the update this morning. Things seemed to smooth out for me, at least with running firefox and basic apps. Running games (most notably Alien Arena) is still a no go, at least if they have anything intensive in the graphics department. I can still play mines though ;) Sound isnt a problem. I can play a video on hulu, but video is really bad, although the audio is good. 

I didnt install via cd, I did it via wubi, so it was the direct image that I used as opposed to a burned cd. I did however check the hardware drivers, and noticed there were no proprietary drivers listed. Im thinking that may be my problem. Ill look into it and see if I can get that, and report back.

---

### Post by NightwishFan on 2010-04-02
Indeed it sounds like a video card issue. Not really my area of expertise to be honest.

---

### Post by Revord on 2010-04-02
Well, Im at an impass here. I checked both Ubuntu software center, and the Synaptic package manager, and I found that drivers ARE installed, but proprietary drivers ARE NOT according to the hardware drivers app. I've included a screenshot of the Ubuntu software center where I did a search for ATI, primarily because it was easier to get everything in one shot as opposed to synaptic. If there is anything Im missing, let me know. It seems that Im close to a solution here, and I would really like to go forward with this. Just for info purposes, I have an ATI Radeon X1650 AGP video card.

---

### Post by strobe on 2010-04-04
What type of cpu usage are you seeing?  With anything other than the nouveau I get stutters.  Not a ram issue, its a cpu issue.  The nvidia drivers for my system max my cpu out.  Was not an issue in Karmic.  Something to do with Lucid, Nvidia, and my laptop.

---

