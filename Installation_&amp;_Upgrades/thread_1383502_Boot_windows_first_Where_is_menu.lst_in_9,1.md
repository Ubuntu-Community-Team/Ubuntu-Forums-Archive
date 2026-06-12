---
title: "Boot windows first? Where is menu.lst in 9,1?"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by xmarkom on 2010-01-17
How to set Windows as default system in boot menu?
Where is menu.lst (i've found some texts on the net where people found solution where all you need is to change some code lines in that file in boot/grub/)

---

### Post by snowpine on 2010-01-17
Ubuntu 9.10 uses Grub 2, which no longer has a menu.lst file.

This should bring you up to speed on the changes:

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by mick222 on 2010-01-17
THere is no menu 1st in 9.1 here is a link to grub2 configuration you will need to edit the file /etc/grub.d/custom_40 [https://help.ubuntu.com/community/Grub2#Initial%20Default](https://help.ubuntu.com/community/Grub2#Initial%20Default)

---

### Post by Leppie on 2010-01-17
if you want to set windows as the default os to boot, edit your grub defaults file:
```
gksudo gedit /etc/default/grub
```
modify the GRUB_DEFAULT variable:
```
GRUB_DEFAULT=[COLOR=Red]**"**[/COLOR]Microsoft Windows XP (loader) (on /dev/sda1)[COLOR=Red]**"**[/COLOR]
```
mind the quotes (it won't work without them). you need to know the exact menu entry though, you can find it like this:
```
cat /boot/grub/grub.cfg | grep Windows
```
now run update-grub to regenerate the configuration file:
```
sudo update-grub
```

---

