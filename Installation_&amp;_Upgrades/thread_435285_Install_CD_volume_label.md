---
title: "Install CD volume label"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by shinjukumaster on 2007-05-06
OK, I got Ubuntu Server 7.04 installed. I’d like to install the desktop and maybe Webmin. Anyway, when I do sudo apt-get install ubuntu-desktop it asks for the install CD. I put in the install CD and press enter and it keeps asking for the disk ‘Ubuntu Server 7.04 _Feisty Fawn_ - Release i386 (20070415)’ When I check the CD volume label it reads ‘Ubuntu-Server 7.’ I didn’t see any instructions in the Ubuntu CD burning guide to modify the volume label. Do I need to burn a new CD and write the label verbatim as above or is something else missing? The base software package installed just fine from this CD.

---

### Post by Big Ed on 2007-05-06
> **shinjukumaster said:**
> OK, I got Ubuntu Server 7.04 installed. I’d like to install the desktop and maybe Webmin. Anyway, when I do sudo apt-get install ubuntu-desktop it asks for the install CD. I put in the install CD and press enter and it keeps asking for the disk ‘Ubuntu Server 7.04 _Feisty Fawn_ - Release i386 (20070415)’ When I check the CD volume label it reads ‘Ubuntu-Server 7.’ I didn’t see any instructions in the Ubuntu CD burning guide to modify the volume label. Do I need to burn a new CD and write the label verbatim as above or is something else missing? The base software package installed just fine from this CD.

The desktop is not available on the server install cd.  That's one of the big differences between the desktop install and the server install.  Note that you don't need the desktop on the server to run webmin.  You can access it from whichever machine you have that has a graphical browser.  Which is, of course, one of the advantages of using webmin.  I do it this way.  My server sits in the basement and I rarely have to go down to do anything locally.  I run everything from my main desktop machine.

If you really want the desktop on your server, edit /etc/apt/sources.list and comment out the line for the cd.  Then you should be able to pull it in from the internet.

HTH,
Ed

---

