---
title: "Boot loader doesn't show up"
date: 2014-09-10
forum: Installation &amp; Upgrades
---

### Post by blackpearljack on 2014-09-10
Hi
  I installed ubuntu 14.04 on my pc.I created some free space on my hard disk and used that space to install ubuntu.I choose to install boot loader on /dev/sda "some name of deive" then after installation it restarted but it doesn't show any boot loader(boots directly to ubuntu) so i'm not able to boot into windows.Please help me .....

---

### Post by oldfred on 2014-09-10
First try this:
sudo update-grub

Then post this if not found:
sudo parted -l

---

