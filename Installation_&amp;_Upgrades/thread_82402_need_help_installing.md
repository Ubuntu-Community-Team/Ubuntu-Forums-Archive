---
title: "need help installing"
date: 2005-10-26
forum: Installation &amp; Upgrades
---

### Post by twoodcc on 2005-10-26
i have a desktop that i built myself:
AMD Athlon 64 X2 3800+
DFI Lanparty UT nF4 Ultra-D motherboard
dvd-rw drive
GeForce 6600GT
i have 3 HD's

i got an error during "installing base system" from the dvd that i burnt. any ideas?

---

### Post by twoodcc on 2005-10-26
i tried again, and i got this message:
the debootstrap program exited with an error (return value 1)
check /target/var/log/debootstrap.log for the details

then i hit enter for continue and got this error message
the base system installation into /target/ failed
check /target/var/log/bootstrap.log for details

then i hit enter for continue again and got this message:
an installation step failed. you can try to run the failing item again from the menu, or skip it and choose something else. the failing step is: Install the base system

what should i do?

---

### Post by twoodcc on 2005-10-26
can anyone help me out? or should i just give up on Ubuntu?

---

### Post by Koybe on 2005-10-26
Did you check your iso before burning it? Maybe it's the DVD that's wrong. Otherwise try to enter another console (using ALT+F3 for example) and then try to get some information on the file they gave you. 
cat /target/var/log/debootstrap.log

---

### Post by lorenco on 2005-10-26
You might want to try a new CD ??  You can also try to get a LIVE CD and try that first ??

---

### Post by Koybe on 2005-10-26
Look at [this](http://www.ubuntuforums.org/showthread.php?p=414838), you might find intersting informations.

---

### Post by twoodcc on 2005-10-26
thanks for the link. looks like i'm not the only one with this problem. i guess i'll have to burn the image again at 1X and try that

---

### Post by rsriniv on 2005-10-26
I had the same problem with the bootstrap message.

I re-downloaded the iso from a German mirror, burnt the disk, and problem solved.

Seems to be a not uncommon issue with downloaded iso's (had a similar problem with Suse-oss-10.0 iso) :(

---

### Post by twoodcc on 2005-10-26
well maybe i should download from a different source also.

---

### Post by taygan on 2005-10-27
try enabling dma on your dvd drive (you can do it from the expert install.. when it gets to cdrom parameters type in -d1  or, get to the console (alt-f3?) during the beginning of the regular setup and type sudo hdparm -d1 /dev/hdb (or whatever /dev your dvd drive is.)

---

### Post by twoodcc on 2005-10-27
well i downloaded it again and burnt another disk at minimum speed. here goes nothing. i will try the dma if i still can (already started)

---

### Post by twoodcc on 2005-10-27
well it seemed to install and everything, and then it spit out the dvd, and when i restarted, it said "error loading operating system"

what should i do?

---

### Post by twoodcc on 2005-10-27
well i think it was my SATA drive. i also have an IDE hard drive (PATA i guess some people call it) and it's installing packages now. hopefully everything will be fine now

---

### Post by twoodcc on 2005-10-27
well it's installed and running.

---

### Post by taygan on 2005-10-27
what brand of SATA do you have?  I had too many problems with my Hitachi Deskstar SATA (120? I can't remember..  It's all partitioned up) and ASUS a7-v600x motherboard giving buffer i/o errors on the drive with the breezy install so I gave up and reinstalled hoary.  The drive is good, so I will wait a few months and see if some bugs are ironed out (or if someone figures out a work-around) and try installing again.

---

### Post by kiwifish on 2005-12-10
:D I also have a BenQ DVD drive and was having the same problem as the poster. The '-d1' flag worked for me. Thanks.

---

