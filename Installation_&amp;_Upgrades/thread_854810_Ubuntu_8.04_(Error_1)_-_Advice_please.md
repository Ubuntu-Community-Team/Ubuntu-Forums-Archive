---
title: "Ubuntu 8.04 (Error 1) - Advice please"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by Andre Ward on 2008-07-09
I installed Ubuntu 8.04 in Windows, and when I reboot after installation and choose to boot Ubuntu. I get this: Error 1: Filename must be either an absolute pathname or blocklist.

I have no idea what do do. I've never dealt with these type of things, this is my first time dealing with Ubuntu and its installation. 

What do I do?


Edit: I'm not using a CD. I downloaded Ubuntu directly from the website.

---

### Post by Pumalite on 2008-07-09
Check your menu.lst:
[http://users.bigpond.net.au/hermanzone/p15.htm#1](http://users.bigpond.net.au/hermanzone/p15.htm#1)

---

### Post by Andre Ward on 2008-07-09
I still don't understand how to adress the problem. 

I don't know how or where to type the commands I need to execute.

---

### Post by Pumalite on 2008-07-09
Backup first (at the Terminal)
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
Edit:
gksudo /boot/grub/menu.lst
Review it for errors in syntax (refer to link in my prior link)

---

### Post by Andre Ward on 2008-07-09
Pumalite, thanks for the information. But please understand I'm kind of clueless and I need step-by-step exact instructions on this. 

I need to know where do I go to execute your instructions, and how do I execute them.

---

### Post by Pumalite on 2008-07-09
Boot your Live CD and post:
sudo fdisk -lu (from Terminal) Copy and paste command then press 'Enter'. Copy and paste here the output.
Applications>Accessories>Terminal

---

### Post by Andre Ward on 2008-07-09
Pumalite, I'm not using a CD. I downloaded Ubuntu directly from the website.

---

### Post by Andre Ward on 2008-07-09
Some assistance please.

---

### Post by Andre Ward on 2008-07-10
Bringing this back up to the first page.

---

### Post by Andre Ward on 2008-07-10
Why won't anyone help?

---

### Post by avtolle on 2008-07-10
Since you decided to do a Wubi install, see [https://wiki.ubuntu.com/WubiGuide#head-c6f30accbf2980929f0f2d7f0ed4a38d80a29f2c](https://wiki.ubuntu.com/WubiGuide#head-c6f30accbf2980929f0f2d7f0ed4a38d80a29f2c) and also navigate to the Wubi Forum to see if there are any threads there which will help.

---

### Post by Andre Ward on 2008-07-10
Okay, thanks.

---

### Post by Andre Ward on 2008-07-10
There's nothing related to my problem either on the link you sent me or on the other forum, I still need help.

Anyone know anything else?

---

### Post by avtolle on 2008-07-10
My only suggestion is to uninstall Ubuntu under Wubi (the Wubi guide will show you how to do it); defrag the disk after that; run chkdisk as suggested in the Wubi guide; then, reinstall under Wubi.

---

### Post by Andre Ward on 2008-07-10
Where do I run chkdisk?

---

