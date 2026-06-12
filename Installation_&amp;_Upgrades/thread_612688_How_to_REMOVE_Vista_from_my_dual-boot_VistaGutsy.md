---
title: "How to REMOVE Vista from my dual-boot Vista/Gutsy?"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by maria-n on 2007-11-14
After seeing the site of Badvista org, I've decided I want to remove Vista completely. Possibly I'll install XP next to Gutsy in that case.
I've been experimenting with gParted to try and clear Vista and install XP, but I couldn't make it work. I also followed the How-to to make a triple boot Ubuntu/Vista/XP, but couldn't install XP.
In Google I only came across uninstalling-insructions related to double-boot Vista/XP.

I'm ready to reinstall Feisty (and then upgrade to Gutsy) as my system is very new, so I won't lose much. But I'd prefer to remove Vista, without touching Gutsy.

My HDD is320 Gb, so the size is never an issue.

i'd be very happy with any help, but I'm not too knowledgeable, though with a good step-by-step explanation i can do a lot (like this is my fourth well-working dual-boot machine, with different OSses)

Thanks!
Maria

---

### Post by bulldog on 2007-11-14
Is Vista the only OS at the moment?
Just use gparted and remove all partitions also the hidden ones.
That should do it.

---

### Post by maria-n on 2007-11-14
Thanks for your reply :-)

No Vista isn't the only, it's a dual-boot with Gutsy (and I'm only using Gutsy, Vista never: it ruins our home-network) If possible I would like to keep Gutsy without reinstalling.

---

### Post by bulldog on 2007-11-14
Can you get me the output of the fdisk command?
In a terminal```
 sudo fdisk -l
``` small L not a one

---

### Post by maria-n on 2007-11-14
This is the output of fdisk -l:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8286    66557263+   b  W95 FAT32
/dev/sda2            8287       17052    70412895    b  W95 FAT32
/dev/sda3           17053       37851   167067967+  83  Linux
/dev/sda4           37852       38181     2650725    5  Extended
/dev/sda5           37852       38181     2650693+  82  Linux swap / Solaris

I must add, that when I tried to make the triple boot Gutsy/Vista/XP, I used gParted and partition 1 and 2 were NTFS.. But now when I tried to remove Vista and install XP instead, the NTFS option wasn't available, hence the outdated FAT32 (after deleting them and making new partitions that is).

---

### Post by forestpixie on 2007-11-14
Hi, I would be inclined to use [gparted]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828")  , you could of course boot with your livecd and use the gparted there.

Format at least  /dev/sda1 to NTFS for the xp install. For /dev/sda2 you could format to fat32 or ntfs so that you could use it from either xp or Gutsy.

Then do your xp install - once you've done that you'll need to redo grub because xp will overwrite it with it's boot - I've used [supergrub]("http://supergrub.forjamari.linex.org/?section=download") (which again is a livecd you boot with) to do that, you can again use the Ubuntu livecd to do [that]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0")

once you've done that you should have xp and ubuntu as a dual boot. 

you will also need to make sure the 2 new partitions mount in your ubuntu install -assuming you want them to. I dealt with the mount issue with the help of psychocats tutorial when I did it - but I've only done it once so not too sure about that one

hope that's of help to you

good luck

---

### Post by d4v1dv00 on 2008-06-24
Hi there, what if I am in similar situation and i want to completely remove vista and solely run Ubuntu Hardy? How can i reclaim all hard disk for Ubuntu only?

Here is my list of /dev

```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00095429

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19477   156447480    7  HPFS/NTFS
/dev/sda2           19478       24321    38909430    5  Extended
/dev/sda5           19478       24116    37262736   83  Linux
/dev/sda6           24117       24321     1646631   82  Linux swap / Solaris

```

Thanks

---

