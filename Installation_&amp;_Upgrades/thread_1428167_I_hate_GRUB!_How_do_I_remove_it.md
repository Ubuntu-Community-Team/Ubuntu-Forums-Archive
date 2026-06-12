---
title: "I hate GRUB! How do I remove it?"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by MacManDan on 2010-03-12
Hi all,

Basically this is my problem:

1.) I want to remove Ubuntu and Grub and have only Windows XP on my PC again. (Remember the good old days?)

2.) I want to put the Ubuntu partitions back into Windows partition. I need the space.

3.) I can't use an XP disc because I don't have one. *(No. Neither does anyone else I know.)*

4.) FIXMBR isn't working... am I doing something wrong and what other options do I have?

5.) Does anyone know how do this without removing all my files on the XP? I can't afford to backup everything on my XP. I CAN'T!

**If anyone can help me with this: I will be your friend for life!**

Thanks,

MAC-MAN-DAN ;)

---

### Post by ajgreeny on 2010-03-12
Sorry you're leaving Ubuntu, but the best way to do it without an XP install disk is to download and burn a copy of Supergrub, boot to that CD and then use it to fix your windows MBR.

You can also do it by using the live Ubuntu CD, installing lilo to that and then using the ms-sys.
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```always assuming your windows is on a partition on sda, of course.

---

### Post by coffeecat on 2010-03-12
Another easy way of repairing the Windows MBR (which removes grub stage 1) is to use [SuperGrubDisk]("http://www.supergrubdisk.org/").

In its menu there are two entries for Windows. One to simply boot into Windows. The other to repair the MBR and then to boot into Windows. Once you've run repair/boot option you don't need SGD and Windows will boot up as it did before you installed Linux.

**Edit:** Oops! Didn't read ajgreeny's post carefully enough before posting. Anyway, I've given you the link for SGD.

---

### Post by ronnielsen1 on 2010-03-14
One and only post, He gave it a try didn't he?

---

### Post by kellemes on 2010-03-14
> **ronnielsen1 said:**
> One and only post, He gave it a try didn't he?

Indeed he did.
And I'm sure he's gonna tell the world Linux sucks..

---

### Post by sevenX on 2010-03-14
Just for the record, I found this thread very entertaining :D

---

