---
title: "Grub installed to wrong partition"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by dan828 on 2006-10-30
Well, I've got my computer set up to triple boot Edgy, Vista, and XP, with Vista taking up the first HD and XP and Edgy in two partitions on a second HD.  The problem is, I wanted to use Vista's bootloader to keep everything organized (supposedly it'll work with Linux as well, and it's fairly easy to change with EasyBCD), but somehow during the installation of Edgy I either missed the option to choose where to stall Grub, or it didn't ask.  Either way, Grub ended up on the first disk and is running everything-- no big deal, as I can just use it to boot the Vista bootloader and choose Vista or XP there, but I'd really prefer to remove Grub from there and install it on the Ubuntu partition only.  It'd make for a cleaner startup.

So what I'm asking is how do I remove Grub from where it's currently residing and put it on the Ubuntu partition and still have a working system afterwards?

Thanks in advance. :)

---

### Post by Computer Guru on 2006-11-01
Hi, I'm the founder of NeoSmart Technologies & author of EasyBCD.. 

It'll do exactly what you need and then some - really easily too.

Just boot into Vista via GRUB, then download and install [EasyBCD 1.5]("http://neosmart.net/dl.php?id=1").
From within EasyBCD go to the "[Bootloader Management]("http://neosmart.net/gallery/v/neosmart/EasyBCD/1_50/Bootloader+Management.png.html")" screen, and tell it to "Reinstall Vista Bootloader."

Go to the "[Add/Remove Entries]("http://neosmart.net/gallery/v/neosmart/EasyBCD/1_50/Add-Remove+Entries.png.html")" screen, click Linux/BSD -> GRUB -> Add. You can give it a custom name if you like.

At this point, **you must install the EasyBCD 1.51 GRUB Patch**.
Just follow the directions at [http://neosmart.net/blog/archives/273#comment-6764](http://neosmart.net/blog/archives/273#comment-6764).

This last step will no longer be required once EasyBCD 1.51 is released shortly.

Reboot. GRUB will have "disappeared" but the Vista bootloader will be there - and you can boot Ubuntu right from it!

---

### Post by dan828 on 2006-11-02
Thanks for the reply and your work on EasyBCD!  I'll give this a try this weekend-- I'm away from home for work right now.  I'll give you a heads-up on how well it worked.

Thanks again.  :D

---

### Post by Computer Guru on 2006-11-02
Cool, good luck.

If you need any further help with EasyBCD specifically, the official support forums for EasyBCD are at [http://neosmart.net/forums/index.php?getforum=5](http://neosmart.net/forums/index.php?getforum=5)

---

