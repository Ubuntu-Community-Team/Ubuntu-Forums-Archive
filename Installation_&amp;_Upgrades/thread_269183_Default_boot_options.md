---
title: "Default boot options"
date: 2006-10-01
forum: Installation &amp; Upgrades
---

### Post by GaryS on 2006-10-01
How do I make XP the default boot system and Ubuntu as a choice.

---

### Post by Kateikyoushi on 2006-10-01
Type in terminal

```
sudo cp /boot/grub/menu.lst menu.lst.bck
sudo nano /boot/grub/menu.lst
```

The first creates a backup copy of the grub menu for you.
The second opens grub menu for editing.

Change the 0 in the "default 0" line to XP's number when you see the grub menu at startup.

---

