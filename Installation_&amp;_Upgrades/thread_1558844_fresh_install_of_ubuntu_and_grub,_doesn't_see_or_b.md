---
title: "fresh install of ubuntu and grub, doesn't see or boot into windows"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by Dawei87 on 2010-08-22
hey all. i just installed the ubuntu 10.04.1 after windows 7 on a newer computer, but grub didnt seem to see windows when i installed and it just boots straight to linux. i dont see a grub screen or anything. i'm not familiar with the new grub or how it works, i ran grub-update and it only showed the linux kernel, and memtest. anyone have any ideas how to get a grub screen with windows on it?

---

### Post by wilee-nilee on 2010-08-22
Try sudo update-grub in the terminal and see if it shows Windows. Look in home on the side panel or in places-computer to see if you see the Windows partition.

You can post the bootscript in my signature in code tags as well.

---

### Post by Dawei87 on 2010-08-23
ok. found the problem. apparently my windows partition had a second "boot" folder along with the normal windows "Boot" folder. grub was seeing the first folder and not seeing it as windows. i deleted the folder and ran update-grub and it saw windows. everything is working fine now. thanks.

---

