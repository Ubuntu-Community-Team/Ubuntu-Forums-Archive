---
title: "Getting XSane to Find A Scanner"
date: 2015-01-21
forum: Installation &amp; Upgrades
---

### Post by SpikeLS6 on 2015-01-21
I am using XSANE .998, the newest version as far as I know.

I am trying to locate a Canon D530/560 printer/scanner/copier, but neither XSane nor Simply Sane will find it. Consequently, the initial screens of either program do not come up; just gives me an error with one of six things that may be wrong.

This is a USB scanner. I know that my: vendor=0x04a9 [Canon Inc], Product=0x2775 [D530/D560], and libusb:003:004.
The SANE Back end is: 1.0.24.

I have added to my PIXMA.conf file:
#CANON D530
usb 0x04a9 0x2775

I have added to my PIXMA.conf~ file:
usb 0x04a9 0x2775 CANON D530

I have tried the SANE Devel site, but neither of my emails work. The Moderators can not diagnosis why that is. So I though I would try the Ubuntu Forum.

Any ideas on getting XSane or Simply Sane to find this scanner device?

---

### Post by SpikeLS6 on 2015-01-26
After all the homework I did searching the Forum and learning things from the XSane site, I did a lot of configuration changes. Nothing worked until the last Automatic Update that came in. It contained an API file for Scanners, so after the Update completed, I let Xsane try to find the scanner. It worked! I have played with scanning different text and picture formats that I learned how to do from a Utube video.I could not find a GUI "How to Use Xsane Manual" anywhere. What ever the Scanner API added or changed, it was able to find and use my Canon D530 Scanner. This will save an enornous amount of time not having to go back into Windows when I need to scan something.

I will mark this Thread as [SOLVED].

---

### Post by will_3 on 2015-08-09
I tried to update but it does not work for me. I use this link [http://forums.linuxmint.com/viewtopic.php?f=51&t=194081&p=1006693&hilit=rolf+bensch#p1006693](http://forums.linuxmint.com/viewtopic.php?f=51&t=194081&p=1006693&hilit=rolf+bensch#p1006693)
Could you list the steps for what you did to make it work. I am using Linux mint 17.2. My canon d530 can print but the simple scan can not find the device. Thank you!

---

### Post by SpikeLS6 on 2015-08-11
The January 26th reply mentions an update that came in with an Xsane API update. That combined with all the things I went through prompted the scanner to work. I often still have to turn the scanner off then on again each time I use it, as Xsane seems to forget it just used the scanner and is looking for a new one. I have to reboot the scanner almost every time. I can not make a list of what I did, because there was so many changes and constantly trying different configurations. Wish I could help more.

---

