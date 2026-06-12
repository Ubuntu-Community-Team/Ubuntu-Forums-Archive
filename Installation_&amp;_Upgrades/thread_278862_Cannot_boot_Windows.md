---
title: "Cannot boot Windows"
date: 2006-10-17
forum: Installation &amp; Upgrades
---

### Post by r6mile on 2006-10-17
I have Windows 2000 installed on my PC. I just resized the partition and installed Ubuntu 6.06 on what was left. But GNURB doesn't let me select Windows 2000, only Ubuntu. What can I do if I want to boot Windows?

---

### Post by gunderwood on 2006-10-17
I'll assume that Windows is on /dev/hda1 which is your first partition. Boot into Ubuntu then edit your menu.lst file to include an entry for the windows partition like so.

```

sudo gedit //boot/grub/menu.lst

```

Add this Listing to the file.

```

title		Microsoft Windows 2000 Server
root		(hd0,0)
savedefault
makeactive
chainloader	+1

``` 

Reboot and you should be able to boot into windows.

---

