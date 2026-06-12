---
title: "lilo wont dual boot am i doing something wrong?"
date: 2005-02-18
forum: Installation &amp; Upgrades
---

### Post by js42dae on 2005-02-18
my lilo will not allow me to load xp..its still there i know that but when the computer boots up and lilo starts it juststarts linux..please help...thanks ...eric

---

### Post by wallijonn on 2005-02-18
[http://support.microsoft.com/default.aspx?scid=kb;en-us;315233](http://support.microsoft.com/default.aspx?scid=kb;en-us;315233) may work as I figured it out for W2KP & GRUB yesterday. Do **NOT** issue the fixmbr or fixboot command(s) as this will erase LILO or GRUB and make your Ubuntu install inoperative. 

You'll notice that it says to copy ntdetect.com & ntldr to the root (C:\) whereas it seems that on WXP it resides in \windows\system32\config\system\. 

You could try replacing those files to their original directories & see if it fixes it or if the files need to be transferred to the C:\ (root) area.

---

