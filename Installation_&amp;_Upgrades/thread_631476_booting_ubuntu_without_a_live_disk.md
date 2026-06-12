---
title: "booting ubuntu without a live disk"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by yehonaton on 2007-12-04
After a successful installation of Ubuntu 7.10, I don't know how to boot into Ubuntu immediately. I have windows XP previously installed on a separate partition. Please instruct me on how to allow my computer to have the choice of booting from Ubuntu. Thank you for your help  -Jon

---

### Post by Pumalite on 2007-12-04
What happens when you boot now? Where did you install Grub? Did you install Ubuntu with one drive disconnected? Your specs would help.

---

### Post by yehonaton on 2007-12-04
I get a screen that asks me to if I want to start up windows XP  pro or windows server 2003, which I have taken off already. so the only OS I can boot into is xp pro.  Ubuntu is installed on the partition that originally had windows server 2003  on it it is (50 gig).  So the Grub was installed wherever it is that it was installed by default.  I am using a separate 30 gig, drive for the swap.  I have the ultimate grub disk but I have no Idea if it is even useful in my situation.

---

### Post by Pumalite on 2007-12-04
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst
(use your Live CD)

---

