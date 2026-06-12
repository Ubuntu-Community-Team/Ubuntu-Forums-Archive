---
title: "Dual Boot - Blue Screen of Death"
date: 2005-11-03
forum: Installation &amp; Upgrades
---

### Post by Zyrix on 2005-11-03
I have tried searching for the resolution to this problem but have not been able to come to a resolution. This appears only to happen when I install Ubuntu. Originally this started with Hoary, so I switched to Gentoo until Breezy came out. Now Breezy is out and the issue is still not corrected.

I have 1 drive (30GB). It had Windows XP on 20GB of it, the extra 10GB was free. 

I installed Ubuntu to the 10GB partition (with default partition ext3 and swap) and wrote grub to the MBR. When I boot the machine I get a Grub menu to choose XP or Ubuntu. If i load Ubuntu everything is fine. When I boot Windows I get Unmountable Boot Volume - bluescreen of death. 

So I wipe everything and reinstall Windows (it was a clean install anyways) on a 20GB partition. 

Then I install Ubuntu on the additional 10GB of free space on the drive and partition it as follows:

hda1 - Windows -  NTFS - 20GB
hda2 - /boot - ext2 - 32MB
hda3 - / - reiserfs - 9GB
hda4 - swap - 512MB

I then installed Grub to hda2

When I boot it goes straight into Kubuntu. So from there I edit the /boot/grub/menu.lst and add the following:

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


I reboot the machine and load Windows and get the same BSOD: UNMOUNTABLE_BOOT_VOLUME

Anyone have any advice?

====================

Hardware: IBM Thinkpad T40

I have tried Ubuntu Hoary and Breezy - same issue with both.

---

### Post by fannymites on 2005-11-03
Is the first partition marked as bootable/active?

---

### Post by Zyrix on 2005-11-03
hda2 (/boot) was the one marked bootable - the NTFS partition was not.

---

### Post by martz on 2005-12-15
I'm having this same issue... on the same hardware... did you ever get it resolved?

---

### Post by markcaetano@gmail.com on 2005-12-15
it might be that it dosent like ibm's made in a certain year
tell me what year it was made in cos my aptiva was made in 1999 and it dosent even partition the drive without freezing!!!

---

### Post by markcaetano@gmail.com on 2005-12-16
just came to my mind again what does the BSOD say

---

### Post by towsonu2003 on 2005-12-16
[QUOTE=Zyrix]hda2 (/boot) was the one marked bootable - the NTFS partition was not.[/QUOTE]
mark windows partition bootable instead instead of /boot. Also, partitioning like this might help as well:
hda1 bootable 20GB ntfs
hda2 4,5 GB ext3 /
hda3 512MB swap
hda4 restGB ext3 /home

I wont be able to help other than this :(

PS. Adding a Fat32 in ther would be nice though (transfer files between OS')...

---

### Post by sparmar on 2006-05-24
Was any able to fix this problem. I am having the same issue on T40, UNMOUNTABLE_BOOT_VOLUME, BSOD. 

I am a newbie, so can  someone tell me how do I make the partiion bootable or recover my system.

---

### Post by Sef on 2006-05-24
sparmar:

Could you please start a new thread.  Thank you.

In the new thread, copy and paste the results of this command:

sudo fdisk -l

(The reason for starting your own thread is that otherwise it looks like you are hijacking this thread, which I am sure is not your intention.  We all make mistakes at times.)

---

### Post by wavesound on 2007-11-25
> **Sef said:**
> sparmar:

Could you please start a new thread.  Thank you.

In the new thread, copy and paste the results of this command:

sudo fdisk -l

(The reason for starting your own thread is that otherwise it looks like you are hijacking this thread, which I am sure is not your intention.  We all make mistakes at times.)

HI Did a new thread get started?
I have the same t40 and the same problem!

Cheers
Bob

---

