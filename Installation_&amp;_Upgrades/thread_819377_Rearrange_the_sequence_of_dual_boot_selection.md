---
title: "Rearrange the sequence of dual boot selection"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by wengkhin on 2008-06-05
----------------------

---

### Post by dstew on 2008-06-05
Yes, you can change the default OS by editing the grub menu.lst file. You can edit it from Ubuntu using the gedit program. To do this, press alt-F2 and enter the command```
gksudo gedit /boot/grub/menu.lst
```Find the line near the top that says```
default   0
```Make sure you have the line without the # at the start. Change the number to the number of the Windows menu item, starting at 0. So if the Windows item is the fifth, change the default argument to 4:```
default   4
```Then save the file, and reboot. It should automatically boot Windows.

If you change the argument of default from a number to the word **saved**, the default menu item will be whichever you used last, as long as that item has a **savedefault** entry in it. See the [Gnu Grub manual]("http://www.gnu.org/software/grub/manual/grub.html#default") for details.

---

### Post by Keith Hedger on 2008-06-05
after editing the grub menu u may have to use ```
sudo update-grub
```

---

### Post by dstew on 2008-06-05
Keith, if the OP's menu.lst has the automagic parameter **# updatedefaultentry=false**, which I think is the default, update-grub will undo his new default setting. See [this thread]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=809163"). If the OP wants to keep the XP as the default OS, then he should set # updatedefaultentry=true before upgrading to a new kernel, or doing update-grub.

---

### Post by Keith Hedger on 2008-06-05
I bow to your superior knowledge, I dont have a windows installation just some spare partitions that i use to try out different distros and i edit my grub menu.lst by hand (when i install a new distro I dont install grub I edit the menu.lst and then do update-grub from a rescue partition).

---

