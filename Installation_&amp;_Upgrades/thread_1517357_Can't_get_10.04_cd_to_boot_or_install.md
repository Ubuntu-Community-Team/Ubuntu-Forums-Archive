---
title: "Can't get 10.04 cd to boot or install"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by supa scoop on 2010-06-24
I'm pretty much a noob to linux, besides installing one or two previous versions just out of curiosity, but I've never had problems like I've had today.

My computer is pretty old but I imagine it can run it fine once I figure all this out (Asus A7n8X-X, 1 GB ram, Radeon 9600, AMD Athlon 1.16ghz). Listing for possible compatibility issues.

Every disc I've burned today (and these were burned on multiple different computers... and multiple linux distros - Ubuntu 10.04, Linux Mint 9) has worked exactly one time before giving me a screen full of errors. 

Example: I burn 10.04, put it in, boots fine. Go to install, so I restart, it gives me errors. I figured it may be the disc. Went on another computer, downloaded the iso again, burned it again... put it in, boots up once, then I can't get it to work after a restart. Same exact thing happens with mint.

With Ubuntu I get the error of "BUG: soft lockup CPU #0 stuck for 61s!" and with Linux Mint I get "Unable to locate package files", "Error: Unexpectedly disconnected from boot status daemon" and a bunch of other errors. (Would go into more detail but I have no idea how to save the logs that scroll by during this.)

Any suggestions on solutions or how to get more detailed info to you guys? I'm dyin' to try this out but it's really frustrating me.

---

### Post by zvacet on 2010-06-25
Did you check [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") and did you check [CD inegrity]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck") after you burned iso?Did you get any errors?

---

### Post by Chame_Wizard on 2010-06-25
Did you install it form the main site?

You can also us [unetbootin]("http://unetbootin.sourceforge.net/") to create a Live USB.

---

### Post by supa scoop on 2010-06-26
I made a live USB with that program but could not get it to boot. Looking up my motherboard I've found a lot of issues with people booting from USB. I just can't get it to work. Changed my BIOS to every USB setting it has (HDD, ZIP, etc) and nothing.

---

### Post by supa scoop on 2010-06-26
Alright, after going back to my old 6.0 disc out of curiosity (which worked fine), I may have forgot to notice/mention that 10.04 is not even displaying a menu with options to run the live cd/check the disc/etc. What could the problem be? Something small that I'm overlooking?

---

### Post by Dex73 on 2010-06-26
I've downloaded 10.04 from two different severs, then burnt them to two CDs, they both gave an error message. This has happened on 2 computers.

---

### Post by Dex73 on 2010-06-26
O.K. seriously I've done 3 downloads of 10.04 from different servers, burned them one a cd-r on 2 different laptops (both with Hardy) using the lowest speed available on Brasero under the burn image option and I'm still getting an error message when I try to boot from the disk. Does Hardy have a problem burning the ISO for 10.04?

---

### Post by avogarden on 2010-06-27
Have you tried to do a minimal install? [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)  I too was having problems installing on an old Gateway laptop with temperamental optical drive.  However, I burned the minimal iso to a CDRW disc and followed the directions.  It worked wonderfully. Here is a link to coach you on the install: [http://www.cs.uml.edu/~aveilleu/projects/ubuntu-minimal/](http://www.cs.uml.edu/~aveilleu/projects/ubuntu-minimal/)

Good luck!):P

---

### Post by supa scoop on 2010-06-27
Bingo. Thanks, man. That seemed to do the trick, got 10.04 minimal installed and seems to be running good.

---

### Post by Dex73 on 2010-06-27
I got md5sum to work in the command line. 10.04 looks great! :)

---

