---
title: "What is the latest kernel version?"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by SoFl W on 2010-09-01
Twice now I have received update notices informing me of header upgrades which I installed, both required a restart of the system.  Usually when this happens there is an additional item in the grub menu.  The last two times this has happened I didn't get an additional menu item.  
What is the latest stable version?  I am currently running:
[COLOR=Navy]
2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux[/COLOR]

I did try a "sudo update-grub2" and the menu didn't change.

---

### Post by andrewthomas on 2010-09-01
[             2.6.32-24.42]("https://launchpad.net/ubuntu/+source/linux/2.6.32-24.42")

for packages linux-image, linux-image-generic, and linux-image-2.6.32-24-generic

---

### Post by SoFl W on 2010-09-01
Thank you, looks like I have/had the latest.  I wonder what required the reboot if it wasn't a kernel change.

---

### Post by marl30 on 2010-09-01
Mine says 2.6.35 -14

---

### Post by NightwishFan on 2010-09-01
Ubuntu Lucid tracks the 2.6.32 kernel. The next Ubuntu version, which is still in development will use the 2.6.35 kernel. You can check the latest version of the upstream (not ubuntu) kernel here:
[http://kernel.org/](http://kernel.org/)

I do not advise installing a newer kernel for Lucid though it is possible and may work well.

---

### Post by marl30 on 2010-09-01
> **NightwishFan said:**
> Ubuntu Lucid tracks the 2.6.32 kernel. The next Ubuntu version, which is still in development will use the 2.6.35 kernel. You can check the latest version of the upstream (not ubuntu) kernel here:
[http://kernel.org/](http://kernel.org/)

I do not advise installing a newer kernel for Lucid though it is possible and may work well.

I think I may of gotten this version from some PPA I've added. Everything seems to be working ok, except for VMware.

---

