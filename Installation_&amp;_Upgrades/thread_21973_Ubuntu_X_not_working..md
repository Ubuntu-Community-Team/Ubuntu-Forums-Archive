---
title: "Ubuntu X not working."
date: 2005-03-24
forum: Installation &amp; Upgrades
---

### Post by Francisco on 2005-03-24
Hi,

 I can't startx  :-( just after it downloaded all the packages from the net (install phase), rebooted and never worked the GDM :(


 A pic of the last lines of 'startx'

[IMG]http://img233.exs.cx/img233/6887/image0454dz.jpg[/IMG] 

  [-o< for it to work

---

### Post by daniels on 2005-03-25
Edit /etc/X11/XF86Config-4 with nano and change DefaultDepth 24 to DefaultDepth 16; this issue will be fixed for the final release of Hoary.

---

