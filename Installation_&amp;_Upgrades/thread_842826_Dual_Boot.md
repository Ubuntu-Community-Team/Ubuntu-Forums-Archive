---
title: "Dual Boot ?"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by MosquitoDH98 on 2008-06-27
If I fit two new Hard disk drives to my desktop pc, and install Win XP on one and  Ubuntu on the other, will the boot loader allow me to select which drive to boot from, without having to enter "Safe Mode" every time I switch on to select which drive to boot from

---

### Post by Pumalite on 2008-06-27
Grub Menu will allow you to choose the OS.

---

### Post by logos34 on 2008-06-27
yep, if you install in that order (win first, linux second).  Grub will detect windows and add a boot entry to the menu.

---

### Post by radical3 on 2008-06-27
> **logos34 said:**
> yep, if you install in that order (win first, linux second).  Grub will detect windows and add a boot entry to the menu.

yup i can vouch for that, thats exactly what i have set up

---

### Post by Pumalite on 2008-06-27
Here is a guide:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by logos34 on 2008-06-27
radical3,

your avatar is hilarious! (and true)

---

### Post by lisati on 2008-06-27
> **radical3 said:**
> yup i can vouch for that, thats exactly what i have set up
+1
One piece of "finnessing" I've done on my dual-boot desktop is to make the grub menu hidden, so that a casual user who doesn't think to press the "Esc" key while Grub is doing its stuff won't see Windows as an option but will automatically be presented with the Ubuntu login screen.

---

