---
title: "sudo install can't find printer file"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by Abidel on 2008-09-29
I have tried and retried all the steps to install my printer drive and its cups file also. Below is the resulting message.

sudo dpkg -i mfc5440cnlpr-1.0.2-1.i386.deb
dpkg: error processing mfc5440cnlpr-1.0.2-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mfc5440cnlpr-1.0.2-1.i386.deb

Does any one have any ideas how I can get my amd64 to recognize my printer?

---

### Post by oldos2er on 2008-09-29
Where did you download the file mfc5440cnlpr-1.0.2-1.i386.deb to? You probably just need to "cd" to the appropriate directory.

---

### Post by Abidel on 2008-09-29
All of my download use to go to desktop. Which is where my printer driver downloads are now, but recently most go elsewhere and I can't find those. I just downloaded again and they defaulted to desktop.

---

### Post by Bablefish on 2008-09-29
Hold on first you should say what kind of printer you have

---

### Post by Abidel on 2008-09-29
Sorry, your right! The printer is a Brother model MFC-5440CN,

---

### Post by oldos2er on 2008-09-29
> **Abidel said:**
> All of my download use to go to desktop. Which is where my printer driver downloads are now, but recently most go elsewhere and I can't find those. I just downloaded again and they defaulted to desktop.

 Then run the command "cd Desktop" before running "sudo dpkg -i mfc5440cnlpr-1.0.2-1.i386.deb".

---

### Post by Abidel on 2008-09-29
I did and this is the following responce.

~$ cd Desktop
~/Desktop$ sudo dpkg -i mfc5440cnlpr-1.0.2-1.i386.deb
[sudo] password for andbc2: 
dpkg: error processing mfc5440cnlpr-1.0.2-1.i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 mfc5440cnlpr-1.0.2-1.i386.deb

I made sure is was the correct file, many time!

---

### Post by Abidel on 2008-09-29
I thought I would try it with "--force-all" and this is what I got:

sudo dpkg -i --force-all mfc5440cnlpr-1.0.2-1.i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package mfc5440cnlpr.
dpkg: regarding mfc5440cnlpr-1.0.2-1.i386.deb containing mfc5440cnlpr:
 brother-lpr-drivers-extra conflicts with mfc5440cnlpr
  mfc5440cnlpr (version 1.0.2-1) is to be installed.
dpkg: warning - ignoring conflict, may proceed anyway !
(Reading database ... 149394 files and directories currently installed.)
Unpacking mfc5440cnlpr (from mfc5440cnlpr-1.0.2-1.i386.deb) ...
Replaced by files in installed package brother-lpr-drivers-extra ...
Setting up mfc5440cnlpr (1.0.2-1) ...
 * Restarting Common Unix Printing System: cupsd                 [ OK ] 

I'm not to sure what this means?

---

### Post by Abidel on 2008-09-29
With the idea of "cd Desktop" I've been able to view the cups file to set up the printer. BUT, still not text page showing up at the printer.

Thanks for the help everyone. Any further ideas to finally solve this?

---

### Post by cariboo on 2008-09-29
Have you tried System-->Administration-->Printing, when it comes time to select the driver for your printer, select the driver you just installed.

Jim

---

### Post by Abidel on 2008-09-29
I did that and all four setting still do not work. Usb and network both don't recieve the test page.

---

