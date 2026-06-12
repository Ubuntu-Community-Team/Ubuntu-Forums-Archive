---
title: "Cant Run live CD"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by MaxTesla on 2010-10-11
I downloaded the cd and burned it and checked it and all that
 

 I start the computer and the press f6 when that picture of the guy and the keyboard comes up and then I choose try ubuntu without installing
 

 Then I can se a white small line blinking in the upper left corner then it goes black, my monitor switches off and then nothing happens
 

 I had the same problem trying to run 10.04 and 9.10
 

 And I have had many different monitor so it is of course not that
 

 I dont know why it wont work just that it dose not work, so will Ubuntu never work on this specific computer or will the next version work?


System Information
------------------
   Operating System: Windows 7 Home Premium 64-bit (6.1, Build 7600) (7600.win7_gdr.100618-1621)
System Manufacturer: FUJITSU                         
       System Model: ESPRIMO P1500                 
               BIOS: Version 6.00 R1.05.2950.A1
          Processor: Intel(R) Core(TM)2 Quad CPU    Q8300  @ 2.50GHz (4 CPUs), ~2.5GHz
             Memory: 4096MB RAM
Available OS Memory: 4094MB RAM
          Page File: 1244MB used, 6942MB available
        Windows Dir: C:\Windows
    DirectX Version: DirectX 11
DX Setup Parameters: Not found
   User DPI Setting: Using System DPI
 System DPI Setting: 96 DPI (100 percent)
    DWM DPI Scaling: Disabled
     DxDiag Version: 6.01.7600.16385 32bit Unicode

------------
DxDiag Notes
------------
      Display Tab 1: No problems found.
        Sound Tab 1: No problems found.
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
          Card name: NVIDIA GeForce GT 220  
       Manufacturer: NVIDIA
          Chip type: GeForce GT 220
           DAC type: Integrated RAMDAC
         Device Key: Enum\PCI\VEN_10DE&DEV_0A20&SUBSYS_2160174B&REV_A2
     Display Memory: 2777 MB
   Dedicated Memory: 986 MB
      Shared Memory: 1791 MB
       Current Mode: 1920 x 1080 (32 bit) (60Hz)
       Monitor Name: Generic PnP Monitor
      Monitor Model: W2253
         Monitor Id: GSM56DC
        Native Mode: 1920 x 1080(p) (59.934Hz)
        Output Type: DVI
        Driver Name: nvd3dumx.dll,nvwgf2umx.dll,nvwgf2umx.dll,nvd3dum,nvwgf2um,nvwgf2um
Driver File Version: 8.17.0011.9745 (English)
     Driver Version: 8.17.11.9745
        DDI Version: 10.1
       Driver Model: WDDM 1.1
  Driver Attributes: Final Retail
   Driver Date/Size: 4/3/2010 22:55:32, 11906664 bytes
        WHQL Logo'd: n/a
    WHQL Date Stamp: n/a
  Device Identifier: {D7B71E3E-4960-11CF-EA52-6B011CC2C535}
          Vendor ID: 0x10DE
          Device ID: 0x0A20
          SubSys ID: 0x2160174B
        Revision ID: 0x00A2
 Driver Strong Name: oem11.inf:NVIDIA_SetA_Devices.NTamd64.6.1:Section011:8.17.11.9745:pci\ven_10de&dev_0a20&subsys_2160174b
     Rank Of Driver: 00E60001

---

### Post by MaxTesla on 2010-10-12
Have checked on google and it seems that people with Fujitsu Siemens ESPRIMO P1500 cant run Ubuntu

This sucks balls

Fix it!

---

### Post by MaxTesla on 2010-10-12
bump

---

### Post by sidzen on 2010-10-12
Before giving up completely, try putting in a different non-Fujitsu hard drive in with SuperOS.
I've seen Fujitsu hard drives deliberately "die" after wiping with zeros and cleanly installing ubuntu.

---

### Post by MaxTesla on 2010-10-12
Whats a superOS?

Also what I want is that the ubuntu programmers program ubuntu so that it works with my computer, that is all that I want

---

### Post by mikechant on 2010-10-12
There are reports that this machine works OK if you specify the 'noapic' boot option in the installer.
Eg:
[http://help.lockergnome.com/linux/Bug-586854-Installation-Fujitsu-Esprimo-P1500-requires-noapi--ftopict522117.html](http://help.lockergnome.com/linux/Bug-586854-Installation-Fujitsu-Esprimo-P1500-requires-noapi--ftopict522117.html)

I'm not at my Ubuntu PC at the moment  but there's an option to specify options like this when booting from the Live CD (possibly using F6 on the appropriate screen) and you will typically see a boot line ending in 'splash', you can add noapic after this.

If this works and you decide to install you can make this option permamnant so you don't have to specify it on every boot.

These sort of problems are often caused by BIOS bugs and may sometimes be corrected by flashing the BIOS to the latest level.

---

### Post by MaxTesla on 2010-10-12
How do i Flash Bios?
 
Yes I have seen this web page before
 
What does the "apic" do
 
And how exactlly do I select no apic exactlly?

---

### Post by MaxTesla on 2010-10-13
bump

---

