---
title: "Help with dual-booting windows"
date: 2006-09-15
forum: Installation &amp; Upgrades
---

### Post by OskarS on 2006-09-15
Hello

I'm running Ubuntu 6.06 and I want to install windows and be able to double boot (from the same drive). So I allocate 15 GiBs at the end of my drive for windows, I backup the grub-bootloader settings using

```
dd if=/dev/sda of=mbr.backup bs=512 count=1
```

I proceed to install Windows XP in the unallocated free space. Everything works fine, but the next time I start up the computer it (as I expected) boots into windows. I put in my Ubuntu LiveCD and boots from that. In the Disks window (System -> Administration -> Disks) i see all three of my partitions, my ext3 ubuntu partition, my NTFS windows partition and my swap partition. I mount my ext3 drive to /mnt/ and I run

```
dd if=/mnt/home/oskar/mbr.backup of=/dev/sda bs=1
```

to restore grub. While this works fine (next time I do boot into grub and ubuntu), it seems to destroy my windows partition. Right after I've done it, it registers as unallocated space instead of NTFS. What have I done wrong? I'm really very new at this, so it's probably something stupid that I'm missing. I'm thinking it might be that I should have run the backup and restore of the boot settings on sda1 instead of sda (my pure ignorant guess is that this my first partition, ie ubuntu), but I really have no clue.

Another thing: I want to get the menu settings for grub down right. To properly boot into windows I should have an entry in /boot/grub/menu.lst that says

```
title		Windows 95/98/NT/2000
root		(hd0,x)
makeactive
chainloader	+1
boot
```

where x is the partition that I have windows installed on, right?

Any help would be greatly appriciated. Thanks!

---

### Post by Herman on 2006-09-15
There are three parts of the 512 byte Master Boot Record. The first 446 bytes is the bootloader code, that's the part you want to back up and restore.
There is also the four x 16 byte partition table there (= 64 bytes), and a 2 byte 55aa bootable device signature.
446+64+2=512
It would be better for you to use,
```
 dd if=/dev/sda of=mbr.backup bs=446 count=1
``` The code you were using was backing up and restoring your MBR with your old partition table on it, so you were wiping out your newly created partition when you restored it. (Because you were also restoring your old partition table, that didn't have a Windows partition yet).  Here are two links about it, [Click Here]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_back_up_and_restore_your_MBR")    |     [Click Here]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd")

Your proposed menu.lst entry looks okay, it should work if you add the correct partition number to it. You should paste that to the *bottom* of your menu.lst file and you should add these extra lines above it to mark the end of your debian automagic kernels list too.

```
### END DEBIAN AUTOMAGIC KERNELS LIST
                                        
# This is a divider, added to separate the menu items below from the Debian
# ones.
 title        Other operating systems:
 root
                                        
                                        
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdax

title        Windows 95/98/NT/2000
root        (hd0,x)
makeactive
chainloader    +1
boot
``` Regards, Herman

---

