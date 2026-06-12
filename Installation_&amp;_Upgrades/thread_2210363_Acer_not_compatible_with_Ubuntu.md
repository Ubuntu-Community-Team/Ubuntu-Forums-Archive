---
title: "Acer not compatible with Ubuntu??"
date: 2014-03-10
forum: Installation &amp; Upgrades
---

### Post by Danniel90 on 2014-03-10
Hello, im new at ubuntu forum and it's the second time i use ubuntu, first time on my desktop pc, and now i want to install Ubuntu on my laptop aswell, which i just bought one week ago.
 It's a laptop Acer Aspire E1-522 series (AMD), it comes with Windows 8.1 preinstalled, and UEFI aswell, like all laptops on stores, problem begins during installation of Ubuntu, version 13.10 (i dont think that's the cause), without deleting Windows 8.1, i tried to install Ubuntu within a partition i had previously created in Windows, i ran ubuntu installation from dvd, but during installation i always get a blank screen after these lines:

-Starting LightDM Display Manager                                                     [OK]
-Stopping Send? an event to indicate playmouth is up                           [OK]
-Starting startper bridge for notification of upstart job start/stop            [OK]
-Stopping startper bridge for notification of upstart job start/stop           [OK]
-Stopping CPU interrupts balancing desmon?                                        [OK]
-Starting startper bridge for notification of upstart job start/stop            [OK]
-Stopping startper bridge for notification of upstart job start/stop           [OK]

after this, many lines of codes appear so fast, and then the screen goes blank. Here is the link to the video i recorded:

[http://www.youtube.com/watch?v=rnM7VGW59E4&feature=youtu.be](http://www.youtube.com/watch?v=rnM7VGW59E4&feature=youtu.be)

After i tried twice, i decided to remove Windows 8.1 from Windows 7 installer, i cleaned the hard disk, then i installed Windows 7, after that i tried once more to install Ubuntu, Secure Boot disabled and Legacy Mode aswell, this time i tried to install it with nomodeset, but installation stops and screen goes blank again, i asked a technician in informatics and he told me is not possible to install any current verion of Ubuntu, maybe new versions from 2015 on, i also called Assus support center, and they say it's not problem with Acer since i could install Windows 7, so they say it's problem with Linux.
I would appreciate so much any information about it, if someone else cannot install Ubuntu either or have the same problem, if new Ubuntu versions will be able to run onto my laptop, i spent more than 400€ on this laptop to use Ubuntu on it because i don't like Windows 8.
Thanks in advice any help is welcome.

Pd: Sorry for my grammar and composition, i am not english native.

---

### Post by oldfred on 2014-03-10
Did you install Windows 7 in UEFI mode.
If not it does not correctly convert  a gpt partitioned drive to MBR(msdos). So a Windows issue.
LInux tools see both MBR & gpt and do not know what you have.

You can convert a Windows 7 DVD to UEFI by copying to a flash drive and updating it somehow??
But you can remove the backup gpt partition table that Windows did not remove.

 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

If drive is MBR, you can only boot in BIOS mode like all the other computers for the last 35 years. 
Some with UEFI on Acer have gotten it to work.

      
 How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Added new msata drive post #3
[http://ubuntuforums.org/showthread.php?t=2174844](http://ubuntuforums.org/showthread.php?t=2174844)

---

### Post by Danniel90 on 2014-03-10
Thanks for reply. No, i installed Windows 7 in Legacy Mode and just after deleting everthing inside my hard disk, i removed all from cmd.exe of Windows 7 installer: diskpart > ..> clear all, i was then avaialble to disable gtp mode of my partition. Therefore i can't boot from usb, it says device mising, restart computer etc,,. I am not so experienced for last recommendations of you, i will take a look on those posts you posted, and i will try to make it works, again thanks a lot for your reply ;)

---

