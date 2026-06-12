---
title: "new pc build same problem"
date: 2016-09-09
forum: Installation &amp; Upgrades
---

### Post by bobipod on 2016-09-09
So i tried updating to 16.04 and my pc / installation crashed part way through.  This meant my original hdd has part of an o/s and is currently useless. I tried reinstalling via the usb from canonical but all i get is errno 5 input/output error clean disk.


Brand new hdd and motherboard and memory came today so i built the new pc. Guess what. Yep same error message. I tried running 
Ubuntu off the usb stick in order that i could try and download from the website and install that way. No good as, although it is connected by cable to the internet, no pages can be shown as if it isn't connected.

I've tried to format the hdd while running ubuntu from the usb but it does nothing.

Any suggestions?

---

### Post by oldfred on 2016-09-09
Does live installer in live mode work without any issues.
What are specs of system?
Motherboard, video card/chip?
Are you using UEFI or BIOS? New systems are all UEFI, but can use the 35 year old BIOS configuration with CSM emulation.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by bobipod on 2016-09-09
I currently have the hdd running a format. Once it completes i will look at bios and report the findings and spec.

---

### Post by bobipod on 2016-09-10
Motherboard is gigabyte GA 970 3.5ghz?
4gb ddr3 memory

I have tried various formations of the uefi / legacy but still no joy. 

Again trying Ubuntu via the USB gives me no internet even though the cable is in and confirmed connected.

I'm now trying to overcome why I no longer have a keyboard working. I know this fine.

---

### Post by oldfred on 2016-09-10
You need IOMMU setting in UEFI and soft setting as boot parameter.

 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by bobipod on 2016-09-10
No help as I can't open a terminal window.

---

### Post by oldfred on 2016-09-10
Neither of those are Ubuntu terminal Windows.

First setting is in UEFI for motherboard.
And second is a grub boot parameter. 
You can manually add as you boot until you get into system. 

Only then you may need terminal.
Then if need be you can edit grub's configuration file to make it permanent.

---

### Post by bobipod on 2016-09-10
When I found the iommu I had option of enable disable.  When I save and exit and then try to run from the USB stick I just get a full screen of the same error message, written on command lines.

Clearly myself, motherboard and Ubuntu are not doing something right.

So starting with me, I'm no programmer, if I go into BIOS and enable the iommu support do I then save\exit?

The system does an auto soft reboot what is my next step?

Do I allow the crash to happen? Then edit using the mentioned command?

---

### Post by oldfred on 2016-09-10
I have seen conflicting info on whether you turn on or off IOMMU in UEFI.
But then when initially booting you must add the iommu=soft just like you would nomodeset boot parameter that is for nVidia cards.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by bobipod on 2016-09-11
I'm going to need to simplify this even more. I'm confused. I thought grub was a terminal.

As i have no os on my system, just on the usb stick, how do i get into a grub window to edit?

Once that command has been entered what is the correct sequence to then move onto nomodeset? Then correctly mpve on to the successful instal?

---

### Post by bobipod on 2016-09-11
Update. I used iommu soft in grub and booted. I now have usb 2.0 ports and ethernet working.

I booted into try ubuntu from the usb. After the umpteen repeat error line msgs it loaded.

I have tried installing ubuntu whilst in the try me now mode but it does nothing.

I'm not sure what nomodeset is. I'm certainly not doing something which switches off fans and cooks my mb.

I'm not understanding nomodeset and what exactly i need to type in the grub edit for quiet splash (which i've found).

---

### Post by bobipod on 2016-09-11
So it would appear what i'm doing is making any difference.

The only thing i have managed, by enabling iommu, is that my usb and ethernet works.

I've tried to edit the splash code but nothing happens. Without a way to save or boot all it does is lose the command.

Same if i try to add a command line of iommu soft. It doesnothing as there is no way to save or boot from it.

Trying to download and install using terminal doesn't work as it just tries to save and install to the usb.

After 8 years i think it's time to say goodbye to ubuntu. Which is a shame as i've enjoyed it thus far.

---

