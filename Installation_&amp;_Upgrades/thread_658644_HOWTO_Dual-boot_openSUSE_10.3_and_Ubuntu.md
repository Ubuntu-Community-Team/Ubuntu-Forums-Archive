---
title: "HOWTO: Dual-boot openSUSE 10.3 and Ubuntu"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by HotCocoa on 2008-01-04
This is my second howto. Enjoy! :)
  First, install openSUSE.  Make sure to mark the option in the settings "Do not install a boot loader".
  Once it is done, go into your normal Ubuntu terminal and type:
```
sudo gedit /boot/grub/menu.lst
```
  Once you have menu.lst open, go to the very end.  If this is not already there, add this for organization reasons:
```
title Other operating systems:
root
```
Once you have made that divider, under it, enter:
```
title openSUSE 10.3
root (hd1,0)
kernel /boot/vmlinuz
initrd /boot/initrd
```
  (The (hd1,0) means I am using a second HDD.  The second HDD, the default partition.  change this if otherwise.)
  This sets GRUB to use the vmlinuz and initrd shortcuts that openSUSE redirects every time those files are updated.  Once you're done, save the document and exit.  Once you reboot, you should have openSUSE in your GRUB menu.  Post any problems. :KS

---

### Post by K.Mandla on 2008-01-06
Moved to Installation and Upgrades.

---

### Post by Northsider on 2008-02-27
Is there a special way to partition the hard drive for two linux os'es?  I'd like to try and get openSUSE 10.3 dual booted.

---

### Post by kellemes on 2008-02-27
> **Northsider said:**
> Is there a special way to partition the hard drive for two linux os'es?  I'd like to try and get openSUSE 10.3 dual booted.

Not really, just give both os's the partitions they need/want and share the swap.

---

### Post by Northsider on 2008-03-03
> **kellemes said:**
> Not really, just give both os's the partitions they need/want and share the swap.

Well, what partitions do they need?  Is it like dual booting windows and Ubuntu, where windows needs its own partition and ubuntu needs its own partitions?

---

