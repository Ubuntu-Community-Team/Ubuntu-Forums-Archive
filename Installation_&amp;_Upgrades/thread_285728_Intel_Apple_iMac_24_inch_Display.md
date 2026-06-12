---
title: "Intel Apple iMac 24 inch Display"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by felixdzerzhinsky on 2006-10-27
I am trying to get a decent display on my 24 inch iMac running Ubuntu in a Parallels virtual machine. 

I get a pretty bad detected display. Only 1024 X 768. The iMac shows 1920 x 1200 with millions of colors. It does not tell me the display rate. 

It would be helpful if some knowledgeable iMac user posts their Xorg file.

Thanks

---

### Post by felixdzerzhinsky on 2006-10-28
sudo dpkg-reconfigure -fgnome -phigh xserver-xorg

I chose vesa and my display of 1920 X 1200.

Got idea from this thread:

[http://ubuntuforums.org/showthread.php?t=280190](http://ubuntuforums.org/showthread.php?t=280190)

---

