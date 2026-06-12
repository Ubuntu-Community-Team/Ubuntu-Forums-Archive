---
title: "Cannot Install Ubuntu 12.10"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by joeturtle on 2012-11-21
Hello everyone. For the past few days, I've been trying to get my new Windows 8 computer to dual boot with Ubuntu 12.10 64bit. And I'm having no such luck getting it to work, unfortunately.

I've tried using Wubi. But unfortunatly, it does not seem compatible with UEFI. (Or at least, that is that the internet has led me to believe.)

And I've also tried using a LiveUSB and LiveCD to install Ubuntu, as it seems that *should* work...but each time I attempt to do so, I get a black screen after I select either Try Ubuntu or Install Ubuntu. I have no idea what I'm doing wrong, or how to rectify what I am doing wrong. Please help.

If you need any information, please feel free to ask.

---

### Post by SeanIM on 2012-11-21
Just giving it a whirl here, but have you tried the good old fashion way of just burning a regular CD and trying to install?

---

### Post by Bootiefulpig on 2012-11-21
Use Boot Repair. It will organize your partitions and help the boot process. You need 6 partitions. 2 bootable partitions, 2 swap partitions and 2 Operating System partitions. Each one from windows and ubuntu. Make sure that both Operating Systems have a FAT32 format.

---

### Post by joeturtle on 2012-11-22
> **SeanIM said:**
> Just giving it a whirl here, but have you tried the good old fashion way of just burning a regular CD and trying to install?

Yes. As I have mentioned above, I've tried using both a USB and a CD to install Ubuntu. I've tried multiple downloads of the iso file as well. It all leads to a blank screen. 

> **Bootiefulpig said:**
> Use Boot Repair. It will organize your partitions and help the boot process. You need 6 partitions. 2 bootable partitions, 2 swap partitions and 2 Operating System partitions. Each one from windows and ubuntu. Make sure that both Operating Systems have a FAT32 format.

If I'm not mistaken, Boot Repair is a linux only program. It would indeed be helpful if I could somehow manage to even install Ubuntu.

---

### Post by claven123 on 2012-11-22
Do you hear the start up sounds, the music ect.... many issues are with the graphics and video cards when you install linux.  Sometimes you need to run nomodeset and you will see the video.

Boot-repair is a good idea, but that is for the obvious boot issues, which you may or may not have and issue with.  (most likely you do... but that is another story).

Do you see GRUB or any options, do you see the regular splash screen, the point at which the BIOS is loading?  Do you get any errors at boot, do you load win8, or linux or neither.

The live USB should be fine.  Sometimes the download is corrupt, you can run a check on the files on the USB drive.  Or, just re-down load them.

Oh, sorry, I miss read your OP....  just re download the file and or check the files on the USB.   If you haven't installed anything you don't need boot-repair yet.  Your download files might be corrupt.

I'm not sure about the Fat32....  I've heard ext4 but that is another story.

Did you set up your partitions?  You will most likely need to shrink one of your partitions anyway.... and create the Linux partition and swap partition.  You should already have the win 8 partitions.

Hope this helps some.... google and search here are your friends.

D

---

### Post by YannBuntu on 2012-11-24
Hello

Can you get to the Advanced boot menu?
[https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)

If yes, try to add the 'nomodeset' option.
If no, try to [setup your BIOS to boot the Ubuntu disk in legacy (not UEFI) mode.]("https://help.ubuntu.com/community/UEFI#Setup_the_BIOS_in_EFI_or_Legacy_mode")

---

