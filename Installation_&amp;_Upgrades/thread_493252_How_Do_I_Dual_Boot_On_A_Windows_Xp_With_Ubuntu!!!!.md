---
title: "How Do I Dual Boot On A Windows Xp With Ubuntu??!?!?!?!"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by ajwak95 on 2007-07-05
HOW do i dual boot with Windows XP media edition 2004?

---

### Post by geek_Man on 2007-07-05
You have to add an entry into your menu.lst file. So type ```
sudo fdisk -l
``` and find out what partition your Windows installation is on (mine was /dev/hda2). Then type ```
gksudo gedit /boot/grub/menu.lst
```
Go to the very bottom and paste in the following ```
title		Windows XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

This might not work the first time since everyone has a different partition scheme and they don't all work the same. But try that, and if it doesn't work, post the output of "sudo fdisk -l" (that's a lowercase L, BTW).

---

### Post by the music man on 2007-07-05
When you *first *install Windows or it already is installed, and *then *install Ubuntu on a seperate partition, the installer automatically recognizes your XP installation and asks you if you want to import settings, files etc, and it adds XP to the boot menu. In other cases, use the explanation above.

---

### Post by ajwak95 on 2007-07-06
> **geek_Man said:**
> You have to add an entry into your menu.lst file. So type ```
sudo fdisk -l
``` and find out what partition your Windows installation is on (mine was /dev/hda2). Then type ```
gksudo gedit /boot/grub/menu.lst
```
Go to the very bottom and paste in the following ```
title		Windows XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

This might not work the first time since everyone has a different partition scheme and they don't all work the same. But try that, and if it doesn't work, post the output of "sudo fdisk -l" (that's a lowercase L, BTW).

HOW DO YOU CHANGE IT?!?!?!?!?!?!?!?!?!?!? (OR ACCESS THE menu.lst FILE???????)

---

### Post by geek_Man on 2007-07-06
Exactly how I told you. "gksudo" runs the graphical sudo, "gedit" is the gnome editor, "/boot/grub/menu.lst" is the path to the file you want to open. If you copy and paste the second command into the terminal, it will open up your menu.lst file. And please don't shout, it hurts my ears ;).

---

