---
title: "Dell Inspiron 5160 goes to flashing screen from install"
date: 2012-01-22
forum: Installation &amp; Upgrades
---

### Post by forcedlogic on 2012-01-22
Hello,

I have a old dell inspiron 5160 that I tried to get ubuntu to load side by side with a windows install. Every time I manage to get the thing booted it gets to the ubuntu 10.xx loading screen and then immediately goes white - red - green.

I assumed it was a problem with the graphics card and followed the instructions listed but nothing has worked. Nothing will get me to even a text log on screen. Can anyone help?

I tried gfx_mode = text
I tried noquiet

I can get to the menu to edit the boot and I can get into recovery. Any suggestions would be much appreciated.

Thank you kindly.

---

### Post by forcedlogic on 2012-01-22
Can anyone help me? I've searched the net and it seems like Dell Inspirons and Linux don't play nice. Since the last post I have tried installing:

Xbuntu Lubuntu and even OpenSuse and none of them work. All come to a white screen when booting and none of them ever get past that screen no matter what options I pick. Is it something wrong with the computer?

---

### Post by Old_Grey_Wolf on 2012-01-22
I have a Dell Inspiron 5100 that I upgraded to 1GB of RAM. I run Xubuntu 11.10 on it. I tried Ubuntu 10.04 and it didn't work very well. 

Does the 5160 have 256 MB of RAM, 512MB of RAM, or did you upgrade it to 1GB?

Did you check the MD5SUM of the iso you downloaded? Did you check that the CD burned correctly?

If you get L/X/Ubuntu to boot you may not be happy with the performance. The Inspiron 5100, 5150 and 5160 laptops are about 8 or 9 years old. It was fine in its day; however, by today's standards it has a slow processor, slow RAM, slow disk drive, slow etc. I keep mine as a novelty.

---

### Post by forcedlogic on 2012-01-22
I ran it from windows directly and then I tried live CD's from the other distro's.

All of them have had the same problem? Do I need to completely nuke the drive to get it to work properly? Even live CD's won't load.

Edit: I upgraded it to a gig a while back.

---

### Post by Old_Grey_Wolf on 2012-01-22
**You do not need to "nuke" the drive!** Don't give up to easily. I have Xubuntu 11.10 running on a Dell Insprion 5100; therefore, it does work.

Did you download it and burn the CD using Microsoft? Did you burn the CD as an iso image at the slowest speed? This link may help you [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto).

Did you change the boot order in the computer's BIOS so that it will boot from the CD?

This link may help you [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing). It is for Ubuntu 11.04. For 10.04 use this link [http://www.psychocats.net/ubuntu/installinglucid](http://www.psychocats.net/ubuntu/installinglucid).

Oh, and by the way, that computer will not support the Unity desktop environment. You will be using Gnome.

---

### Post by forcedlogic on 2012-01-22
I did get to boot from the cd. I completely installed it via windows dual boot but now when I try to boot ubuntu I just keep having the same problem. The loader comes up for like half a second and then proceeds to goto a white screen and then red screen etc. It never shows me the log on.

---

### Post by Old_Grey_Wolf on 2012-01-22
Please answer the questions I asked in my previous posts. Without the answers it makes it difficult for me to help you.

Also, read the links I provided. They may tell you if you need to try to install Ubuntu differently from the way you did it.

Thanks

---

### Post by forcedlogic on 2012-01-22
I installed it using the "Run along windows" method. There was no burning of any CDs. However after I could not get that to run I tried other distro's live CDS...I never tried Ubuntu live CD but I figured none of the other distro's ran using a live CD so why would Ubuntu?

I can get to the boot menu in grub and the recovery by holding shift. That's as far as ubuntu will go on my system.

I am sorry if I am confusing you.

I did not change the bios I didn't have to it dual boots and comes up with pick either windows or ubuntu and I choice ubuntu.

Sorry I will try what you have said to do and burn to a CD and see if that makes any difference.

Thank you!

---

### Post by forcedlogic on 2012-01-22
I've tried both ways listed above and nothing seems to work. The graphic interface will not load period the end.

The normal text interface loads and I felt hope but it was shattered when it got an error during the package install, it gets almost to the end gives no error code and say it can not be installed. So as of right now I guess I would need to reinstall windows because ubuntu will not run on this system.

---

### Post by Old_Grey_Wolf on 2012-01-23
> **forcedlogic said:**
> I installed it using the "Run along windows" method. There was no burning of any CDs. 
...
I did not change the bios I didn't have to it dual boots and comes up with pick either windows or ubuntu and I choice ubuntu.


Are you trying to install Xubuntu with WUBI? If you are, I wouldn't recommend a WUBI install on that computer.

---

