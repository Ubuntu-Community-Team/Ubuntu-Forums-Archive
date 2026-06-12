---
title: "Ubuntu 12.04 64 bit booting into low graphics mode"
date: 2014-05-01
forum: Installation &amp; Upgrades
---

### Post by akhil-dmx on 2014-05-01
My Lenovo T430 running Ubuntu 12.04 64 bit which recently got updated via package manager, now always boots with system running in low graphics mode. By doing crtl+alt+f1 I can go into terminal mode and access the system but the desktop never appears. I tried command startx which gave me an error exactly like the one here:
 [http://www.linuxquestions.org/questions/gentoo-87/x-won't-start-no-matter-what-i-try-intel-hd-graphics-i3-1st-gen-884695/](http://www.linuxquestions.org/questions/gentoo-87/x-won't-start-no-matter-what-i-try-intel-hd-graphics-i3-1st-gen-884695/)

I have already spent half a day on this, Please help.

---

### Post by squakie on 2014-05-01
Well, the link is showing the log file - what do you get on your screen when you do startx?  Also, once you've logged in, type:

lspci | grep VGA

Post those results back as well as the information on the screen when you do startx.

---

### Post by squakie on 2014-05-01
Also, when 12.04 was upgraded, what version did it upgrade to?  What are your hardware specs?  Since 14.04 is the new LTS, you may want to consider booting off a livemedia (dvd or usb), backing up anything you need, then install 14.04 from scratch.  Depending on the upgrade, it is quite possible somethings got lost or overwritten.  You can also try adding "nomodeset" as a boot option.

---

### Post by akhil-dmx on 2014-05-01
Thanks for your response...output of lspci | gep VGA is
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphicss Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [NVS 5400M] (rev a1)
 
When I do startx now, I see Fatal server error Server is already active for display 0

X10: fatal 10 error 11 (resource temporarily unavailable) on X server ":0"
after 7 requests (7 known processed) with 0 events remaining. I have to stick to 12.04 LTS as this is the preferred platform for my project.

---

### Post by akhil-dmx on 2014-05-01
I was able to resolve this issue by removing lightdm and installing gdm.

---

