---
title: "GRUB Error"
date: 2006-09-24
forum: Installation &amp; Upgrades
---

### Post by oscabat on 2006-09-24
I know that I'm not the first person with a GRUB error, but I can't seem to find anyone who has this exact problem:

I have two IDE hard drives: 1 Windows, 1 Ubuntu
I want to format both of them, so I first formatted my Ubuntu one.  Apparently, there must have been some GRUB files on my Windows hard drive as well, as it still attempts to load GRUB (and now I get error 17).  I can't really restore GRUB from either of my hard drives because both of them are NTFS, and I can't mount them (at least, I assume that's why).

What can I do to boot back into Windows?

---

### Post by wieman01 on 2006-09-24
Do you have a Windows 98 Boot CD? Run it and run this command:
> fdisk /mbr

---

### Post by oscabat on 2006-09-24
Sorry I didn't clarify.  I have windows XP.  And I don't have any Windows boot disks/CDs.  Would I be able to do the same thing with like a boot floppy?

---

### Post by gm__ on 2006-09-24
I didnt have the same exact problem but i managed to reinstall grub with SuperGrubDisc.
Just google and download and burn it, its an ISO.

---

### Post by oscabat on 2006-09-24
The Super Grub Disk allowed me to boot back into Windows, so where would I go to make sure I have removed all of the GRUB files so I don't have to have the Super Grub Disk in the CD-ROM every time?

---

### Post by wieman01 on 2006-09-24
You still need to format the master boot record (MBR) of your HD. Win XP won't allow you to do that for you cannot change a running system. So try to get a boot floppy or anything like that that let's you run the "fdisk /mbr" command. That'll do.

---

### Post by confused57 on 2006-09-24
You can make a Win98 floppy boot disk using this guide:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Go to the section for restoring mbr for Windows 98 & Windows XP without an install CD.

You could probably reinstall Ubuntu, which would reinstall grub to the mbr & allow you to boot Windows or Ubuntu.

---

