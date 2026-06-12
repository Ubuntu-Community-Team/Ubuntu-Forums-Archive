---
title: "[SOLVED] Can not select Windows after Update"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by mahinda on 2008-02-24
I am running ubuntu and windows in the same machine. When machine start I can select OS.

I have update ubuntu files. Now when machine start I can't see option of windows to select. In the option now I can see only different mode of ubuntu no windows. please help me. I am new to ubuntu.


Probable I need to mention this also. About sometime I ago one of my friend edited one ubuntu file manually where he changed selection order of OS. After that It work fine until I update ubuntu

---

### Post by logos34 on 2008-02-24
> What NOT to do-  don't paste your Windows entry anywhere inside the automagic kernels list because it will be deleted when you have a kernel update in Ubuntu.

[http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST](http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST)

Put windows stanza OUTSIDE (above or below) the 'automagic' kernels section.

---

### Post by mahinda on 2008-02-24
Thanks, I am new to linux and ubuntu 
What should I do?,    I can edit   /boot/grub/menu.lst   file where I can see this 

# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1

just uncomment these 4 line is enough?

---

### Post by logos34 on 2008-02-25
Copy the example to the bottom, below this line:

> ### END DEBIAN AUTOMAGIC KERNELS LIST

Yes, uncomment and change 'root' line (if necessary) to match yours

---

### Post by mahinda on 2008-02-26
Thanks, I did what you suggested.it is working fine now.

---

### Post by logos34 on 2008-02-26
Ok, great.

Mark thread as 'solved' and enjoy.

---

