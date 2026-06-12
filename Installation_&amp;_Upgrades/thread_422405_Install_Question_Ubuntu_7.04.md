---
title: "Install Question Ubuntu 7.04"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by victorash on 2007-04-25
I have 2 Hardrives Window XP is on the First Drive , my 2nd Drive is empty, I intend to partition my hardives, will it make any difference if I install Ubuntu on the second drive, or is it better to set up a Partion on the fist drive so its installed on the same Drive as Windows XP.  Im not sure if the install process is any harder if you are installing to a 2nd Drive. I have downloaded the file to my Desktop and wilL burn it to CD.  How much space should I allow for Ubuntu ? I think I read it depends on how much Ram you Have is that right ? I have 4Gb of ram.

Thanks For Help

Alan

---

### Post by BoneKracker on 2007-04-25
Actually, it doesn't matter as long as you install Windows first and in first part of boot disk.  You can put Linux on the same disk or another.  Both are fine.

My preference is for a different disk.

---

### Post by Spr0k3t on 2007-04-25
You've got quite a bit of ram, so much that I'm wondering if it would be beneficial for you to avoid using a swap partition.  Well, I would do at least 512MB for the swap (just in case).  Change the boot order in the bios and install to the second drive.  Once installed, you will need to edit GRUB if you want to boot to your XP partition.  Another option would be to use the installed XP as a VM system, you enough memory that I doubt you would even touch the swap space.  As for the size needed for Ubuntu, you will need at least 4GB to install, but I would recommend at least 20-25GB for a good daily use.

---

### Post by BoneKracker on 2007-04-25
Missed your other questions:

You need about 5 GB to have a full install.  It has nothing to do with how much RAM you have.  And you have plenty of RAM anyway.  10 GB is run-able for an extended period (you'd probably run out of space with only 5).

If you have the space, give it about 40-50 GB.  That leaves you plenty of room for MP3 files, photographs and stuff.

If this is your first Linux install, it's probably best to let the installer automatically partition the disk for you.  But that will also hog either the whole disk or whatever free space is available.

If you have a big drive (say 160 GB), one easy way to handle this is:

When you get to the part of the install where it talks about partitioning, go into "manually parition"
Create a "placeholder" partition that takes up all the free space except about 60 GB.
Then go back to "automatically partition" and tell it to use the free space.

Then you can later delete the "placeholder" partition, and that gives you some free space to play around with later (like if you want to create a /srv partition to put public files on or something, or if you want to install another system).

If you know how to use a partitioner in Windows, you might prefer to make that placeholder partition that way before starting the Linux install.

Also,  I wasn't going to mention it because it's a bit more advanced (to understand, not to do):

If you're installing Linux to a separate disk from Windows, you can do a neat thing.  Instead of having the Linux bootloader over-write the Master Boot Record (MBR) that Windows created on your first disk, you can have it install to the MBR on the second disk.  If you then go into your BIOS settings when you reboot and switch the boot-disk to being the second disk, then your old Windows MBR will remain intact (which is useful if you ever decide to uninstall Linux).

---

### Post by JLahm on 2007-05-04
Bonekracker: Could you elaborate a little about what you meant when you said: 

[INDENT]"If you're installing Linux to a separate disk from Windows, you can do a neat thing. Instead of having the Linux bootloader over-write the Master Boot Record (MBR) that Windows created on your first disk, you can have it install to the MBR on the second disk. If you then go into your BIOS settings when you reboot and switch the boot-disk to being the second disk, then your old Windows MBR will remain intact (which is useful if you ever decide to uninstall Linux)."[/INDENT]

I am looking to install Ubuntu onto a second, new drive and your approach looks like a great idea. I am new to Ubuntu, so I want to make sure I do it right! If you could give a few additional instructions, I'd appreciate it. Thanks.

Jim

---

