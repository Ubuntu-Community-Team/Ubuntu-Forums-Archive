---
title: "Cannot boot from Kubuntu usb stick"
date: 2023-12-07
forum: Installation &amp; Upgrades
---

### Post by oilhat on 2023-12-07
I recently acquired a dell optiplex 5050 with Windows 10.  It uses efi.  I have a Kubuntu 22.04 on a usb stick that I created on another computer with Kubuntu startup disk creator.  I cannot get the dell to boot from the usb stick.
 
 The computer with the Kubuntu startup disk creator does not use efi.  (Is it legacy bios then?)
 
 I have used the usb stick to boot on two other computers and it worked fine.  One of them uses legacy bios (not efi), and probably the second computer also, since it is older.
 
 On the dell with efi, I have entered the bios and disabled secure boot.  I have also gone into the windows settings and the advanced options or whatever it was and selected boot from USB.  The only options available is the Windows boot loader.  The usb stick is inserted, but it does not show up as a boot option.  It seems that it is not recognized. 

 Is there a difference between a usb boot stick for efi and legacy bios?  Does the boot stick need to include an efi partition?

 Many of the solutions that I have found include instructions to create a usb boot stick.  Rufus seems to include options for MBR or GPT.  And efi or bios.  The instructions in the ubuntu tutorials say to just use the defaults.  Here is the link.    [https://ubuntu.com/tutorials/create-a-usb-stick-on-windows?ref=techbruh.net#9-installation-complete](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows?ref=techbruh.net#9-installation-complete)

Do I need to recreate the Kubuntu usb boot stick with Rufus or Etcher, or is there a different problem?  Does the boot stick need to be created on the same computer that I want it to boot from?  (The dell 5050 with efi.)

---

### Post by guiverc on 2023-12-07
If you *clone* an Ubuntu ISO (*which includes flavors like Kubuntu*) to media; it will boot and install on 

- legacy hardware (pre-uEFI)
- uEFI hardware
- uEFI hardware with *Secure boot* enabled

You can use ISO writing software to reformat the ISO (*during write*) so it will boot only on a specific one of those, but if *cloned* without change it'll boot & install on all.

You mention Kubuntu 22.04 LTS, but not which 22.04; ie. 22.04, 22.04.1 or 22.04.2 (*all of which now have revoked keys on them & may not boot on updated hardware using Secure-uEFI*) OR 22.04.3 media. This may or not be your issue (*ie. are you using updated media? or an ISO with now revoked key?*) but you weren't specific as to what 22.04 ISO you used.

---

### Post by oilhat on 2023-12-07
Ubuntu 22.04.3 LTS

```
[FONT=monospace][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lsb_release -a [/COLOR]
No LSB modules are available. 
Distributor ID: Ubuntu 
Description:    Ubuntu 22.04.3 LTS 
Release:        22.04 
Codename:       jammy

[/FONT]
```

---

### Post by fullscale4me on 2023-12-08
[SIZE=3][SIZE=2]From page 46 of your PC's User Manual [https://dl.dell.com/topicspdf/optiplex-5050-desktop_owners-manual_en-us.pdf](https://dl.dell.com/topicspdf/optiplex-5050-desktop_owners-manual_en-us.pdf)
[/SIZE][SIZE=2]
It seems that pressing F12 at boot (it will get slightly bolder onscreen after your keystroke) should give you one, possibly two boot choices for your USB. 

For best result ensure that your USB is inserted _prior_ to powering on the PC.
[/SIZE]
**Boot Sequence**[/SIZE]

Boot Sequence allows you to bypass the System Setup–defined boot device order and boot directly to a specific device (for example:
optical drive or hard drive). During the Power-on Self Test (POST), when the Dell logo appears. you can:

• Access System Setup by pressing F2 key
• Bring up the one-time boot menu by pressing F12 key

The one-time boot menu displays the devices that you can boot from including the diagnostic option. The boot menu options are:

• Removable Drive (if available)
• STXXXX Drive

NOTE: XXX denotes the SATA drive number.

• Optical Drive (if available)
• Diagnostics
[B]
NOTE[/B]: Choosing Diagnostics, will display the ePSA diagnostics screen.
The boot sequence screen also displays the option to access the System Setup [Boot order] screen.

---

### Post by oilhat on 2023-12-08
I inserted the Kubuntu 22.04.3 usb stick and pressed F12 on startup.  The results don’t match what you copied from the dell users manual.  Here is the menu that I got.

 
 
 ```

 
 Boot mode is set to : UEFI;  Secure Boot:  Off

 
 
 UEFI BOOT:

     Windows Boot Manager

     Windows Boot Manager
 OTHER OPTIONS:
     BIOS Setup
     BIOS Flash Update

     Diagnositics

     Change Boot Mode Settings
```

 
 
 I Selected Change Boot Mode Settings

 ```

 
 CHANGE BOOT MODE TO:

     1)  Legacy Boot Mode, Secure Boot OFF

     2)  UEFI Boot Mode, Secure Boot ON
```

 
 
Then I Selected Legacy Boot Mode, Secure Boot OFF

 
 
 ```
Boot mode is set to:  LEGACY;  Secure Boot:  OFF

 
 
 LEGACY BOOT:

     PO:  KingFast

 UEFI BOOT:

     Windows Boot Manager

     Windows Boot Manager

 OTHER OPTIONS:

     BIOS Setup

     BIOS Flash Update

     Diagnositics

     Change Boot Mode Settings
```

 
 
Then I Selected PO:  KingFast

 
 
 ```
Selected boot device failed.  Press any key to reboot the system.
```

It seems that PO: KingFast is the SSD.  The usb stick is not on the menu anywhere.

I also booted into windows 10 and I opened windows explorer.  It seems like the usb stick is recognized there but the filesystem is not readable by windows. As I might expect.  

Any other advice?

---

### Post by tea for one on 2023-12-08
Page 49 of the manual:-
USB Configuration Allows you to enable or disable the integrated USB controller for:
• Enable Boot Support
• Enable Front USB Ports
• Enable Rear USB Ports

Are the USB ports enabled for Boot?

---

### Post by oldfred on 2023-12-08
For most systems you only want UEFI boot, do not enable Legacy boot. Although a few older systems had UEFI settings under Legacy boot which seems backwards as Legacy/BIOS/CSM is a sub-set of UEFI.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

You should be able to turn on UEFI, but turn off Secure Boot.
But Ubuntu should install with Secure boot on or off.

Boot mode in UEFI settings is often just for installed system.
Most UEFI then have options  to boot USB flash drive. One should be UEFI and one not UEFI, if secure boot off. 
If Secure boot on & USB boot allowed, then only Secure Boot install will be the option.

---

### Post by oilhat on 2023-12-08
Boot support was not enabled!  Whew!  It boots now. 
 
 Page 49 of the manual.  Like Tea for One said.
 
 
 I have spent several hours figuring this out.  Thank you for your help.   
 
 
 Can I mark this thread as solved?  I don’t see it on the page anywhere.  I will keep looking.

---

### Post by #&amp;thj^% on 2023-12-08
Glad to hear this, and in your first post>>Top Right>>Thread Tools..Mark as Solved

---

