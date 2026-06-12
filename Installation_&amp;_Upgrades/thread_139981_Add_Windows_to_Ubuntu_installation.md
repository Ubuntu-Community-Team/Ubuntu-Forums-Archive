---
title: "Add Windows to Ubuntu installation"
date: 2006-03-05
forum: Installation &amp; Upgrades
---

### Post by sjmo2 on 2006-03-05
I am happily and successfully running Ubuntu BB 5.10, but want to add a windows-bootable HDD.  I have previously installed Linux on top of WIndows but not the other way around.  Is this possible?  How is this performed knowing the multiple reboots Windows requires. Thanks!!


sjmo2

---

### Post by Coelocanth on 2006-03-05
You want to add a second hdd and put Windows on it? I would think this should be possible. Not sure exactly how you'd have to do it, but I'm sure one of the gurus here can offer suggestions.

*edit* What kind of drives are you talking about (SATA, IDE)?

---

### Post by lha on 2006-03-05
[QUOTE=sjmo2]I am happily and successfully running Ubuntu BB 5.10, but want to add a windows-bootable HDD.  I have previously installed Linux on top of WIndows but not the other way around.  Is this possible?  How is this performed knowing the multiple reboots Windows requires. Thanks!!


sjmo2[/QUOTE]
Simplest solution is to unplug Ubuntu drive, plug in your empty drive and install Windows like it would be the only os on your computer. Then make Windows drive slave, put Ubuntu drive to its original position and edit menu.lst to include an option to boot Windows.

---

