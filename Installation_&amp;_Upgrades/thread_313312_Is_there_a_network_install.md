---
title: "Is there a network install?"
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by atomictaco on 2006-12-05
I have a couple of computers that I would like to run Ubuntu on.  The problem is I have not been able to get the install CD's to work.  I have tried the Live CD and Alternate both.  Both machines are running newer hardware and the install should work just fine, but the install fails everytime.  It has to be the installer included with the latest version as I know at least 10 other people that have been trying to install Ubuntu from downloaded versions and no success.  Are there instructions anywhere that outlines how to install Ubuntu Edgy from the web?

---

### Post by Shadic on 2006-12-05
Seeing as how I have my own topic of Ubuntu failing to install, I would greatly appreciate it if there was an online option as well.

I also had problems installing FreeBSD on a CD, but FTP went flawlessly.

---

### Post by atomictaco on 2006-12-06
OK, after some research I found an answer.  If you open a mirror and browse the directories there is a netboot folder.  Download the mini.iso and burn it.  This will boot the system and run the install, but it downloads all the packages from the web.  I installed Edgy on 2 computers last night using this method and it worked fine where the CD's I downloaded would not.  I have yet to find any documentation on this method, but I found it to be just as straight forward as a normal install.  Below is a link to one of the directories for the mini.iso:

ftp.iinet.net.au/pub/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/

---

