---
title: "Ubuntu 10.04 can't see my hard disk"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by javyn999 on 2010-05-11
Hey all.  I'm trying to install Ubuntu 10.04 amd64 on a system I recently built that currently has Windows 7 installed.  

Strangely, when I booted from the install disk, I got an unrecoverable error.  Ubuntu.com said in that case, try to install from a live session, so I did that.

Live session install worked fine until I got to the partitioning section of the setup.  Nothing displayed in the partition space and all my partition options were greyed out!

I have tried several things.  I tried booting from my Lubuntu 32 bit that I know works (running on my laptop), it could not detect the hard disk either.

I tried booting into Windows 7 and shrinking the partition in the Windows partition manager and seeing if Ubuntu's installer would detect the space that way...no such luck.

cfdisk would not work either.  Gave a big fat cannot access the disk error.

fdisk -l displays nothing.
Gparted from the live session is a no-go as well.  

I'm at my wits end here!  Can anyone help?  

BTW, relevant hardware:

GIGABYTE GA-770TA-UD3 AM3 AMD 770 SATA 6Gb/s USB 

Western Digital Caviar Blue WD5000AAKS 500GB 7200 RPM SATA 3.0Gb/s 3.5" Internal Hard Drive -Bare Drive

I wouldn't think that Ubuntu should have a problem detecting this...

---

### Post by geowtx on 2010-05-11
check this out [http://ubuntuforums.org/showthread.php?t=1310560&highlight=sata](http://ubuntuforums.org/showthread.php?t=1310560&highlight=sata) . I suffered with the same problem this worked for me.

---

### Post by javyn999 on 2010-05-11
thanks, tried that  as well still nothing :(

---

### Post by javyn999 on 2010-05-11
Problem solved.  I tried plugging into a different SATA port.  Apparently the installer doesn't like SATA 6.  (Have a SATA 3 drive, but was plugged into a SATA 6 port).

---

### Post by pepoweb on 2010-09-12
Thank you!

After hours of trying all kinds of stuff to upgrade an AMD64 machine from 8.04 to 10.04 I was about to eat my hat ;-)

Changing the disk to a different SATA-port did the trick.

The machine is installing as we speak!

---

