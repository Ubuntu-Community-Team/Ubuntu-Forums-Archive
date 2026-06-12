---
title: "Kernel Update didn't install / won't show on grub"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by Nickedynick on 2008-07-23
Hi, firstly - which is the latest kernel that has been distributed to Hardy users? I updated the other day and noticed there was a kernel update, which I installed (I think), but on reboot I still have the same 2 kernel versions I had before in grub.

I recall there being a couple of questions asked about what I wanted done with my grub and I may have misinterpreted one of the options - what can I do?

Any help would be much appreciated :)

---

### Post by logos34 on 2008-07-23
sudo grub-install /dev/sda
sudo update-grub

Check that the newest kernel is listed in menu.lst

---

