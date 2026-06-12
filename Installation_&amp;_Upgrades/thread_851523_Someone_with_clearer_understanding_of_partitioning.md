---
title: "Someone with clearer understanding of partitioning schemes help please."
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by ethos101 on 2008-07-06
So I have a laptop that had vista and a recovery partition then a data partition.  I backed up the recovery partition and erased it then erased the vista partition.  I've had XP on here as well which I'd like to keep and dual-boot.  I don't know if thats possible.

This could get complicated.

Here's a screenshot of what I have.
sda4 = DATA, storage space.
sda5 = XP
sda6,7,8 = Ubuntu Hardy (swap, boot, root, respectively)
Now, 5, 6, 7 and 8 are all logical drives under the extended partition sda3.

When I add the entry for XP in grub's menu.lst it's hd(0,5) but it gives me BOOTMGR isn't found which is vista's boot loader.  I've tried booting the XP CD to get to recovery console and rebuild the boot sector using fdisk /fixmbr command but XP's CD just hangs while trying to boot, I'm assuming it hangs because the first partition is an extended partition or because the first logical drives are linux and the XP CD doesn't comprehend (I assume this from past experience).

The unallocated is left for other distros I'd like to try out in the future.

[[img]http://pix.nofrag.com/4/d/d/8cf4674899634e1debb7fed540ada.png[/img]](http://pix.nofrag.com/4/d/d/8cf4674899634e1debb7fed540ada.html)

I'm a bit stumped.  At least Ubuntu is working fine but I have apps for my digital camera in XP I'd like to use once in a while plus I need XP for school.

Any help is appreciated.  I'm thinking I screwed myself somehow.

---

### Post by Pumalite on 2008-07-06
You are trying to boot Windows from a logical partition. Windows needs a primary partition; preferably sda1. Grub can boot Windows from a logical partition. Pretty tricky. I know of only two guys around here that have done it. Maybe they will show up to help you.

---

### Post by ethos101 on 2008-07-06
Yeah, I was doing it when I had Vista/XP dual-booting but I had to use easyBCD in both vista and xp to re-write the mbr each time i wanted to switch between the two.  I think that was because I had both OS's on logical partitions.  I just didn't think this through when I set up my partition scheme...

---

### Post by ethos101 on 2008-07-07
Bump
):P

---

### Post by upchucky on 2008-07-07
first fix the ntfs partitions with windows xp there is a command ```
chkdsk /f
```to fix the clusters then reboot to make it work, the fix is silent, but it works. if win xp wont boot, get supergrub, it will boot xp.

Then use supergrub to search the drives, advanced mode commandline. to discover geometry.

your data is all intact and can be restored

make xp drive active with gparted.

/boot/grub/menu.lst needs editing to be told where each op system is, as the partition order is all changed because manipulating partitions

---

