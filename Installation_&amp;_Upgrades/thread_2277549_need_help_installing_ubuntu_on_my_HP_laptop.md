---
title: "need help installing ubuntu on my HP laptop"
date: 2015-05-09
forum: Installation &amp; Upgrades
---

### Post by kaitlin3 on 2015-05-09
ok so i am trying to install ubuntu 14.04 lts on my elitebook 8530p and the install fails to install the bootloader and says the installer has crashed ubuntu will create a desktop enviroment idk what to do any ideas? also when i try ubuntu all is well but when i install it fails at the boot loader install

---

### Post by undershepherd1 on 2015-05-09
kaitlin:
If your laptop is a recent one (made within the last 4-5 years), see this thread [http://ubuntuforums.org/showthread.php?t=2277217](http://ubuntuforums.org/showthread.php?t=2277217). 
Rad especially the links oldfred has in his posts concerning UEFI and Windows 8.1 computers.

---

### Post by kaitlin3 on 2015-05-09
i think mine was released back in 2009  because it has a windows vista sticker on it also i am able to boot from usb if that helps

---

### Post by yancek on 2015-05-09
Post some details on your hardware such as processor, RAM.  Did you check the minimum hardware requirements at the Ubuntu site before installing?  Did you leave the default option to install the bootloader to the MBR?


[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by grahammechanical on 2015-05-09
What install option are you choosing? Install Alongside? Something Else?

If you are using the Something Else option, what file system are you choosing? Ext4? If we choose btrfs as the file system then we will get a failure to install Grub unless we have a small amount of unallocated space at the front of the hard disk.

Regards.

---

### Post by RobGoss on 2015-05-09
Hello and welcome, first how are you creating your USB stick and what program did you use?

make sure you're using the correct version of Ubuntu meaning 32 bit or 64 bit.

---

### Post by sammiev on 2015-05-09
Hello and welcome, a lot of good info posted above.

It sure would be great to have your computer specs as well as a image of your partitions. ( Gparted does a great job )

When you downloaded the ubuntu iso did you check the download with [MSD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") to see if the checksum matched?

Can you run a live session from the USB when you select "Try Ubuntu"?

---

### Post by kaitlin3 on 2015-05-10
intel core 2 duo T9600 at 2.8Ghz 4 gig ddr2 ram mobility at 3650 256 meg dedicated hp elitebook 8530p laptop also im using 64 bit ubuntu install as for usb i cant remember what guide i used

edit i can run live install from usb and i can try ubuntu from the live install it just crashes at the install boot loader also im using full erase and install on a fresh clean empty 500gig hard drive

---

### Post by kaitlin3 on 2015-05-10
------------------
System Information
------------------
Time of this report: 5/9/2015, 23:39:11
       Machine name: KAITLIN-PC
   Operating System: Windows 7 Home Premium 64-bit (6.1, Build 7601) Service Pack 1 (7601.win7sp1_gdr.150316-1654)
           Language: English (Regional Setting: English)
System Manufacturer: Hewlett-Packard
       System Model: HP EliteBook 8530p
               BIOS: Default System BIOS
          Processor: Intel(R) Core(TM)2 Duo CPU     T9600  @ 2.80GHz (2 CPUs), ~2.8GHz
             Memory: 4096MB RAM
Available OS Memory: 4060MB RAM
          Page File: 7411MB used, 771MB available
        Windows Dir: C:\windows
    DirectX Version: DirectX 11
DX Setup Parameters: Not found
   User DPI Setting: Using System DPI
 System DPI Setting: 96 DPI (100 percent)
    DWM DPI Scaling: Disabled
     DxDiag Version: 6.01.7601.17514 32bit Unicode


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
          Card name: ATI Mobility Radeon HD 3650
       Manufacturer: Advanced Micro Devices, Inc.
          Chip type: ATI display adapter (0x9591)
           DAC type: Internal DAC(400MHz)
         Device Key: Enum\PCI\VEN_1002&DEV_9591&SUBSYS_30E7103C&REV_00
     Display Memory: 2024 MB
   Dedicated Memory: 249 MB
      Shared Memory: 1774 MB
       Current Mode: 1280 x 800 (32 bit) (60Hz)
       Monitor Name: Generic PnP Monitor
      Monitor Model: LP154WX4-TLAB
         Monitor Id: LPL3D01
        Native Mode: 1280 x 800(p) (59.976Hz)
        Output Type: Internal
        Driver Name: aticfx64.dll,aticfx64.dll,aticfx32,aticfx32,atiumd64.dll,atidxx64.dll,atiumdag,atidxx32,atiumdva,atiumd6a.cap,atitmm64.dll
Driver File Version: 8.17.0010.1103 (English)
     Driver Version: 8.911.4.1000
        DDI Version: 10.1
       Driver Model: WDDM 1.1
  Driver Attributes: Final Retail
   Driver Date/Size: 1/21/2012 23:18:30, 892416 bytes
        WHQL Logo'd: Yes
    WHQL Date Stamp: 
  Device Identifier: {D7B71EE2-D6D1-11CF-8C73-1846ADC2C835}
          Vendor ID: 0x1002
          Device ID: 0x9591
          SubSys ID: 0x30E7103C
        Revision ID: 0x0000
 Driver Strong Name: oem66.inf:ATI.Mfg.NTamd64.6.1:BR_132536_ati2mtag_M76:8.911.4.1000:pci\ven_1002&dev_9591&subsys_30e7103c
     Rank Of Driver: 00E60001
        Video Accel: ModeMPEG2_A ModeMPEG2_C

---

### Post by mörgæs on 2015-05-10
From the live boot a good first step is to take a look at the SMART data.

---

### Post by kaitlin3 on 2015-05-10
how do i look at the smart data

---

### Post by william_smith3 on 2015-05-10
I have an HP laptop as well and there are a few problems that most of these guys understand but without being there they can't give a proper answer. I searched and searched for an answer (I'm a novice FYI) and through trial and error I was able to boot to ubuntu - well actually lubuntu is my flavor of choice.

Sorry if I over explain. I know you know most of this but it may be helpful to other HP users.

Things to check for on your HP.
32 or 64 bit? 
Go to control panel and select "System..." If a list comes up press "System" again. This will bring up a page that tells you what hardware you have. It also tells you if it is 64 bit. I say this because it took me a while to figure this out. I wanted 32 bit because I thought I could use a thumb drive on any of my computers but as it turns out the install for my HP had to be 64 bits.

Once you know that:

You'll need to make your image on a CD or on USB.  This is the image you will use to boot from so it's important to know which, I prefer thumb drive, because you will be changing the boot order in bios to the image drive and the application you'll use I don't know enough about to say it does CD's.

That's probably the stuff you know. Now the harder part. I see in the forums most people recommend pendrivelinux ... I can't figure that one out so I downloaded Rufus 2.1.exe. Search in Google and it will show up - it's freeware. This application makes the process much easier because your computer boots UEFI not EFI. This process is the least invasive of the bios. You will change nothing but the boot order so if you've changed anything there, set it back to defaults. This should have safeboot enabled, legacy disabled.

Open Rufus and tell it what version you're installing, and give it at least 4096 MB in the drop down. *Note - I used a USB for this and I don't know how or if it will do a CD. Sorry for that but I feel your pain with the HP. The HP boot manager is a beast and tries its best to load windows.  IMPORTANT - there's a drop down menu in rufus that has 2 options for MBR and 1 for GPT. Choose GPT option. GPT will allow the drive to boot on an HP.

Click start after choosing your options. The way you know it's done is by the green bar being filled and it says finished or complete.  It is done just press close, or exit.  This drive/CD will be able to boot your HP into Ubuntu install.

If you have not yet been to bios, go there and make sure you have your preferred drive selected as the first boot drive. In my bios I went down the list and pressed F5 to make the selection go down the list and F6 made it go up.

Save and exit bios. after changing the boot order. The computer will restart and should boot...well, take you to a window with options you've seen before. From there install and it should load because rufus allowed you to make a UEFI version with GPT - don't know if I'm writing that correctly or not (remember, I novice) but the main idea here is making an HP bootable drive/CD

I probably used improper working and explained things you already know but the key here is:
Same bit ubuntu image as computer - 32 or 64
Use Rufus to make live image and select GPT
Change boot order
All should work fine - If not, LMK

It is frustrating with the HP's. Everything has to be just so-so to work.  Good luck and LMK either way - worked or not

---

