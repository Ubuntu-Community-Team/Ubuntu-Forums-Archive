---
title: "partition ruined hard disk"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by pangil on 2007-10-26
hi, i have 2 PCs at home that were previously running windows. i installed ubuntu on one PC, liking ubuntu, i tried installing it on the other PC. when i did a manual partition on the other PC with these
preferences:
#1 - primary - 4GB - /
#2 - logical - 1GB - swap
#3 - logical - 15GB - /usr
#4 - logical - 20GB - /home

the installation went ok. but after restarting i got this error:
GRUB loading stage1.5 Read Error

i tried repeating the installation this time using guided partition and using the entire disk but i still got
the same error.
thinking that it there was probably something wrong with my installer, i installed debian. and i got the
very same error.
frustrated at having spent hours trying to get it to work, i went back to windows. when windows restarted during the installation i had a read error.
so now i got 1 useless computer because it looks like the hard disk is ruined.
could the partitioner have ruined my hard disk? is there still a way to fix it?

---

### Post by pangil on 2007-10-26
hi, i ran gparted to completely remove all of the partitions and started a fresh install using the
default settings.
i still got the same error:
GRUB loading stage1.5 read error

unfortunately my hard drive did not come with a diagnostic CD.
i'm really new to linux and i really don't know how to run super grub. can i get some help
concerning this? are there any other methods that i can try to fix my problem?

---

### Post by Craigus on 2007-10-26
I'd suggesting downloading Ultimate Boot Cd [http://ubcd.sourceforge.net/]("http://ubcd.sourceforge.net/")

It will have manufacturer software for your drive. Do a low level format to zero the drive and you should be fine from there ...

---

### Post by gpilkay on 2007-10-26
I honestly had a similar problem, I had to send mine back (luckily, Dell Business has the no questions asked 30-day swap policy).

Here's another possibility, program-wise:

[http://qtparted.sourceforge.net/](http://qtparted.sourceforge.net/)

You can also, if re-loadign windows, try for a full format, instead of just a quick one.  It takes a long time, though.

Right now, due to the problems I had, I am actually using a 7.10 Live-CD on my laptop when I need Linux, and the rest fo the time, running OpenOffice, Firefox, Celestia, Kompozer, and VLC in XP.  They seem to work just fine.

---

