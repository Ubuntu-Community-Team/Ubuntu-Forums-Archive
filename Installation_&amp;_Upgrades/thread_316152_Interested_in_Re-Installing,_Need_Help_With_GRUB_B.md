---
title: "Interested in Re-Installing, Need Help With GRUB Bootloader"
date: 2006-12-10
forum: Installation &amp; Upgrades
---

### Post by Araelius on 2006-12-10
I had Ubuntu previously installed when build 6.06 was released, I loved every minute of it, however I had to uninstall Ubuntu due to the fact that my wife is not very computer-savvy. Every time the PC booted up the GRUB bootloader's default starting OS was Ubuntu and if my wife wanted to use the PC she didn't know how to select Windows.

Anyway, to make things short, is there a way to edit GRUB to have Windows as it's default starting OS?

---

### Post by daou on 2006-12-10
You have to edit your /boot/grub/menu.lst file:

```
sudo gedit /boot/grub/menu.lst
```

Then, near the top of the file, there should be a line:

default X

where X is some number. The number determines the entry which boots by default (0 is the first). For example, if your Windows installation is the fourth item in the Grub menu, you would have to edit the line to

default 3

---

### Post by daou on 2006-12-10
Make sure the line in the menu.lst:

timeout X

is something other than 0. X is the number of seconds Grub waits before booting WinXP. Three seconds is probably good, this is the amount of time you have to press escape and choose Ubuntu before Windows is booted.

---

### Post by Araelius on 2006-12-10
Perfect, you guys are amazingly fast at helping others, thanks so very much. Hopefully this thread can help others as well. :)

---

### Post by daou on 2006-12-10
> Perfect, you guys are amazingly fast at helping others

One of the many reasons I chose to use Ubuntu ;) .

---

