---
title: "Question about &quot;Live&quot; USB and Ubuntu."
date: 2013-06-14
forum: Installation &amp; Upgrades
---

### Post by TNFrank on 2013-06-14
Ok, so I've test driven a few different Op Systems via Live USB over the last couple days. All were ok to one degree or another but none of em' lives up to what I'm experiencing with Ubuntu 12.04LTS. For me it's THE Op System.  So, I decide to clean off my 3 USB thumb drives and install Ubuntu 12.04LTS on my fastest one, a SanDisk 8GB.  I do the install using UNetbootin, give it 2GB for the persistent files and install it.
 On my test run things worked pretty well so I decided to shut down and restart to see if it actually would be persistent.  On my first run I didn't have to give a user name or password and could do sudo without needing a password.  On the re-boot when it hit the desktop screen it ask for a user name and password. I entered what I figured they'd be(i.e. the ones I use for my installed version on my actual computer hard drive) but they were wrong so it was a "no go" at re-boot.
 So, Ubuntu Gurus, what gives?  What didn't I do or what should I have done to get it so that I can carry a nice customized copy of my beloved Ubuntu 12.04LTS with me in my pocket on a USB for use on other computers? Thanks in advance for any help.;)

---

### Post by ajgreeny on 2013-06-14
I have no idea why you got a user and password request when starting a live USB system, but try again and if it happens try user **ubuntu**, and for password leave the box empty, and just hit enter.  However, I think something must be very wrong with your live USB if that password request continues, so you may want to double check the md5sum of your .iso file against the listed value at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes") .  If it does not totally match you need to download again.

---

### Post by TNFrank on 2013-06-14
Thanks for the link, so where do I find the md5sum number of my file at?

---

### Post by Rebelli0us on 2013-06-14
Forget UNetbootin, do a regular install just as if the flash drive was a hard disk, and make sure you tell the installer to put the boot loader on the flash drive.

---

### Post by ajgreeny on 2013-06-14
> **TNFrank said:**
> Thanks for the link, so where do I find the md5sum number of my file at?

There is another link How to MD5SUM on that page.

---

