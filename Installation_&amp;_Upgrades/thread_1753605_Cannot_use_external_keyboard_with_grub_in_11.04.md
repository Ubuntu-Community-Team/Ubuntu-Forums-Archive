---
title: "Cannot use external keyboard with grub in 11.04"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by nignasi on 2011-05-09
I'm using a Toshiba Tecra Laptop through a dock station with attached keyboard, mouse and display. I mainly use windows but also practice with ubuntu. After update to 11.04 I cannot select which system starts with the external keyboard and I must open the laptop and use its keyboard only for this task, once started everything works as usual. 

As a partial solution I've tried to edit /boot/grub/menu.lst and force windows as default system. But on boot grub still shows Linux (the first line) as preferred system. Do you now what's wrong?

By the way, now I find a lot of files in /boot/grub. If I'm not wrong they weren't there with 10.10, do you know their purpose?

Thank you,

Ignasi

---

### Post by atupmok on 2011-06-20
Same problem here.

---

### Post by nignasi on 2011-06-20
I've openend [this]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/786857") bug report, but whithout any answer yet.

---

