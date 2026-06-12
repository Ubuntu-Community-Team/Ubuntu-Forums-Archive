---
title: "Windows + Ubuntu 11.10, LUKS full disk encryption alternative installation"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by liherb on 2011-10-14
I am currently using my netbook running on Windows XP. I want to install Ubuntu 11.10 onto a LUKS full disk encrypted partition. I've tried this before with Ubuntu 10.10, has anybody tried this with Ubuntu 11.10? If possible, could anybody please provide a step by step guidance here? Thanks.

---

### Post by liherb on 2011-10-20
Has anybody ever tried LUKS full disk encryption with Ubuntu 11.10? I mean, netbook is especially vulnerable at rest, so full disk encryption is a highly desirable feature. If Unity aims at netbook sector, why does it not support full-disk encryption? Thanks.

---

### Post by mastablasta on 2011-10-20
Unity is a desktop interface and has nothing to do with disk encryption.
 
don't know much about LUKS but Truecrpyt works. [http://www.truecrypt.org/](http://www.truecrypt.org/)
 
 I guess LUKS (Since it was made for linux) should work too. 
 
> LUKS is also cross-platform standard. Thanks to [FreeOTFE]("http://freeotfe.org/"), you get LUKS for Win32. Of course, you have to use a file-system on your LUKS partition that both OS understand to actually make use of this cross-platform capability (either use ext2fs drivers for windows or use FAT drivers for Linux). 

---

### Post by liherb on 2011-10-20
Unfortunately no. Ubuntu Unity does not by default support LUKS installation, you have to go through something called alternated installer, and it is much formidable learning curve. An ordinary user probably has to expose his or her netbook to undefended mode.  By the way, TURECRYPT does not support dual system, as far as I know. Some expert here may update our knowledge base here. Thanks.

---

### Post by Felonious Punk on 2012-02-15
TrueCrypt does not do full-disk encryption on linux, only filesystem-within-a-file. LUKS can do both on both Windows & Linux.

I'm actually trying to do a 11.10 install with a fully encrypted / and only /boot left in plaintext. I'm not finding any guides yet written, I guess I'll type up the process to make it easier for folks.

---

