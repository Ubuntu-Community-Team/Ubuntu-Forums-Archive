---
title: "AMD or NVIDIA problems not sure which"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by jtnickle on 2008-04-27
okay ,so im trying to install the new ubuntu onto my laptop ... i have an AMD 64 turion x2 processor and a nvidia graphics card, im running it all on an HP Pavillion dv 9000, does anyone know any common problems that I'm doing wrong, i made the boot disk and loaded it up , got through the start menu but after what seemed to be the end of the loading lines it goes to a blank black screen, i've waited there for about an hour and it doesnt load up, any ideas anyone?

---

### Post by paleheretic on 2008-04-27
I had this problem - it was the NVidia graphics card drivers. If you hit Escape at the Grub prompt, you can choose recovery, and it will offer yo a menu part way through the boot. Choose reset / fix x-windows config and you should find it works. And don't reinstall the graphics drivers - just breaks it again.

---

