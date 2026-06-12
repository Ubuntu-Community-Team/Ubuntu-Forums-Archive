---
title: "[SOLVED] Post attempted 8.10 upgrade  -   need help!!"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by groovelator on 2008-11-02
Hi,

My upgrade to 8.10 went horribly wrong  -  apparently every application that I'd installed was 'obsolete', so on reboot I discovered that my system was toast.

My first move was to d/l a copy of 8.10 and install it that way.  No dice  -  got stuck on a black screen after installation.

Next move was to d/l 8.04 and reinstall this.  It's working fine :)

**My problem is this**: I now have three partitions on my hdd, old 8.04, new 8.04 and 8.10 which doesn't work.  (Please see screenshot)

* I want to keep the data from my old 8.04 install but delete everything else.

* I also want to delete 8.10 and recover the partitioned space, merging it with the old 8.04 partition.

* I want GRUB to understand that I only have *one* OS.

I think part of the problem is permission  -  I don't 'own' either partition so can't use the manager it seems.  Or delete files.  Also, I think they're both mounted and refuse to be unmounted?

But the biggest problem is that I don't know enough about Linux to fix this...

Any help appreciated!

cheers,
Mark

[COLOR="Gray"]--
[www.myspace.com/markbristol](www.myspace.com/markbristol)[/COLOR]

---

### Post by tommcd on 2008-11-02
> **groovelator said:**
> 
* I want to keep the data from my old 8.04 install but delete everything else.

* I also want to delete 8.10 and recover the partitioned space, merging it with the old 8.04 partition.

* I want GRUB to understand that I only have *one* OS.


Use a GParted live CD or a Parted Magic Lice CD:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)
Boot from one of those. Delete everything exept /dev/sda1, which you have indicated is 'old 8.04' that you want to keep.
Next, use the gparted / parted magic live CD to make a 1GB swap partition from the newly created unallocated space.
You will have space left over. Partition that any way you want. Or leave it unallocated for now if you want. You could always partition and format it later.
For grub, which of all those Ubuntus has grub installed to the mbr? If it is 'old 8.04' on /dev/sda1, you are fine. If it isn't, you may need to reinstall grub to the mbr. If you need to do that, see this page to reinstall grub from the Ubuntu live CD:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck](http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck)
After that, you should be good.

FYI,
If you have more than one linux distro installed, you only need 1 swap partition. You don't need a swap for each distro. I have 3 distros on my PC and they all share the same swap.
You could use all that extra free space to install some other distros!

---

### Post by Partyboi2 on 2008-11-02
You also may need to unmount the partitions before deleting them you can do that by right click and choose to unmount and you probably will need to turn swap off as well (right click on swap and turn off)

---

