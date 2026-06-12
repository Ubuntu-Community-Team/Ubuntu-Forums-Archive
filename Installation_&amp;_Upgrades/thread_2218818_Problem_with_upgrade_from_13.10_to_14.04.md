---
title: "Problem with upgrade from 13.10 to 14.04"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by borisov87 on 2014-04-22
Hello
I start upgrade from ubuntu server 13.10 to 14.04 ,during upgrade process i receive message for replace 000-default.conf file, i choice (d) for view differences, but after this i can not get out from view difference mode and continue upgrade. Any suggestions?
I try with esc, ctrl+x,end,ctrl+end but nothing.

---

### Post by 3rdalbum on 2014-04-22
It has been years since I upgraded on the command line, but I think you need to press Tab to select the OK button, and then press Space to activate it.

---

### Post by Danger_Monkey on 2014-04-22
3rdalbum is correct, tab and space will move/select the "checkbox".

In case you don't see the differences once you get it installed, the main difference is the DocumentRoot, which is changed from /var/www tp /var/www/html.  So, you will have to edit it or move your directories to the new spot.

---

