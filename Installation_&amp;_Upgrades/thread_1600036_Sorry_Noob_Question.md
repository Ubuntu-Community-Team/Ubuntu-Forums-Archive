---
title: "Sorry Noob Question"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by RFXCasey on 2010-10-18
Windows XP pro already residing on my laptop, I installed Ubuntu 10.4 and let it handle all the nasty business of creating a dual boot. Restart the machine and viewing the boot options I would like the  XP to appear first instead of last as it currently shows.

Fired up Ubuntu so I could edit the menu.lst but when I go into /boot/ there is no menu.lst file. OK so then I think XP is creating the boot menu maybe so I go into the boot.ini file and there is no mention of Ubuntu whatsoever. So what incredibly noobish mistake and I making???

---

### Post by JackNocturne on 2010-10-18
You are probably using **GRUB2** , its different from GRUB-Legacy(aka old)

**[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)**

---

### Post by snowpine on 2010-10-18
Ubuntu no longer uses GRUB (/boot/grub/menu.lst) but the new GRUB2. This document will bring you up to speed on the changes:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by RFXCasey on 2010-10-18
Thanks, both you guys are great!!!:-D

---

