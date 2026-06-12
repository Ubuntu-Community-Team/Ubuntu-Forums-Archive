---
title: "how to install ubuntu without formating"
date: 2005-08-06
forum: Installation &amp; Upgrades
---

### Post by idokus on 2005-08-06
What I want to do:

Install Ubuntu (perhaps making it Kubuntu afterwards) without losing data at the homedirs and some music files (I don't want to rip them all over again, but I do not want to back them up on cd)
I do not have enough space on the other partitions to back it all up.

What I have:
OS: Fedora c2 and windows XP (XP only for a few programmes with not a really alternative in linux, for as far as I looked)
Grub chooser

partitions:
[list]
[*]hda,0 winXP (NTFS) 20GB
[*]hda1 (FAT 32) 40 Gig (90 % used)
[*]hda2 boot (ext3) 100 MB
[*]hda3 / fedora (ext3) 58 GB 90% used
[*]hda4 swap 1GB
[/list]

(with a wrapper partition or something, never bothered to follow up on the details)

Is there an easy way of installing ubuntu on hda2,3 and 4?

---

### Post by macgyver2 on 2005-08-06
Weeellllll...I can't come up with anything that you haven't already said you can't or would prefer not to do...  You really can't get around formatting your / partition, which for you would wipe /home.  Maybe someone else can come up with a way to work some magic...

But I would like to offer a suggestion for when you get around to installing...make a separate /home partition (at the very least).  I think it's invaluable, and your situation shows why.  Were you to have a /home partition separate from your / partition, you could keep your personal data safe while still formatting /.  Also, some other partitions are worth having on separate partitions in certain situations...but if you really should have any of those separate you'd already know.  I'd say, though, definitely put /home on a separate, dedicated partition.

Anyway...saving your data...not enough space on the other partitions, don't want to burn things to CD.  Only other thing I can think of is do you have any friends or family with a usb hard drive?

---

### Post by idokus on 2005-08-07
hmm... I do was afraid of that, but at the time I didn't know what was a reasonable amount of space for home or the rest of the system at the time.

For now I would say: 
15 GB for the rest of the system
rest for home partition
2 *ddr size for swap
100 MB for boot
But I'm not sure about it quite, but then again, there is something like parted.

But I do know it is possible for windows to install without a format, so therefor I thought it should/could be possible to do so in linux aswell, but I couldn't find any advise on doing so.

---

