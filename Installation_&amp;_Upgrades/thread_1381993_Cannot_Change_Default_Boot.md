---
title: "Cannot Change Default Boot"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by willcaddy on 2010-01-15
I have recently upgraded my ubuntu image to 2.6.31.17. since I upgraded the start-up manager dosent work any more. I even tried changing it manually in the \ect\defualt\grub.cfg and it says boot from entry 8 (which is my windows partition) but it still defaults to 0 on boot. what could be wrong? 

Any help would be most appreciated Thanks :-D

---

### Post by darkod on 2010-01-15
It's /etc/default/grub, not grub.cfg. Did you save and close the file after changing it to 8? And don't forget you need to lower the number by one, for example if your windows is 8th in the grub menu, you need to put 7 as default OS value because it starts counting from 0.

After saving and closing the /etc/default/grub file you also need to run:
sudo update-grub

---

### Post by willcaddy on 2010-01-26
that was the file i was editing. i change the defualt value to the one i want and ran update-grub but no change. i looked online abit n i found a command that tells you what grub version u have. i did it n it says i have 0.97. but when it boots it says 1.97 beta 4. this seemed to happen after i updated to 2.6.31-17. also it says vga+765 is depreciated on boot? what could be rong?

Thanks

---

### Post by willcaddy on 2010-01-26
hi everyone. just fixed the problem. i reinstalled grub-pc and then edited the config file n now its fine. thanks for your help :popcorn:

---

