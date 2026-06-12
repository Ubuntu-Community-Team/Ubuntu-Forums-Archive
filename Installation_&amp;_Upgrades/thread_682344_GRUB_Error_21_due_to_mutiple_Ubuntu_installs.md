---
title: "GRUB Error 21 due to mutiple Ubuntu installs"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by Logicone on 2008-01-29
Being a long time Windows user, I've never had much experience with multiple OS's on a single machine until recently. Hearing from my friends about how nice Ubuntu is, and experiencing it for myself, I decided to set my XP machine up for multi boot. No problems, even with the triple hard drives. Being a student at a CISCO academy, and working with servers for the first time, I also decided to install Ubuntu 7.10 server to allow me to experiment from home. This is where I first encountered problems with GRUB.

Upon my first reboot, GRUB came up with an Error 21 - hard disk not found. The process for fixing the problem was long, complicated, and lost to my memory, ending when I decided that enough was enough, and reinstalled my original copy of Ubuntu 7.10, and blowing away 7.10 server in the process. Recently, I decided to try again for a multi-boot machine, this time interested in gOS, which I understood worked off a modified version of Ubuntu, forgive me if I'm wrong. The installation went fine with gOS, up to the point where I went to reboot. Imagine my horrified look when, instead of giving me my options to boot Ubuntu or XP as normal, GRUB failed to load with Error 21. Is there anyway to repair the error without damaging either Ubtuntu or gOS in the process?

If it makes a difference, both Ubuntu 7.10 and XP are installed to the master hard drive. gOS and 7.10 Server were installed to the third hard drive.

Thank you in advance.

---

### Post by David Ostrom on 2008-01-29
Have you tried doing a live CD without the install to see what is going on? I've thought of doing that if I ever had a problem like your having. I don't know if it's possible or not, but it's worth giving a try. Let us know what you find. David

---

### Post by Logicone on 2008-01-30
It took a bit of digging, but I did find something that might have caused the problem. Both gOS and 7.10 have copies of GRUB. Otherwise, to be perfectly honest, I'm not completely sure what exactly I'm looking for. I have no experience at all with GRUB.

---

### Post by logos34 on 2008-01-30
I would try [reinstalling grub to mbr]("http://ubuntuforums.org/showthread.php?t=224351"), pointing to your ubuntu 7.10 partition on the master hard disk).  Then add [configfile]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile") entries to the menu.lst for gOS and server.

---

### Post by Logicone on 2008-01-30
That worked mostly perfectly. I'm still attempting to locate where exactly the gOS install is, but now I can do it in 7.10 Ubuntu rather than off a Live CD. Thank you for your assistance!

---

