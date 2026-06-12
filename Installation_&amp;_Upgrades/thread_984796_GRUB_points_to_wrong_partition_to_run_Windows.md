---
title: "GRUB points to wrong partition to run Windows"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by Yankees9920 on 2008-11-17
I installed GRUB onto the partition with the Linux install. And GRUB launches Linux, however when I click to launch Windows XP i get "Error 21".

I pressed "e" to look into the statement, and says

root (hd1,0)
map(hd1,0)
map(hd1,1)

If I manually change these by pressing "e" before I boot and change them to

root(hd0,0)
map(hd0,0)
map(hd0,1)

and press "b" it boots into Windows XP no problem.

The problem that I am having is that when I make those changes they are not saved in GRUB.

So basically I am asking is how can I change those settings to the proper ones.
Linux is not finished installing yet and will only boot up into a black screen with a command prompt type thing, with no graphical interface. And when I tried running a liveCD of linux I was unable to find the GRUB.conf file, that I believe I have to change.
Is there anything I can do from windows to fix this?

---

### Post by Yankees9920 on 2008-11-17
I reinstalled using the regular installation disk, rather than alternative...and GRUB seemed to correct itself. I just had to select advanced settings and make it install GRUB onto (hd0,2).

All partitions boot fine now;
Windows XP
IBM Thinkpad Recovery & Restore
Linux

---

