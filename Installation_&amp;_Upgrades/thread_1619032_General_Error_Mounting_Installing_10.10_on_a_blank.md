---
title: "General Error Mounting Installing 10.10 on a blank HDD"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by MegaZoneEX on 2010-11-11
i am new to The Community :) i always wanted to try out Linux! i am very passionate about open source work and use open source software.

Now My problem...

The Second HDD(the drive i want Ubuntu on) was formatted as a SLAVE on my Standard PC that runs XP on its MASTER drive.

Now instead of dual booting, (2 HDD 1 PC) I put the HDD back in its own PC, making it its own MASTER.

i followed the steps: downloaded Ubuntu 10.10, burn to a CD, etc.

i put the CD in, get the "Ubuntu" load screen for the first time ( waited for it to load).

[Btw the PC i am installing it on is a Dell Dimension 2400 upgraded with 2GB of RAM.]

Then i get this Message:


General error mounting filesystem
maintenance shell will now be started
CONTROL-D will terminate this shell
and reboot the system

i looked around and found that i needed to press CTRL + SHIFT + D but that just reboot :/

---

### Post by MegaZoneEX on 2010-11-11
other messages i get:

/lib/libssl.so.0.9.9.8 cannot read fila data Input/ouput error

and 

usr/bin/python:error while loading shared libraries

---

### Post by sikander3786 on 2010-11-11
Welcome :)

Please first of all check the quality of downloaded image.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the sums match, try burning the disc at the lowest possible speed and try again.

I am pretty sure that it is cause by a corrupt image or bad burn.

Please let us know about your progress.

---

### Post by psusi on 2010-11-11
Boot up the live cd and open the disk utility and take a look at the SMART status of the drive.  It sounds like it is failing.

---

