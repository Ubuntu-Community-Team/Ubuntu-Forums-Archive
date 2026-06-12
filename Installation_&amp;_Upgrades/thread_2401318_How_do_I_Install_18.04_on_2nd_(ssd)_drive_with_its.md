---
title: "How do I Install 18.04 on 2nd (ssd) drive with its own boot loader"
date: 2018-09-16
forum: Installation &amp; Upgrades
---

### Post by wiz70 on 2018-09-16
I have a new Acer laptop with 12 gb ram, a 1tb hdd and new installed 256gb ssd.  Windows is resident on hdd.   I want to install 18.04 on the ssd drive with its own boot loader.   I want to be able to select what drive to boot from in the powerup F12 selection process.   Have read numerous articles but, not finding a "How To" for my requirements.  I have already did one reinstall of windows due to false info from one article.  Fast boot is disabled.

Doing the install, I need to know how to configure the Partitions for the sdd drive (sdb), so that I have the booting flexibility I want.   Also, how do I deal with the "Stack Exchange" issue of 512b vs 4096b? 

Have spent many hours researching this issue and know there has got to be a process in place to do this.....

Appreciate the help....    Thx

---

### Post by oldfred on 2018-09-17
Drives automatically use 512 logical even if newer 4K drives.
But you have new UEFI system, so must use gpt partitioning. At minimum you need ESP & /.
How you boot install media UEFI or BIOS is then how it installs, so be sure to boot installer in UEFI mode from UEFI.
Many need UEFI settings changed to allow USB boot.

Acer has a unique requirement of once installed you must set "trust" on the grub/Ubuntu .efi boot files particularly shimx64.efi.
         Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947)

Is SSD seen as sdb? 
If so better to disconnect SSD when installing Ubuntu. You may be able to logically disconnect it in UEFI, if difficult to physically unplug power or signal cable.

Issue is Ubuntu's UEFI version of grub only wants to install to ESP - efi system partition on first drive, normally sda or first NVMe drive. And then if you can Ubuntu drive bootable on its own, you have to manually copy files from one ESP to ESP on Ubuntu drive and edit fstab with correct UUID.

General UEFI install instructions in link below in my signature. With more links to anything you amy not understand.
Be sure to fully back up Windows and make a Windows repair flash drive.
Also even when installing to a separate drive, you will need Windows fast start up off, so the Linux NTFS driver can see the NTFS partition(s). Otherwise they are hibernated & invisible.Also note that Windows with many udpates turns fast start up back on. So when issues seeing NTFS or booting Windows from grub, boot directly from UEFI and turn fast start up off again.

---

### Post by wiz70 on 2018-09-17
In my original post, I stated; sdd drive (sdb), fast boot is disabled and SSD is the target for Ubuntu.  Removing the SSD is contradictory to what I'm trying to do. Fast boot is disabled in the Acer Power Options, not in the Bios. The SSD is setup for gpt partitioning.

Acer Trust settings is something I didn't come across in my research.  I'll have to investigate it. 

" [COLOR=#000000]Issue is Ubuntu's UEFI version of grub only wants to install to ESP - efi system partition on first drive, normally sda or first NVMe drive. And then if you can Ubuntu drive bootable on its own, you have to manually copy files from one ESP to ESP on Ubuntu drive and edit fstab with correct UUID."  ? IS THERE A PROCEDURE FOR THIS?[/COLOR]

During the partitioning of the SSD for the install, I get a warning about the stack exchange set for 512 instead of 4096 so, should I then accept that or do need to realign the drive?  Is there a procedure to realign the drive?  

When I get to partitioning the SSD what are the required partitions to install Ubuntu and set the SSD to be able to Boot?

---

### Post by C.S.Cameron on 2018-09-17
Can you not just unplug the HDD while installing to the SSD?
Once installed make the SSD No 1 HDD in BIOS, (or whatever).
Boot the SSD and run update-grub.
Windows should end up at the bottom of your SSD's grub menu.

---

### Post by Dennis N on 2018-09-17
> you have to manually copy files from one ESP to ESP on Ubuntu drive and edit fstab with correct UUID." ? IS THERE A PROCEDURE FOR THIS?

Yes, there are a few fairly simple steps. I've done it a couple of times. 

You boot Ubuntu, then mount the new EFI partition, and from terminal copy the Ubuntu folder from one EFI system partition to another.  Your fstab has the UUID of the old EFI partition, so you have to edit that to match the new EFI partition. You also need to generate a new entry in the EFI boot manager menu so that the firmware knows which EFI partition to go to for grub files. That is done with efibootmgr (Formulating the command options for this may be the hardest part). You don't need to reinstall grub.

---

### Post by oldfred on 2018-09-17
Minimum partitioning or a default UEFI install to an empty drive is ESP & / (root). But if installer sees ESP on another drive, it will not create one on new drive. So you have to partition in advance.
I prefer smaller /  partitions of 25 to 30GB and larger data or /home. I use /mnt/data for all my data, but I want to mount data in multiple Ubuntu installs. You may want a separate /home and a shared NTFS partition. Every user has different requirements.

If you look at link in my signature below and in that is a two drive section. The two links there have lots more details on install to a second drive. Also examples of using efibootmgr to create UEFI boot entries. 

If you need specific help, best to post details of where you are at. If installed post link to summary report from Boot-Repair.
       [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

