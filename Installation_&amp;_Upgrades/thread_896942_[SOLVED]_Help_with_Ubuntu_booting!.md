---
title: "[SOLVED] Help with Ubuntu booting!"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by E-Cecilia on 2008-08-21
[I]I have installed Ubuntu 7.10 on my laptop Pc. When I start the computer, right after the BIOS starts and the big Acer thing appears and the GRUB starts, the screen goes completely black and nothing "seems" to happen. I have to wait around for more than 4 minutes with the screen totally black and then I get the welcome message indicating that I should write my username and password. After that Ubuntu starts off at a normal speed and everything works fine.

What can I do to:
1. Speed up the 4 minutes booting?
2. Actually get the Ubuntu progress bar that should appear after the GRUB process finishes?

Any good help will be appreciated. Thank you very much.[/I]

---

### Post by linux_tech on 2008-08-21
backup menu.ls:
```
 sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup  
```

edit menu.lst
```
 sudo gedit /boot/grub/menu.lst   
```

try removing  the "quiet" word from /boot/grub/menu.lst

tips to speed up boot by disabling unnecessary scripts-
[http://lifehacker.com/software/linux-tip/speed-up-ubuntu-boot-and-shutdown-process-267588.php](http://lifehacker.com/software/linux-tip/speed-up-ubuntu-boot-and-shutdown-process-267588.php)

---

### Post by E-Cecilia on 2008-08-22
[I]I tried to go to the terminal and write down the codes, but when the gedit boot/grub/menu.lst window opened it was completely empty, there was nothing in it.
Do you know what could I be doing wrong? :([/I]

---

### Post by E-Cecilia on 2008-08-22
*Ok. I managed to fix the problem somehow. I wanted to thank you for your help! *

---

### Post by manishtech on 2008-08-22
> **E-Cecilia said:**
> *Ok. I managed to fix the problem somehow. I wanted to thank you for your help! *
Please mark the thread as [SOLVED] and say a thank to the person who solved this by click on the Medal on the post which helped you :)

---

### Post by E-Cecilia on 2008-10-25
This was my salvation. I hope it works for you.

---

