---
title: "Experiencing difficulty installing Keryx"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by Lethaniel on 2010-12-21
Hi there Forum,

I decided to take a second dive into the Linux pool last night by dual booting Ubuntu and Windows 7 onto my PC.  After a short time, I had (and still have) everything working just fine.  The exception is my internet access.  I'll explain:

I'm running a wireless connection in my home.  The router and modem are in the other room and therefore, on Windows 7 I have used a USB Wireless N network adapter to receive the internet signal wirelessly.  In order for the USB adapter to operate on the computer, I've had to install a bit of software from 'Netgear' on Windows 7.  The software is contained in an .exe and therefore, I'd assume I need Wine to run this file and install the software on Linux.  Herein lies the problem:  I have no internet access on the Linux-side of my PC because of the 'Netgear' .exe software and I am unable to install Wine via web browser.  **It seems that Keryx is the solution to my problems but once I open the keryx/linux directory contained in the Keryx zip file, Ubuntu is unable to read the keryx icon.  **

Instead of initiating the Keryx UI and allowing me to create a new project, a new window appears prompting me to select a program from an empty list to run the keryx file.  Are there any file readers I may be missing which I need to run this keryx icon, or is there some error I'm making along the way?

Thanks for any/all help!

---

### Post by Lethaniel on 2010-12-21
Something else:  I'm not loading Keryx onto a pendrive via Windows 7 and then extracting it from the pendrive via Ubuntu - I am saving the Keryx zip file onto my /c drive on Windows and accessing that drive via Ubuntu to get to the Keryx zip.

Not sure if this would make a difference, but it was a step I omitted from the OP.  Many of the tutorials/guides include a "extract from pendrive" step or some step involving a pendrive motion so this may or may notfactor into my issue.

---

### Post by dino99 on 2010-12-21
welcome,

ubuntu (linux) work differently with drivers: they are kernel builtin modules, so no need of netgear exe here.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by Lethaniel on 2010-12-21
Hi dino,

Thanks for the info on the kernel difference.

I visited the link you provided but I became slightly overwhelmed after several minutes of browsing.  I'm sure if I was more accustomed to Linux, I'd quickly realize that the answer is staring me right in the face when I look at the linked site, but the solution is not too obvious for me at the moment.  

When I visit the site, is there something in particular I should be looking for?  A dependency or a terminal command, or something else? 

Thanks for the help again.

---

### Post by Laysan_A on 2011-01-12
Hi Lethaniel,

I'm sorry no one got back to you. It's been three weeks, so I'm sure you've moved on...Just in case: You cannot load windows drivers with wine, so keryx probably isn't the issue. You need to post either in the absolute beginner's section, or the section dealing with wireless. Ask about getting your wireless up, and include information about the specific model of your adapter.

---

