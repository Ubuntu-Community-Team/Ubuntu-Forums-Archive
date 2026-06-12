---
title: "Dual boot XP, No cdrom, Failed install"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by ash_nug on 2008-07-17
Hi.

Wanting to breathe new life into a crappy old laptop thats too slow to run XP comfortably. 

I wish to keep XP on there however.

Problem is, the cdrom drive, and network card is ******.

I used a USB drive to transfer the ubunto ISO onto the laptop and mounted it on a virtual drive using some pirated software.

Install went without a hitch, then it asked to restart windows. However there is no sign of grub or a working ubunto desktop.

I chose to install Ubunto "inside windows", and indeed there is a folder with its files there. Im assuming the install failed because i mounted the CD on a virtual drive? 

Can this problem be solved by installing grub manually?

I thought this would have worked as i read a post in another thread saying he did the same thing...

When i boot the CD in windows it askes me if i wish to uninstall Ubunto, so it defo installed. Question is, how do i get the dual boot workin?

---

### Post by logos34 on 2008-07-17
So, you can run the cd in windows but not boot from it, is that what you mean?

If you're trying to 'breathe new life' into this machine, a Wubi-type virtual install is not the way to do it.  It'll run even slower because it's running **inside** windows on a loopmounted filesystem.

You want to try a lightweight ubuntu flavor like Xubuntu.  Get the alternate install .iso and follow this guide:
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)
(->'CD image approach')

---

### Post by ash_nug on 2008-07-17
> **logos34 said:**
> So, you can run the cd in windows but not boot from it, is that what you mean?

If you're trying to 'breathe new life' into this machine, a Wubi-type virtual install is not the way to do it.  It'll run even slower because it's running **inside** windows on a loopmounted filesystem.

You want to try a lightweight ubuntu flavor like Xubuntu.  Get the alternate install .iso and follow this guide:
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)
(->'CD image approach')

Thanks for your reply.

Correct: i can mount the CD image and install inside windows. I do this because the CDrom drive is non-functional. However upon restarting windows i cannot boot linux. Im guessing grub didnt install itself properly resulting in windows booting up as normal.

Your probably right about it being too slow, but i would still like to give it a try for the time being. If i cannot boot to Ubunto ill uninstall it and give your solution a try, although the following quote troubles me slightly, as this will be the case with myself:

"If you are installing onto the disk that is hosting the installer, and during partitioning the installer says that the kernel cannot read the new partition table, and that you should reboot your system, don't. The partitioner has already flagged the new Linux partition as the boot partition, so the system will be unbootable. If you're dealing with a system with no floppy or CD drive, you will be stuck. Instead, use Alt-F2, Enter to open a console and use cfdisk to set the boot partition back to the partition which hosts the installer, then go back to the installer using Alt-F1, <Go Back> as many times as needed to get to the menu, then select "Abort Installation" to reboot. "

---

### Post by logos34 on 2008-07-17
yeah, I understand your concern...cfdisk is pretty straightforward though...I've tested most of the methods on the page, but I cannot remember actually seeing that message pop up after the installation.

If you can boot from USB, then you could get the Super Grub Disk (USB tar.gz), or else the SGD floppy version, just in case of emergency, to make the windows partition 'active' again.
>  
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#mistake_when_I_edited_my_menu.lst](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#mistake_when_I_edited_my_menu.lst)
* No Active Partition Found message appears. With Super Grub Disk you will be able to activate partitions. You need the 'Tools' menu, available from the Super Grub Disk's English Super Grub Disk menu. 

---

### Post by ash_nug on 2008-07-17
> **logos34 said:**
> yeah, I understand your concern...cfdisk is pretty straightforward though...I've tested most of the methods on the page, but I cannot remember actually seeing that message pop up after the installation.

If you can boot from USB, then you could get the Super Grub Disk (USB tar.gz), or else the SGD floppy version, just in case of emergency, to make the windows partition 'active' again.

I would like to play/learn about supergrub, but ill do that only as a last resort. Im still cofident that ill be able to get Ubunto working from inside windows. It is afterall why i decieded to go with this distro, as it was designed with this purpose in mind.

Furthermore my laptops limited bios does not provide the option of booting via USB, but it does have a disk drive.

Is there any other threads out there were people have discussed this? I have seen people mention that they were able to mount the ISO and get Ubunto working, they said it was "easy", but never went into any detail.

---

### Post by dreadmeat on 2008-07-17
supergrub .ISO is a lifesaver.

'EEE_XP_MINI.ISO' is worth a look for an uber lightweight stripped down xp

---

### Post by ash_nug on 2008-07-18
> **dreadmeat said:**
> supergrub .ISO is a lifesaver.

'EEE_XP_MINI.ISO' is worth a look for an uber lightweight stripped down xp

Is this a total replacement for XP? Sounds intriguing.

Although im still looking for a dual boot alternative.

Thanks for the reply.

p.s: Specifically, im looking for information on how to fix my boot loader so it gives me the option of booting with Ubunto. Does the windows based Ubunto install use GRUB? If so, where do i access the bootloader options (within windows) if i cant boot from the CD (as the drive is broken)?.

---

### Post by dreadmeat on 2008-07-18
> **ash_nug said:**
> Is this a total replacement for XP? Sounds intriguing.

Although im still looking for a dual boot alternative.

Thanks for the reply.

p.s: Specifically, im looking for information on how to fix my boot loader so it gives me the option of booting with Ubunto. Does the windows based Ubunto install use GRUB? If so, where do i access the bootloader options (within windows) if i cant boot from the CD (as the drive is broken)?.get supergrub and boot it, follow the instructions it's straightforward and relatively graphical too.

as for the borg xp, try it out see what happens... :p

---

### Post by ash_nug on 2008-07-18
> **dreadmeat said:**
> get supergrub and boot it, follow the instructions it's straightforward and relatively graphical too.

as for the borg xp, try it out see what happens... :p

will this super grub thing work for the windows based linux install? there is no seperate partition for linux on my computer... i installed inside of windows...

---

### Post by dreadmeat on 2008-07-20
wubi? i'm not sure.

czech out [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
and of course [http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by upchucky on 2008-07-20
Advanced supergrub combined with Knoppix live cd are a godsend when playing with installs. supergrub can fix any mbr, stage 1 or stage 2 errors.

knoppix live cd can read and repair windows files, and it comes with qparted which does ntfs partitons and gparted that does linux partitions.

knoppix also gives you an easy way to edit ubuntu files and the bootloader files.

and windows is the best virus catcher out there.

---

### Post by Wazoot on 2008-07-20
a WUBI derived install will be slower then XP itself, since its basically intalled inside windows, if your HD is big enough partition it and install Ubuntu..without Wubi. =D

---

