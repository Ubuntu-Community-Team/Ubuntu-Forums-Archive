---
title: "want to install 16.04 on Dell XPS 8910, but I have an Nvidia GE Force-GTX video card"
date: 2018-04-16
forum: Installation &amp; Upgrades
---

### Post by Angela_C.Murphy on 2018-04-16
I have a relatively new Dell XPS 8910 desktop, Core I7 processor, 16 Gb memory, 2 TB hard drive.  It now runs Windows 10 Pro, but I want to add Ubuntu 16.04 and have a dual boot.  The problem is the video card -an NVidia GeForce - GTX 750 Ti with 2 Gb memory.  I have heard that there are problems installing Ubuntu with this card.  I need all the help I can get. I am 79 years old, not a computer expert and have recently been ill. If anyone can spare the time to explain to me the steps I should follow for the installation, I would be eternally grateful. My husband and I really need Ubuntu.

Thanks in advance for any assistance.
AC Murphy

---

### Post by dino99 on 2018-04-17
in the past i have used a 750 card too with ubuntu, without huge trouble (that happen when the driver is not yet ready, but now its no more an issue) (working with nvidia-340 driver for that card)

But you say its a relative new hardware, so you might install also a new OS, instead of an old one.
18.04 which is a LTS release, like 16.04 is/was, is quite ready to be released, and is stable.

[http://cdimage.ubuntu.com/ubuntu/releases/18.04/beta-2/](http://cdimage.ubuntu.com/ubuntu/releases/18.04/beta-2/)

---

### Post by oldfred on 2018-04-17
If new hardware and Windows 10 it will be UEFI with gpt partitioning.
So you need to boot Ubuntu live installer in UEFI boot mode from UEFI boot menu. It should show two boot options, one clearly UEFI and the other just the flash drive name or label and that is BIOS boot.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You should get grub menu and want to add a boot parameter nomodeset to allow graphics to work. Once installed you will only need nomodeset on first boot or until you install the proprietary nVidia driver from Ubuntu repository (not directly from nVidia).

       
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 

See link in my signature below - 9 "easy" steps.
Actual only really difficult step for me with my only Windows system and Dell was backup. Dell wanted backup, Windows wanted backup and I did a full image backup with macrium. Backups took 3 days, but had to run to store for more DVDs & flash drives.

 [http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp) 

After backups, shrink Windows using Windows tools, reboot to run chkdsk, make sure fast start up is off. Best in UEFI to have fast boot off to make sure you have time to press keys to choose UEFI boot or get into UEFI to change settings. I also suggest updating UEFI from Dell. Many changes due to CPU virus issues for all brands of CPUs.
Then actual install of Ubuntu took less than an hour.
Then create plan for backups of Ubuntu.

---

