---
title: "grub question"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by Namarpus on 2011-05-20
I have a desktop pc with three hard drives:

160 gb with windows XP
500 gb used for data and archives
40 gb with Ubuntu 10.04 and Zorun 4

Grub currently defaults to boot Ubuntu

I want to make changes to boot XP as default.

What file(s) do I need to edit to make necessary changes?  In the older distros I knew how to edit "menu.1st" to get this done.  The newer distros must have a different structure because I can not find a menu.1st file. 

All help appreciated ... Mike

---

### Post by Quackers on 2011-05-20
Here is a guide about making changes to grub. I believe what you want to do is change the GRUB_DEFAULT=0 line by changing the "0" to the correct number as described.
Please note that some changes are dependent on your exact grub version. You can find that out by looking at the top of the grub menu.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Rubi1200 on 2011-05-21
The link provided by Quackers is really fantastic, but if you want a nice GUI application to do this, check out Grub Customizer, which can do the same thing:
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by Namarpus on 2011-05-21
Thank you very much ... that was what I was looking for.

---

### Post by Rubi1200 on 2011-05-22
No problem, you are more than welcome :-)

Please mark this Solved using the Thread Tools near the top of the page.

Enjoy!

---

### Post by Quackers on 2011-05-22
Niiiiiiiiice :-)

---

