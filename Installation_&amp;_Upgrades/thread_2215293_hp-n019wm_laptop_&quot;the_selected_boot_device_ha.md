---
title: "hp-n019wm laptop &quot;the selected boot device has failed&quot;"
date: 2014-04-05
forum: Installation &amp; Upgrades
---

### Post by levi4 on 2014-04-05
I've been trying to install Ubuntu to my hp-n019wm laptop, and I keep getting the error "the selected boot device has failed". I have tried installing via USB using pen drive linux's tool, and by burning the install files to a disk with powerISO. I get the same error each time.

Here's a link to the laptop, I'm not sure if it's relevant but the bios version is f.07

[http://www.walmart.com/ip/HP-Sparkling-Black-15.6-Pavilion-15-n019wm-Laptop-PC-with-AMD-A6-5200-Accelerated-Processor-4GB-Memory-750GB-Hard-Drive-and-Windows-8/28503694](http://www.walmart.com/ip/HP-Sparkling-Black-15.6-Pavilion-15-n019wm-Laptop-PC-with-AMD-A6-5200-Accelerated-Processor-4GB-Memory-750GB-Hard-Drive-and-Windows-8/28503694)

---

### Post by oldfred on 2014-04-05
If you have Windows 8 pre-installed, you have UEFI with secure boot.
You must turn off fast boot and usually better to turn off secure boot.
If secure boot is on, only systems in secure boot mode will be offered to boot.
You also want to have UEFI for Ubuntu to easily dual boot, not legacy/CSM/BIOS boot mode. Although some systems only install in BIOS move and you have to use Boot-Repair to convert.

       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you have it installed run the BootInfo report in Boot-Repair and post link. 

 With UEFI If you run any fixes from Boot-Repair do not say yes to 'buggy' UEFI fix. That is only for systems where UEFI has been modified by vendor to only allow Windows to boot. Only if we confirm your system only boots Windows may we want to use that fix.

Different model HPs, but UEFI may be similar, so similar issues?

 HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)

---

### Post by levi4 on 2014-04-06
So I went in and disabled secureboot in the bios, and disabled fastboot in the windows 8 power settings, and I'm still getting the same error (actually it only gives me the error when I select from windows to boot from disk, when I turn off and restart the computer it just skips over it entirely and goes straight to windows, even though I have the disk in and have my cd drive at the top in the bios boot priority)

I don't want to dual boot or anything, I want windows 8 gone, I'm not really sure what UEFI is but if I don't plan on dual booting I don't need to worry about it right?

And how can I install and run the "bootinfo report" if I can't boot to ubuntu? It looks like this is an ubuntu feature. 

Anyways thanks for the help, I hope I can get this working, or else I'll probably try and install a previous version of windows or return the laptop. This windows 8 UI really pisses me off

Edit: So I just tried booting with a windows 7 disk and it took, not sure if this is relevant or not

Edit: I just tried booting from the ubuntu disk I burned on my desktop and it didn't take, tried booting from windows 7 disk and it did, I think at this point I may have just messed something up when I burned the installation disk. I'm going to try booting from the bootable flash drive tomorrow and see if that works

3rd Edit: Went back and tried installing windows 7 64 bit on the laptop and it didn't end up working, I went to amazon and saw the reviews for the laptop. 2 out of 3 buyers said that you won't be able to install linux on it. I'm thinking I might just have to return the damn thing
[http://www.amazon.com/Hewlett-Packard-15-d017cl-Quad-core-Processor/product-reviews/B00HNWX43S/ref=dp_top_cm_cr_acr_txt?showViewpoints=1](http://www.amazon.com/Hewlett-Packard-15-d017cl-Quad-core-Processor/product-reviews/B00HNWX43S/ref=dp_top_cm_cr_acr_txt?showViewpoints=1)
Seems like HP is trying to force you to use that god awful excuse for a desktop operating system windows 8

---

### Post by oldfred on 2014-04-06
Some of the HP's have been and issue. 
And Microsoft has made it more difficult for a new user as with UEFI and secure boot the entire install process have several extra levels of complexity.
But some vendors seem to make it easier to change settings & install Linux than others.

If you are using a Windows 7 install DVD, that will only install in BIOS/Legacy/CSM mode not UEFI. But it does not correctly convert from gpt partitioning which is required by UEFI to MBR(msdos) partitioning which is required by Windows for BIOS booting.
You can convert a Windows 7 DVD to flash drive and install some minor changes to make it a UEFI installer.
Ubuntu will install to gpt or MBR to boot with BIOS.
And if BIOS booting it is just like any old system, no UEFI nor secure boot. But non of the advantages of new UEFI like quicker booting, gpt partitioning where there is no primary, extended nor logical partitions and a few others. 
In the future new hardware may only work with UEFI as there will not be old BIOS drivers, but current systems seem to all work either way.

If you cannot even boot Ubuntu in BIOS mode then I would suspect the DVD or flash drive, or download was not correct. A few do have issues with certain brands of flash drives, or certain USB ports on computer. And some have to enable USB booting separately in UEFI/BIOS, but if Windows boots it must be enabled.

---

### Post by levi4 on 2014-05-04
Sorry I know my reply is a little late, but thanks for helping me out. I ended up having the laptop returned/exchanged at costco, and am now running xubuntu from a desktop

---

