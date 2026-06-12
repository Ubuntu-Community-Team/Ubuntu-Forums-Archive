---
title: "GRUB doesn't recognize Windows"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by inebriant on 2006-09-21
I have 2 HDs on IDE0 (Master and Slave). I loaded windows on the Slave and Ubuntu LAMP server on the Master.  GRUB loads Ubuntu automatically and when I get the menu, Windows is not on it.  I tried loading a bootloader called GAG, and it recognized both OSes and will boot Windows, but I get an error when selecting Ubuntu that says "Missing boot sector".  The FAQ says something about needing LILO. It seems like it should be a simple fix, but I don't want to get a degree in bootloaders just to get this working.  Thanks for your help.

---

### Post by confused57 on 2006-09-21
> **inebriant said:**
> I have 2 HDs on IDE0 (Master and Slave). I loaded windows on the Slave and Ubuntu LAMP server on the Master.  GRUB loads Ubuntu automatically and when I get the menu, Windows is not on it.  I tried loading a bootloader called GAG, and it recognized both OSes and will boot Windows, but I get an error when selecting Ubuntu that says "Missing boot sector".  The FAQ says something about needing LILO. It seems like it should be a simple fix, but I don't want to get a degree in bootloaders just to get this working.  Thanks for your help.
You should be able to add an entry to your /boot/grub/menu.lst file to boot Windows(type one line at a time, press enter after each line):

```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo nano menu.lst
```
The menu.lst is short for menu.list, not menu.first.
If you not sure where the spaces are:
sudo(space)/boot/grub
sudo(space)cp(space)menu.lst(space)menu.lst_backup
sudo(space)nano(space)menu.lst
Add something like the following to the very end of the file(add the entire entry):
```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

Press ctrl+X, y, enter...to save.

You make the grub menu visible at bootup by adding a # in front of hiddenmenu.
You can extend the time the grub menu is displayed by changing the timeout(in seconds).
```
hiddenmenu
```
to
```
#hiddenmenu
```

and
```
timeout  3
```
to
```
timeout  10
```

If something goes wrong and you need to restore your original menu.lst;
```
sudo cp /boot/grub/menu.lst_backup /boot/grub/menu.lst
```

You "should" be able to boot Ubuntu or Windows from the grub menu at startup.

---

