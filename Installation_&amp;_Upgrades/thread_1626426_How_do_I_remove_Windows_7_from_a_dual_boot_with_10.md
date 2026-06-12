---
title: "How do I remove Windows 7 from a dual boot with 10.10?"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by patrick2008 on 2010-11-20
About 2 months ago I installed Ubuntu 10.10 on my HP laptop as a secondary OS to Windows 7 Professional. I'm extremely satisfied with this version of Ubuntu and am ready to pay my final respects to Windows, drive in the last nail, and put it in the ground. 

My goal is this: To allow Ubuntu to take up the entire hard drive, thus removing the Windows partition entirely, all without having to reinstall Ubuntu from scratch. Is this possible to accomplish? If so, how?

---

### Post by Quackers on 2010-11-20
If you are sure that is what you want, and you are also sure that you truly have a dual boot system (not a wubi install!) you can delete all the Windowsy partitions with Gparted and then run ```
sudo update-grub
```
If you don't have a Windows installation disc I would take this opportunity to make recovery dvd's from within Windows, as without these there is no way back (without buying! something - officially).
If you then want to use the resulting free space for your Ubuntu installation it is likely that you can do that. Please post a screenshot of your current setup from GParted screen, or post the contents of the results.txt file which is produced by running the boot info script below.

hthttp://bootinfoscript.sourceforge.net/

---

### Post by patrick2008 on 2010-11-20
It is a true dual boot system. I was originally thinking that the deletion of the windows partition and then telling grub o update itself would do the trick, but I didn't think it would be that simple. 

See attached screenshot:
[http://imgur.com/TEwqr]("http://imgur.com/TEwqr")

Thanks for your help.

---

### Post by Quackers on 2010-11-20
Happy Ubuntuing :-)

---

### Post by kansasnoob on 2010-11-20
> **patrick2008 said:**
> It is a true dual boot system. I was originally thinking that the deletion of the windows partition and then telling grub o update itself would do the trick, but I didn't think it would be that simple. 

See attached screenshot:
[http://imgur.com/TEwqr]("http://imgur.com/TEwqr")

Thanks for your help.

Once you delete both Win partitions you'll have no primary partitions at all.

That may cause problems.

---

### Post by patrick2008 on 2010-11-21
This is indeed true. I'm going to just blow the whole thing out and start from scratch. Not desirable, but quite effective. Thanks your your help.

---

