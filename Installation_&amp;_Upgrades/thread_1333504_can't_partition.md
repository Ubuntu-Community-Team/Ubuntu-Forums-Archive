---
title: "can't partition"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by dcottingham on 2009-11-21
I'm attempting to install using the xubuntu alternate 9.10 i386 iso on a USB drive, the hd-media kernel and initrd.gz on my target disk, and a grub floppy. Everything goes fine for a while -- the kernel boots, it finds and mounts the iso, loads installer components, etc -- until it's time to partition the target disk.

I go through "guided partitioning", tell it to go ahead and write it, but it then fails with a message that it couldn't mount the resulting disk. So I go ctl-alt-f2, and fire up fdisk. fdisk says: "Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disk label." So I manually use fdisk to set up the partition table, tell it to write and exit. Then I run fdisk again to check, and it again tells me that there's no partition table. I can run mkfs, but when I attempt to mount the result it's no go.

As an additional oddity, I have a second ATA disk on the same controller, and fdisk tells me it also has no partition table, and attempts to mount it also fail. But if I then boot my linux-on-a-floppy (Slackware 11.0) its fdisk says the partition table is just fine, and I can mount it and see everything is there just fine.

I am at a loss what could be going on here. It is plain that this disk is just fine, but the ubuntu installer can't deal with it. The only thing possibly out of the ordinary about my machine is that it is old -- about 10-11 years old. Any ideas?  Is the ubuntu hd-media kernel and initrd incompatible with the xubuntu installation iso?

---

### Post by dcottingham on 2009-11-22
Also tried this with the ubuntu alternate iso, with exactly the same result. So much for the theory that this problem is some conflict between ubuntu hd-media kernel and xubuntu iso.

Maybe ubuntu doesn't support old ATA drives? Any ideas?

---

### Post by darkod on 2009-11-22
Sorry, but I couldn't quite understand.
Grub floppy? Why, you can't boot off usb stick I guess because of the computer age.
Couldn't you just adjust the grub floppy to boot xubuntu 9.10 from the usb stick?
Why are those kernels you mention involved?
I am not sure but if in this whole process your HDD gets mounted it might be a problem. It can't do anything on mounted disks I guess.

---

### Post by dcottingham on 2009-11-22
Yes, my computer has USB but the BIOS doesn't know how to boot a USB disk. It's an old computer.

I haven't tried using grub to boot the kernels off the USB disk. I'm not sure how to name the USB disk to grub. Are you thinking I could use a USB installer this way?

I'm using the hd-media kernel and initrd because they understand that they should look for the installation iso on a hard disk, mount it, and install from it. And this part works just fine.

I have checked that, at the point the partitioner is trying and failing to do its thing, the hard disk is not mounted ("df" shows just the ramdisk, the USB disk, and the installation iso on the USB disk mounted loopback).

---

### Post by dhavalbbhatt on 2009-11-22
If you are trying to install using the Desktop installation CD, then try doing the following:

Run the LiveCD. Once you are in the LiveCD environment, open Synaptic Package Manager (under System > Administration > Synaptic Package Manager).

Search for "dmraid". You will find two packages under dmraid which will show as installed.

Mark these installed packages for "complete removal". 

Once this action is complete, re-boot with the LiveCD in your CD drive. This will allow you to go past your partition manager during your installation.

Hope this helps.

---

### Post by dcottingham on 2009-11-22
Thanks, but the reason I'm jumping through these hoops is I have no CD drive.

---

