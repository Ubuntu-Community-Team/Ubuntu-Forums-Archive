---
title: "No partition after yesterday's upgdate"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by zedascouves on 2011-05-03
Hello,

I installed 11.04 without problems and I was running the classic desktop. Then, yesterday, I updated it (Gwibber and some Gnome things, I think), and my /home hard drive stopped working (I have two hard drives, one for the OS and another just for /home).

Every time I boot up, it says it can't find the /home partition or "it's not ready". I even tried booting with Gparted, but it says my /home hard drive is empty, as in "there's not even a partition there".

I know it can be hardware problem, but it's highly doubtful.

Can anyone help, please?

---

### Post by dino99 on 2011-05-03
boot on recovery mode ("shift" key down at bios end process) then run from a terminal:

sudo shutdown -r now

that will force a fsck on next reboot

---

### Post by zedascouves on 2011-05-03
Thank you. I'll try that later, when I'm home.

---

