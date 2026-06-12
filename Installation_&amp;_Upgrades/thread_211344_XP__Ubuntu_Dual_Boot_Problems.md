---
title: "XP / Ubuntu Dual Boot Problems"
date: 2006-07-08
forum: Installation &amp; Upgrades
---

### Post by prezet on 2006-07-08
Hi

I'm trying to install Ubuntu onto a drive which already has XP installed.
The drive is 120gb.

I have gone through and resized the XP partition. So that XP has 100gb (NTFS), Ubuntu is allocated 14gb (ext3), swap 1gb & a fat32 share of the remainder.

Anyway, I go through the Ubuntu install process, and all is well, however I don't get any kind of prompt about where to install GRUB. It seems to just automatically install it in the MBR ](*,) , so now when I boot I get a GRUB Error 17....

I've tried reinstalling Ubuntu, but it just does the same thing. Am I missing something?

Thanks

---

### Post by Athropos on 2006-07-08
Are you using the Desktop CD? If so, I believe that it does not offer the option to choose where to install Grub. You should then try the Alternate Install CD if you want more control over the installation process.

---

### Post by raldz on 2006-07-08
I don't know about your case, but do you have an anti-virus installed that scans your boot sector when doing a boot up? sometimes changes in the boot sector is identified as virus activity and thus is cleaned by the anit-virus.. but if it is just a GRUB problem, then this link may be of help:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

