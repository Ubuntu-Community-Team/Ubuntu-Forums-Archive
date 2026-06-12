---
title: "Sony Vaio (SVF15N26CXB)"
date: 2015-07-22
forum: Installation &amp; Upgrades
---

### Post by dan508 on 2015-07-22
Hello,

I need some help with some very difficult configuration issues.  My newest laptop that I am currently using came with windows 8.1.  I removed the hard drive and have replaced it with a SSD drive.  The issue that I am having is getting Ubuntu to install.  I was unable to get the display to work using Legacy boot mode and under UEFI it seems to have similar issues.  The computer currently runs Fedora 22 but I want to switch back to Ubuntu.  Does anyone know what I can do to start the system in a failsafe graphics mode or to enable install using the command line?

Please advise I think the major issue is the Nvidia graphics card.

-Dan

---

### Post by watchpocket on 2015-07-22
I would first look into potential problems with your graphics card (and/or graphics driver(s)) -- from within Fedora -- before trying to install anything.

Apart from that, and just as very *general* advice, not knowing more about your issues, I might start here (if you haven't already): [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Boot into Fedora, download Ubuntu 14.04 to a USB stick, boot from the USB stick, take 14.04 for a test drive, check out the various helpful links on that page. 

And after backing up your Fedora system, run the installer from the USB drive.

---

