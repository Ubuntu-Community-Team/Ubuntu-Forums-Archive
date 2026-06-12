---
title: "recovering vista after dual-booting Vista with Linux (Vista installed first)"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by dekay on 2007-06-27
I recently tried to dual-boot vista with linux
(having vista installed first.Being a newbie 
I just followed the the steps described in 
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")
. after the installation was complete and after system reboot I dont see windows vista
as other operating system on the GRUB. I dont know what I might have missed while installation.
Is there any way I can recover win vista with out loosing any data? or did I already wipe it off my machine :) ? 

Thanks

---

### Post by hessiess on 2007-06-27
you may have wiped the drive, did you use "use entire drive"? or you may have corupted the partition during the install. in ubuntu you should be able to see the vista partition on the desktop, so long as the partition is mounting.

if the partition is there then it should just be a matter of editing the grub list, sorry but i dont know how to do this:(

---

### Post by merlinus on 2007-06-27
Whilst booted into ubuntu, enter this in a terminal and post results:

```

cat /boot/grub/menu.lst

```

and also:

```

sudo fdisk -l

```

l is a lowercase L.  You will be asked for your password.

-merlin

---

### Post by dekay on 2007-06-27
I do see the vista partition.....

---

### Post by merlinus on 2007-06-27
```

cat /boot/grub/menu.lst

```

if you want help.

-merlin

---

### Post by dekay on 2007-06-27
I tried that... but all it shows is the disk partitions. but is there any way I can recover windows now?

---

### Post by merlinus on 2007-06-27
This may help:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by ihristov on 2007-06-27
I suppose you are missing an entry for Windows in grub.menu

You should have something like:

```

title Microsoft Windows XP Professional
root   (hd0,0)
savedefault
makeactive
chainloader  +1

```

in /boot/grub/menu.lst

You could manually type this at the GRUB prompt or you can use the [Super GRUB rescue disk]("http://sgd.howto-linux.de/")

Boot from it and select Windows / Boot windows to try to boot manually. If it boot correctly you can then manually add an entry like the one above in /boot/grub/menu.lst

---

