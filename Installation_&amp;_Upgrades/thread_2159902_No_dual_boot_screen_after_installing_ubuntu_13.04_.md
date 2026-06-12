---
title: "No dual boot screen after installing ubuntu 13.04 along with windows 8"
date: 2013-07-05
forum: Installation &amp; Upgrades
---

### Post by aayus on 2013-07-05
I just installed the Ubuntu 13.04 alongwith the windows 8. 
But the problem is everytime i start my lappy it automatically loads the Ubuntu and do not show the dual boot option asking whether to load windows8 or ubuntu.

---

### Post by Penguenci on 2013-07-05
Are you sure you didn't erase your Windows installation altogether? Let's hope not. The most likely scenario is that you somehow made a setting such that GRUB doesn't look for the other operating system in the first place. Or the timer may have been set at zero. Try installing GRUB Customizer. If there is a Windows 8 loader intact on your system, it should find it and add it to the boot menu. Also make sure your GRUB isn't set to quiet splash or anything like that. You can also check the timer and ensure it gives you enough time to see and react to the GRUB prompt.

---

### Post by fantab on 2013-07-05
> **aayus said:**
> I just installed the Ubuntu 13.04 alongwith the windows 8. 
But the problem is everytime i start my lappy it automatically loads the Ubuntu and do not show the dual boot option asking whether to load windows8 or ubuntu.

Its a known issue. Use **[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")** to fix it. '*Recommended Repair*' suggested by Boot-Repair will be enough.
In case you still have problems booting after repairing then post the output link that '*BootInfo Summary*' generates.

Good Luck...

---

