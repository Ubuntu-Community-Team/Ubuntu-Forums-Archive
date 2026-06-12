---
title: "Installing 9.10 from USB CD ROM fails to detect CD ROM"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by pm010537 on 2009-12-16
Hello,

I'm trying to install Ubuntu server 9.10 from a USB CD ROM on a server equipped with intel xeon 3.2 ghz processor.

The box boots nicely from USB CD ROM, goes through the language and keyboard detection dialogues, but then starts asking to select a drive which contains the image: the options do not have CD ROM listed at all. It complains it can't find a cdrom media drive and leaves me with no other option then to abort the instalation.

I am able to install CentOS 5.4 on the same server using the same USB CD ROM. How do I continue installing Ubuntu 9.10 from USB CD ROM?

I am stuck and help of any kind is very much appreciated.

---

### Post by zkriesse on 2009-12-16
Hmm....you could try grabbing the files from the CD itself while in the CD's Live mode and then using the Ubuntu Startup Disk Creator program to make a bootable USB drive and then use that to install. It's a shot.

---

### Post by Carson Dyle on 2009-12-16
I'm having pretty much the same problem trying to install 9.10 server from a USB CD-ROM.  I get to a point in the installation where the installer claims that it can't find a suitable CD-ROM driver.

What files do I need from the CD and how to direct the installer to find them?

---

### Post by Carson Dyle on 2009-12-18
I decided to punt and try installing 8.04 instead.  It installed without a hitch from the same USB CD-ROM drive, so apparently it's a bug in the 9.10 installer.

---

