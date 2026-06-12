---
title: "how to restore grub2 - different drives"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by mawiles on 2010-05-28
I have a rather interesting situation. I have an IDE drive with windows xp and a sata drive with ubuntu 10.04. I have to disconnect the xp drive to get a proper boot into ubuntu (using the bios select boot drive causes the /home directory (sda5) to not mount, use to work with 9.10). How do I install grub on my xp mbr (though I hate to do that) to dual boot. There is good documentation, but can not find documentation when more than one drive is present, and the documentation is a bit vague for me.
HELP !!!!!!!!  :roll:


sda = SATA Drive - ubuntu 10.04
sdb = IDE Drive - windows xp

bios is set to boot sdb first.

If change bios to boot sda first, then ubuntu boots with error that /home is not mounted (sda5)

if use the 'on the fly' change boot order same thing as if changing boot order in bios occurs. The solution it seems is to place grub on sdb to be able to dual boot xp and my ubuntu installation on sda.


results of fdisk -l is:


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

Device Boot Start End Blocks Id System
/dev/sda1 * 1 14589 117186111 83 Linux
/dev/sda2 14590 60801 371197859+ 5 Extended
/dev/sda5 14590 60545 369141538+ 83 Linux
/dev/sda6 60546 60801 2056288+ 82 Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdc44dc4a

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 9729 78148161 7 HPFS/NTFS

I would prefer to use the live CD to affect these changes.

---

### Post by darkod on 2010-05-28
Boot into live mode, and if your root partition is /dev/sda1 as it seems, to install grub2 to the MBR of the IDE disk just do:

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

---

### Post by mawiles on 2010-05-28
Followed the directions literally,

All that did was render Ubuntu unable to boot, just like I was selecting the SDA Sata drive to boot from using either change bios or on the fly select drive to boot.

This means that the mbr of SDB is now over written, which is what I really wanted to avoid, as my xp cd is packed away.

when the system boots, I see grub come up, and a disk check is automatically started. Then the old familiar error message

"The disk drive for /home is not ready yet or not present"

"Continue to wait; or press S to Skip mounting or M for manual recovery"

You can wait till hell freezes over  :)
Skip mounting, and you don't have a usable system
manual recovery is above my head.

If I have to reinstall linux to fix this, I will be going back to 9.10, as there are a bunch of bugs with the LAMP stack as well.  

Please advise... now off I go to hunt down my packed away xp cd to restore the mbr.  Sure wish Linux had a decent easy to use utility to do the same.

---

### Post by darkod on 2010-05-28
It does, you can use lilo for that. Ignore the warnings it will give you:

sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr

That will write generic mbr on /dev/sdb which just calls the boot flag, similar to windows bootloader. XP should start booting fine.

The message about /dev/sda5 might mean something else is going on. It seems this is not entirely grub2 issue.

---

### Post by mawiles on 2010-05-28
ah... back to the old way of booting Ubuntu.... I never did like this grub2 which was "supposed" to make things easier.  I guess I am old n crusty, and if it ain't broke, don't fix it

I dont' know what is going on with sda5, I know I am typing this in ubuntu that is installed on sda1, but I disconnected the xp drive.  I wouldn't fuss with this that much if there were not so many issues with LAMP in ubuntu 10.04, and it is just easier to set up WAMP and configure in windows( which is really working nice btw).

I may try the old trick of hooking all the drives up and do an install up to the point of setting the partitions and drives, without formatting them and see what happens (installing grub too).  

If not successful, then I guess when I find the xp cd I will find the old 9.10 cd too, and drop back a version for around 6 months or so and let 10.04 mature a bit

---

### Post by darkod on 2010-05-28
I have no issues with grub2, same as many others. It still looks like something else is the problem, just grub2 can't act like this.

You could run the boot info script for more details, it's in my signature. If you need instructions, here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

You don't have to post the content of the results file unless you have questions. But looking at it might help you figure out something.

---

