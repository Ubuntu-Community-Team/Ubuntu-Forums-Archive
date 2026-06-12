---
title: "Modifying Grub"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by atwin on 2009-12-15
hello,

I just installed ubuntu 9.10 and wanted to modify the boot loader priorities.  Unfortunately, I can't find the default files!

They used to be in /boot/grub/menu.lst

Does Anyone know the new location of menu.lst to set the grub boot priorities?

Thanks for the help!


atwin

---

### Post by sisco311 on 2009-12-15
You can set the default menu entry in the /etc/default/grub file.

[uhelp]community/Grub2[/uhelp]
[thread=1195275]The Grub 2 Guide[/thread]
[thread=1302743][COLOR="Red"]Grub 2 - 5 Common Tasks[/COLOR][/thread]
[thread=1287602]Grub 2 Title Tweaks[/thread]

---

### Post by Zebedee050 on 2009-12-15
In 9.10:
 
No */boot/grub/menu.lst*. It has been replaced by */boot/grub/grub.cfg*. 
 
The primary configuration file for changing menu display settings is */etc/default/grub*.

---

### Post by atwin on 2009-12-15
Thanks for the quick replies guys!  I fixed it; although I don't see the point of all these complex new steps!!!  The old configuration was much more user-friendly and "human-readable" !!!

---

