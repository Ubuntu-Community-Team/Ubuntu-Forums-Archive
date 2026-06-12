---
title: "Can't install Ubuntu 10.04"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by dj_ee3 on 2010-05-03
I want to install Ubuntu but I can't. When I boot the cd I see the normal menu that let me chose try without install install check disk ect. but when I click one of them my monitor turns off and I can't see anything really. I can't turn the monitor on unless I shut down the computer and start it up  again. Thank you for helping me in advice.

---

### Post by dj_ee3 on 2010-05-04
no one can help me? :(:(

---

### Post by jvbn on 2010-05-04
Did you burn your iso CD at the lowest possible speed? This is usually advisable and it seems to prevent some installation errors. I haven't got much experience on these things, so I cannot say anything else that may be of help. Sorry!

---

### Post by b4nn1k on 2010-05-05
I am actually having the same issue doing a dual boot windows7 and ubuntu 10.04 run the installation cd get to pick english and tried nomodeset it will try to start the installer and then my monitor shuts off and i cant do anything besides reboot my machine.

---

### Post by windowsfree on 2010-05-05
experiencing the same thing with an old Gateway mx6030 laptop.  I tried the alternate install and had the same situation with that.  I burned the CD twice once at 20X the other at 12X.
Any suggestions ?  (it appears to be when it gets to the graphic drive install, because I see a bunch of color bars flash on screen before it goes black.

---

### Post by aphx on 2010-05-05
Try ticking acpi = off, noapic, nolapic or whatever in the options (main menu), I have managed to do it that way.

---

### Post by b4nn1k on 2010-05-05
Yeah tried that as well no luck still after selecting language turning those off or whatever it goes to the purple ubuntu screen like its trying to load the installer stays there for a couple mins and then the screen goes black. Anything else to try?

---

### Post by windowsfree on 2010-05-05
Ditto, checked them all off, didn't help.  Any suggestions.  BTW, I burned another disc at 4x.

---

### Post by dmp2010 on 2010-05-06
My guess is that the CD is no good. I had downloaded 9.1 couple of times, 10.04 couple of times (with Win 7). But nothing worked until I downloaded it different computer (with XP). I am not sure if there is any connection with Win7/XP, but it's working now. So, download it at different location or ask someone to download it for you and try.

---

### Post by ronparent on 2010-05-06
For some reason I could not install 10.04 unless I unplugged one monitor. After install I was able to install a restricted driver and plug the monitor back in. Both my monitors use dvi plug in's and it had to be a specific monitor unplugged, not just one of them.

---

### Post by dr21 on 2010-05-06
Having the exact same problem with a Dell 700m. Can't get past the Ubuntu logo screen, so I downloaded and installed Xubuntu 9.10 from USB thumb drive, which works great. I downloaded 10.04 twice and burned several disks. Also tried the nomodeset, but still no luck. I'll try again in a few weeks, maybe the bugs will be worked out.

---

### Post by windowsfree on 2010-05-06
Been there - done that, still no good.  It has to be a software/hardware issue, but I have no place to start.  turned off acpi and all those options - still no good.  I can't believe since I had 9.10 on this laptop, removed it because of random freezes, I can't get 10.04 on here.  Anyone with other suggestions.  Spent about 35 minutes on google and another 45 minutes on this forum, but nothing is working.
Thanks

---

### Post by windowsfree on 2010-05-06
> **dmp2010 said:**
> My guess is that the CD is no good. I had downloaded 9.1 couple of times, 10.04 couple of times (with Win 7). But nothing worked until I downloaded it different computer (with XP). I am not sure if there is any connection with Win7/XP, but it's working now. So, download it at different location or ask someone to download it for you and try.

Tried that, even went to a friend with Windows and another with a Mac.  Still no good.
getting very disappointed with this release.

---

### Post by Radly on 2010-05-06
I'm also having a problem with the 10.04 CD.  I SHA-summed the image to make sure it was right, then tried the "Check Disk" option on the installer and THAT crashed with the following output (timestamps and about 15 lines in the middle omitted for brevity):

 Call Trace:
   [<c0588f42>] ? printk+0x1d/0x23
   [<c0588e7a>] panic+0x48/0xf3
   [<c014ec0d>] forget_original_parent+0x2bd/0x2c0
   [<c014ec23>] exit_notify+0x13/0x170
   ...
   [<c058d980>] ? do_page_fault+0x0/0x3a0
   [<c058b983>] error_code+0x73/0x80

I re-installed 8.04 just to convince myself that the new graphics card and hard drive I just installed are actually working, so I'm pretty sure it's the installer CD.

---

### Post by dai_bach on 2010-06-16
I've been having a similar problem installing 10.04 to my Dell Latitude.  With either the install CD that I burned or the USB install disc I get beyond the options menu and the screen goes blank (and black).  There is no hard disc or cd activity either.

---

### Post by Pharum on 2010-07-24
i have the same issue with ubuntu 10.04 and win 7 but in my case i use pendrive to boot - the boot menu show up nicley i choose option install with out installation ubuntu boots up as it should com up with desktop and x server i see glimps of my windows 7 pulpit few tray icones and part of the program i'm bean using before restart - but the whole thing is freezed dead and it cant be done anything over powering down.

maby it will help to find solution.

---

