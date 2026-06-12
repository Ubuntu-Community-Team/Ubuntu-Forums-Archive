---
title: "Why does a new &quot;partition&quot; for ubuntu show up every new update?"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by Jherrera8 on 2010-12-26
It seams like for every update, i get a new option to start up ubuntu 10.10, it says 
"Ubuntu, with linux 2.6.35-24 generic
...2.6.35-23 generic
...2.6.35-22 generic" 
is this normal? and i also have it dual booted with windows 7, so it gives the windows 7 loader option too, any ideas?

---

### Post by aeronutt on 2010-12-26
Yep, normal. Those are kernal updates, and are considered significant enough that if you have problems booting into the new kernal, you can easily select the previous one that worked. Once you get comfy with the new kernal, you can delete the older ones.

eg [http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/)

---

### Post by Quackers on 2010-12-26
Some updates include new kernels which add a new line to the grub menu. If your new kernel boots ok you can uninstall all previous kernels (except one maybe) via synaptic package manager. Just enter 2.6.35 into the search box and mark for complete removal all kernels except the new one and the last one previous to that (as a safety net :-) ). There will be at least 2 entries in synaptic for each kernel number. Check carefully.
After uninstalling the older kernels open a terminal and run ```
sudo update-grub
``` to adjust the grub menu.

---

### Post by 0N3 on 2010-12-26
yes its normal its just a kernel update best to keep @ least the last 2 upgrades if one fails (AKA the newest one) fall back to the previous one which worked

---

### Post by Jherrera8 on 2010-12-26
great thanks guys, this really helps

---

### Post by garvinrick4 on 2010-12-26
If you get to many (always leave 2) and you want to delete them.
Go into synaptics and type it in upper right box.
like 2.6.35-23 or whichever one you want to remove.
right click on it and say remove and hit green arrow to apply action.
See yours by in terminal
```
grep menuentry boot/grub/grub.cfg
```

---

