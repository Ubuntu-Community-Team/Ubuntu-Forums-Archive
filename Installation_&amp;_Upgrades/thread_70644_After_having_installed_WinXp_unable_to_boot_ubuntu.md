---
title: "After having installed WinXp: unable to boot ubuntu"
date: 2005-09-30
forum: Installation &amp; Upgrades
---

### Post by TopasPV on 2005-09-30
Hi guys!
For a couple of months I've been using Ubuntu and (cause I use to play Counter-Strike) WindowsXP. My partitions:

hda1 WindowsXP (ntfs)
hda2 Ubuntu / (ext3)
hda6 /home (ext3)
hda5 Swap
hdb1 extra space for some files (ext3)

As I mentioned before I used this systemconfiguration for quite a while and I was realy surprised as suddenly everything began to go wrong. I tried to start Windows XP by selecting it via Grub and it began to load. Unfortunately, it didn't boot completely. (Might this have anything to do with a kernelupdate I installed in these days?) After some attempts I decided to reinstall Windows and reformat hda1. I installed a tool called Ext2IFS (Ext2IFS_1_10.exe) to access my linux-partitions while using Windows and I think this to be a possible reason for the upcoming problem - also I've used this tool before without any problems. Because of the new Windows installation I had to reinstall Grub and used the Rescue function of the Ubuntu-CD to "grub-install /dev/hda". Now Grub displays two Ubuntu releases: the old and the new kernel version (2.6.12-8-386 and 2.6.12-9-386). As only the old one seems to have a proper function I start my Ubuntu using 2.6.12-8-386. After having completed some tasks it stops at "Checking filesystem...", says it can't find /dev/hda6 and tries to repair /dev/hdb1 saying:
"The superblock could not be read or does not describe a correct ext2 filesystem. ... then the superblock is corrput, and you might try running e2fsck with an alternate superblock: e2fsck -b 8197 <device>"

Summary:
- I can't access hda6 and hdb1 from linux (but from WinXP using the tool mentioned before)
- I read some threads on this forum about similar problems but none of them was able to help me out

I appreciate for every single answer.
Regards, TopasPV

---

