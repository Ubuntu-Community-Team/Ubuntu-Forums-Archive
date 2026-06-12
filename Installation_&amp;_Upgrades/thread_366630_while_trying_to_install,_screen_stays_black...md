---
title: "while trying to install, screen stays black..?"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by azki14 on 2007-02-21
ok, im new to kubuntu right, anyway, i put in the cd, it all loads up i click start or install kubunutu, and after loading for ages, the screen goes and stays black, then i hear music, possibly the intro music, ive also tryed using safe graphics mode, and to no success, also ive tryed every resolution !, heres my specs

AMD 2000+ @ 1.89GHz
1.0GB DDR400 Ram
ATi X1600 Pro [256mb]
60gb Hdd
160gb Hdd

---

### Post by mikewhatever on 2007-02-21
Can you type on that black screen? If so try typing 
sudo dpkg-reconfigure xserver-xorg
that should bring up an option to manually reconfigure xserver. Try choosing ati or vesa video driver.
If you can't type, try hitting Alt+Ctrl+F1
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

---

### Post by aberry5555 on 2007-02-21
as mikewhatever says, it's probably the graphics drivers. Try that but don't use the "ATI" drivers as, out of experience myself, they don't work with the X series cards. Try either "vesa" or "radeon"

---

