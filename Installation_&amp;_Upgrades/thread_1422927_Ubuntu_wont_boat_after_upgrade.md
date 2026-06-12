---
title: "Ubuntu wont boat after upgrade"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by dleong21 on 2010-03-06
I am dual booting Windows 7 and Ubuntu Karmic. After upgrading some packages in Ubuntu and restarting I cant boot into Ubuntu. The first Grub menu appears where I get to choose if I want to boot into windows or Ubuntu. I can pick Ubuntu, but it doesn't go into the second Grub menu, all I get is Grub 1.45 beta (i think, its 1.something). Where I'm then ask for some bash code line thing.

I'm pretty new to Ubuntu and really like it so far, can someone please help me get back into Ubuntu.

---

### Post by oldfred on 2010-03-06
Is this a wubi install. (otherwise I do not think you get two menus)

Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by dleong21 on 2010-03-06
It is a wubi install. I try changing the wubi boot file, but I get the same screen. GNU Grub 1.97 Beta4, and sh:grub>.

---

### Post by slysimon on 2010-03-06
Thanks for the post and thanks to Oldfred  as his link was what solved my problem.
 
Cheers

---

