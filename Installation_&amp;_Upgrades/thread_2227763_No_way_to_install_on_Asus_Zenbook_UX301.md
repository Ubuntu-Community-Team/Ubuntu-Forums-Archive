---
title: "No way to install on Asus Zenbook UX301"
date: 2014-06-03
forum: Installation &amp; Upgrades
---

### Post by a_m on 2014-06-03
Hallo,
I have a brand new Asus Zenbook UX301LA and I am striving to install Ubuntu 14.04 (I tried also Mint 17). No matter how I configure the bios, how hard I try, the installer just fails.
It seems that I can't get a mounting point or something.
I enabled CMS in the bios (disabled secure boot of course) and switched from RAID to AHCI. This helped a bit, but still not enough. In the partioning windows of the installer I have no active option for setting a mount point and I just see a mess of partitions, basically kind of /dev/mapper/xxxx stuff. How to get rid of all that crap of /dev/mapper?
(as I understand, there are two ssd in raid0. Also, Gparted fails as it starts, probably because it does not work with gpt?)
I don't want to save the Windows installation at all; I just want to erase everyhting and install Linux on a good old /dev/sda device.
Can you please help me?

---

### Post by gdesilva on 2014-06-03
Worth checking out the instructions for UEFI Installation before you try anything else....[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by a_m on 2014-06-04
Hallo,
I am trying to install Ubuntu 14.04 on a new Asus Zenbook UX301, but everything goes wrong and I am afraid I have badly messed up things.
Using boot repair did not solve the problems. 
[http://paste2.org/vLk6tdxN]("http://paste2.org/mdU6pbny")

At the moment, when booting I get:
error: unknown filesystem.
Entering rescue mode...
grub rescue>

I am pretty sure I have already destroyed Windows8, and I guess I really need some help, thank you!

---

### Post by Chris_Welty on 2014-06-07
I went through this successfully.  The many partitions it comes with was indeed very confusing.  You should see two very big partitions, though.  I did a simple boot, root, swap partitiion for dist 1 and one big-ass partition for disk 2.  I think for ssd partitions are not so important.

I followed some of the advice in this thread to break the RAID down into the two disks:

[http://ubuntuforums.org/showthread.php?t=2193133&highlight=asus+ux301](http://ubuntuforums.org/showthread.php?t=2193133&highlight=asus+ux301)

Then partition the disk.  If this doesn't help then give some more details.

Chris

---

### Post by Chris_Welty on 2014-06-07
It sounds as if something went wrong with your installation device.  Did you by any chance try to repartition it?  Do you have another computer to reformat and reinstall on it?

Chris

---

### Post by oldfred on 2014-06-09
Merged two threads on same issue.
Please do not create duplicate threads on the same issue. We all are volunteers and need to know what else has been suggested to avoid duplicate or conflicting suggestions.

You did a LVM or LVM with encryption install. LVM is with Ubuntu default install always a full drive install. Or you erased everything. Always best to have good backups before any major system change.

Some vendors will provide a replacement image of your hard drive for a nominal charge. That would be the same as the recovery partition on hard drive. Or you may have to purchase a full version of Windows. The product key is now built into the UEFI, but will only work with the vendor image or version.

---

### Post by charlie_mtl on 2014-07-13
Hi,

This is the way I instaled Ubuntu on my ux301.
First switch fron RAID to AHCI and disable all security options.
Boot from the Ubuntu USB stich and choose "Try Ubuntu"
Run gparted and delete all partitions, everything you can, on both SSD.
Then reboot and choose "Install Ubuntu".
Create 3 partitions: 1 => UEFI boot, 2=> / , 3 => swap
In my case I've installed OSX on the first place so In did not had to create a UEFI partition as it was created with OSX installation.

Hop it helps,
Best regards.
Charlie

---

