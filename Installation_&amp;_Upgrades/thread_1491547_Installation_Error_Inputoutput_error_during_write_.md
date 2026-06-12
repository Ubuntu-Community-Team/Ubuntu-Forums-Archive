---
title: "Installation Error: Input/output error during write on /dev/sda"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by Jagon on 2010-05-23
Hi,

I'm trying to install ubuntu 10.04 on my desktop. I would like to erase my old xp completely and have only ubuntu as my os. I boot from cd but when I install it stops at 15% and keeps giving me this error:

Input/output error during write on /dev/sda.

It won't let me retry or ignore and when I cancel the installation continues until I get another error. 

Can anyone help me here?

Thanks

---

### Post by freonchill on 2010-05-23
did you test the cd you burned to verify that its not bad (its an option when it first boots up) - i believe its called "test install media"?

then do the memory test (from the same menu) it loads-up memtest86

if both of those pass, you might want to do a test on your hard drive, if its having problems writing to a sector - it could be that you have issue with your drive (e.g. drive might be dying)

you could run checkdisk or similar
or if you have a copy of spinrite ([www.grc.com](www.grc.com)) you could use that to refresh the sectors on your drive)

---

### Post by Jagon on 2010-05-24
The disk passed the test, the memory test passed and a check disk passed. I'm not sure if my hard drive is dying but that error is really annoying.

I went ahead and just installed ubuntu within windows without dedicating a partition. Will this greatly affect the performance of my computer comparing it with a full install? I read somewhere that I can't hibernate and it may slow it down.

I just can't install it any other way on my computer so that's my last resort.

Thanks.

---

