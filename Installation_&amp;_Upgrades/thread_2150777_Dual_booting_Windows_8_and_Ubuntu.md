---
title: "Dual booting Windows 8 and Ubuntu"
date: 2013-06-02
forum: Installation &amp; Upgrades
---

### Post by cozzybcb on 2013-06-02
Hi,

I installed Ubuntu, and it detected a previous install on my second hard drive of windows, I reinstalled windows to this drive and now when I boot the computer, Grub? shows Ubuntu and then Windows 8 but it is trying to boot the old one it detected rather then the new one, anyway to fix this/update grub?

Thanks for any help.

---

### Post by fantab on 2013-06-02
When you reinstalled Windows did you format the Hard Drive completely?
Where did you install Ubuntu?
Where did you install GRUB?

---

### Post by cozzybcb on 2013-06-02
Drive 1 (ssd) has Ubuntu
Drive 2 (500gb) has Windows, and it was formatted with the included tool when you install, so properly, doubt it lol

Grub no idea, I'm not sure if I'm calling it the right name, when I boot Ubuntu it gives me a choice of what to boot, thats what I am talking about.

---

### Post by fantab on 2013-06-02
Boot with LiveDVD/USB and from Termianl post the output of:

```
sudo parted -l
```

---

