---
title: "Unable to boot Ubuntu on Lenovo via DVD"
date: 2014-01-23
forum: Installation &amp; Upgrades
---

### Post by brantesimon on 2014-01-23
Hi y'all. 

First time user here, wanting to get in to Ubuntu and I'm trying to install it on my new laptop that I got just today so I'll learn everything while using it for what I usually do. 

Slight problem though: I can't get it to boot properly. I have managed, by screwing around in the BIOS a bit, to get to the screen where I can choose wether to install, just try etc etc. but when I press either Install or Try Ubuntu it just turns to a black screen with a white line blinking up in the left corner. I have a friend who is able to help me, but not until after the weekend and I really want to get going as fast as possible. 

The computer is Lenovo Essential B5400 with Windows 7 preinstalled. 
Intel core i5-4200M @2.50 GHz 
4 GB RAM
Intel HD graphics 4600 (I think) 

Thank you!!

---

### Post by tfrue on 2014-01-24
You may need to disable Secure boot, Fastboot, and enable Legacy boot in order to get any where and that is all configured by BIOS.

---

### Post by fantab on 2014-01-24
> **brantesimon said:**
> 

First time user here, wanting to get in to Ubuntu and I'm trying to install it on my new laptop that I got just today so I'll learn everything while using it for what I usually do. 

Slight problem though: I can't get it to boot properly. I have managed, by screwing around in the BIOS a bit, to get to the screen where I can choose wether to install, just try etc etc. but when I press either Install or Try Ubuntu it just turns to a black screen with a white line blinking up in the left corner. I have a friend who is able to help me, but not until after the weekend and I really want to get going as fast as possible. 

The computer is Lenovo Essential B5400 with Windows 7 preinstalled. 
Intel core i5-4200M @2.50 GHz 
4 GB RAM
Intel HD graphics 4600 (I think) 


Are you sure you are using Windows 7? Most of the new laptops come with Windows 8.

What happens when you 'Try Ubuntu (without installing)"? If you are able to boot Ubuntu without installing then Open Terminal [ctrl+alt+T], run the following commands and post its output here:

```
sudo parted -l
sudo fdisk -l
```

---

### Post by Bucky Ball on 2014-01-24
Welcome. When you get to the screen with 'Try Ubuntu' 'Install Ubuntu', hit F6, choose 'nomodeset', proceed to 'Try Ubuntu'. Any luck?

Before installation you need to get into the BIOS and check whether Windows is booting in UEFI or not. This will make a considerable difference to how you go about installing Ubuntu.

---

### Post by brantesimon on 2014-01-24
Yeah I have disabled secure boot, but I don't really know where to find fastboot to disable that. My BIOS for some reason looks different from all the ones I've seen in guides on how to change it... 

> Are you sure you are using Windows 7? Most of the new laptops come with Windows 8.


Yes, I am sure I am using win7. However, it said where I got the computer that it had win8 as a "secondary" OS. I don't know what this means, and I have seen no mention of win8 in any way when using the computer. 

> What happens when you 'Try Ubuntu (without installing)"?

Nothing. Same as when I try to install it: black screen with blinking white line top left. 

> When you get to the screen with 'Try Ubuntu' 'Install Ubuntu', hit F6, choose 'nomodeset', proceed to 'Try Ubuntu'. Any luck?

Nope, same as before...

---

### Post by fantab on 2014-01-24
See if your windows is hibernating, if it is then disable hiberantion and shutdown Windows....

EDIT: It could also mean that you have either a bad 'burn' or a bad download.
If you have USB drive burn ubuntu.iso to it after you have run [MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM") or [SHA256Sum Check]("https://help.ubuntu.com/community/HowToSHA256SUM") on the downloaded .iso. If the sums don't match redownload ubuntu.

---

### Post by brantesimon on 2014-01-24
> See if your windows is hibernating, if it is then disable hiberantion and shutdown Windows....

How do I find out if it's hibernating? Is it like "sleep mode"?

---

### Post by fantab on 2014-01-24
The the tutorial here: [http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html](http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html)

---

### Post by Bucky Ball on 2014-01-24
You need to switch fastboot off by actually booting into Win and doing it via the software:

[http://www.pcmag.com/article2/0,2817,2417361,00.asp](http://www.pcmag.com/article2/0,2817,2417361,00.asp)

---

### Post by brantesimon on 2014-01-24
I've tried about everything and still nothing except a black screen, no matter what I choose. I've tried to see if there is some CD defect from the boot-program but it also gives me a black screen. 

I'm going to try to get a USB stick and attempt installation that way I guess.

---

### Post by oldfred on 2014-01-24
Often nomodeset works for video issues.
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

But the newest Intel video often needs other boot mode settings. See ubfan1 suggestions above.
There may be UEFI/BIOS settings also required.
This was a Dell but they say the issue is common to all Intel systems.
      
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
> Running in legacy BIOS mode or in UEFI mode both work, but for now  you'll need to enable "Legacy Option ROM" in the BIOS if you're running  in UEFI mode because of the display's backlight. This is because of an  issue with the Intel i915 driver that currently affects several systems  from many vendors. If you don't enable this BIOS option, the backlight  will be stuck at the lowest setting in Linux. 

This user added all the options at once. I would have expected them to conflict and really should  not use all at once.
      
 [http://ubuntuforums.org/showthread.php?t=2191814](http://ubuntuforums.org/showthread.php?t=2191814)
> acpi_backlight=vendor dell_laptop.backlight=0 pcie_aspm=force i915.i915_enable_rc6=1 drm.vblankoffdelay=1 i915.semaphores=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 vt.handoff=7 quiet splash elevator=deadline acpi_osi=linux



---

### Post by brantesimon on 2014-01-24
Alright, so I've basically tried everything it feels like. I've tried to make all the necessary changes to BIOS (however I am not sure of what the **** I am doing there really), I've made to DVDs and one USB, I did the MD5sum(or what it's call) and it checks out... Still just a black screen... Tiresome.

---

### Post by bertan2 on 2014-01-24
Sometimes new laptops include hardware that is only supported in a recent Linux kernel. Have you tried the latest daily build of Ubuntu 14.04? Here is the link to the "Trusty Tahr" daily images: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by Bucky Ball on 2014-01-24
It is not a good idea to direct a new user to install an unreleased and testing version of Ubuntu. ;)

---

### Post by fantab on 2014-01-25
> **brantesimon said:**
> Alright, so I've basically tried everything it feels like. I've tried to make all the necessary changes to BIOS (however I am not sure of what the **** I am doing there really), I've made to DVDs and one USB, I did the MD5sum(or what it's call) and it checks out... Still just a black screen... Tiresome.

Does your comp have dual graphics or [Hybrid Graphics]("https://help.ubuntu.com/community/HybridGraphics")? 

Can you boot Windows? If yes, then show a screenshot of ALL your HDD's, SSD's etc with the 'Windows Disk Management Utility'.

---

### Post by brantesimon on 2014-01-25
I downloaded Ubuntu 13.10 and it seems to work now. I haven't installed it yet but the "Try Ubuntu" feature was at least working. Thank you for all your help!

---

