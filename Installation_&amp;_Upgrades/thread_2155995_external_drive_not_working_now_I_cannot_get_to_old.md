---
title: "external drive not working now I cannot get to old device"
date: 2013-06-20
forum: Installation &amp; Upgrades
---

### Post by Alphonso Whitfield on 2013-06-20
I have an acer netbook. I created an ubuntu instance and an xp instance on a 500 gb external drive. The drive fell off my table hit the floor and is no longer operable. I purchased an acer recovery disc , ran the disc as instructed but the recovery did not work when I restarted the netbook. I receveid this error: when the computer comes back on after the initial open screen.

error: no such device; b168-137b-9a13-4a58..(there are 12 other numbers and letters)..grub rescue> (flashing cursor)

the recovery process backed up the files on the c drive

what do I need to do to get the netbook to start up using the ubuntu or xp operating system and then view the data on my hard drive.

---

### Post by varunendra on 2013-06-20
> **Alphonso Whitfield said:**
> what do I need to do to get the netbook to start up using the ubuntu or xp operating system and then view the data on my hard drive.

Welcome to the forums Alphonso !

To view and backup your data you should use a Live USB flash drive.

Regarding the recovery disc, some discs rely on the recovery partition on the internal hard disk drive itself and thus may not work if that partition is missing or even if the partition structure has changed on the hdd.

Recovery discs are only guaranteed to work if they contain an image of the OS on themselves, not rely on the image stored on the hdd. But such 'full' recovery discs tend to overwrite entire hdd, thus destroying any existing data on it. Since you say it 'backed up' data on C:, I doubt if it is a full one.

In any case, you should back up your important data on an external drive using a live flash drive, then probably the best thing to do would be to run Boot-Repair to possibly fix the problem, or at least generate a report of the current status of the partitions and the os on it : [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Please note that the Boot-Repair CD is like a normal Live CD itself that you can also use to view and backup data. Or, if you already have a live cd or iso of Ubuntu, you can just install it on the live session. Of course you will need a working computer to create a live USB if you don't already have one.

---

