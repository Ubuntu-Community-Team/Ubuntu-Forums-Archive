---
title: "Tried to resize NTFS, Windows no longer booting. Please help."
date: 2006-08-07
forum: Installation &amp; Upgrades
---

### Post by kopo88 on 2006-08-07
I'm trying to install Ubuntu to dual-boot, with Win XP Home already installed.
1 hard drive, 160 GB (much less actual GB)

2 partitions:
5.8 GB - (D) HP/WinXP system restore, FAT 32
141 GB - (C) Main windows drive, NTFS, 24 GB free

I tried to resize the NTFS partition from the Ubuntu installer, with manual partioning, but it seemed keen on breaking my Windows partition in order to make a new one, so I'm trying to use QT Parted from the Rescue CD instead.

I opened QT Parted and did the preliminary resize, making the C partition 7 GB smaller.

It took about 10 minutes to complete the preliminary calculations, or whatever it was doing.

I pressed commit. It took about 25 minutes.

The partition is showing up as Active, but file system Unknown (instead of NTFS!)

When I tried to reboot into Windows, I got 
[B]
Missing operating system.[/B]

I'm frantic. Please, I know I sound like an idiot, but I'm completely at a loss! What should I do?

Does this mean I've lost all my data permanently? Is the partition corrupt, or is there a way to make the computer realize it's NTFS without formatting it?

---

### Post by hopstah on 2006-08-08
you haven't lost your data - if worse comes to worse, you can run a data recovery program on the hard drive.  other than that, i don't know what to tell you.  i have had great luck with gparted on the ubuntu live cd.  i really hope you can get this fixed with the fewest headaches possible ;)

---

### Post by orb9220 on 2006-08-08
Wait are you saying that the new partition is showing active or your xp partition is active?

Did you resize from the end of the xp partition from right slide to left?

---

### Post by kopo88 on 2006-08-08
The attached image shows what it looks like now (sorry, didn't have time to crop the screenshot).

I'm running Ubuntu Live CD right now.

/dev/hda2/ was formerly known as my C:\ drive, and was formatted as NTFS.

I tried running TestDisk within Ubuntu. It found a 7.5 GB partition - the unallocated one - but nothing else.

I'm also going to try to run it from the Ultimate Boot CD, but I doubt the results are going to be any different.

Any ideas?

---

### Post by confused57 on 2006-08-08
From the Ubuntu live cd, try running this command:
```
sudo fdisk -l
```
The -l is a small "L".

---

### Post by kopo88 on 2006-08-08
I ran the DOS version TestDisk from the Ultimate Boot CD.
It found both of my original, real partitions
1) FAT32 - Windows Recovery (Drive D)
2) NTFS - Windows, docs (Drive C)

However, they're being shown as "D" (deleted). If I change the NTFS partition's status to, say "*" (Primary bootable) , TestDisk tells me that the structure is [COLOR="Red"]Bad[/COLOR]

What should I do?

---

