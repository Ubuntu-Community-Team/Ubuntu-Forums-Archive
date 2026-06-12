---
title: "upgrading ubuntu deletes winXP entry from menu.lst"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by dijxtra on 2007-06-15
How do I stop updater from messing with my menu.lst? Of last 3 times I updated my system, my menu.lst changed twice by erasing my winXP entry. You can't imagine how irritating it is when your family members wake you up before noon because "I deleted their Windows". Help, please :-(

---

### Post by musther on 2007-06-15
I'm not sure if there's a way to stop packages from changing the file, although you could use synaptic to hold back the grub package, but I wouldn't advise that really.

What you could do is make a backup of menu.lst, say /boot/grub/menu.bkp then add this line to the script /etc/X11/gdm/PostSession/Default

```
cp /boot/grub/menu.bkp /boot/grub/menu.lst
```

Then every time you log out that command will run and copy the backup over the potentially new one, if it's ever updated, it will be restored from the backup when you (or any user) logs out.

The Default script in PostSession is run as root so no sudo or anything is required.

Hope that's helpful.

---

### Post by dijxtra on 2007-06-15
> **musther said:**
> What you could do is make a backup of menu.lst, say /boot/grub/menu.bkp then add this line to the script /etc/X11/gdm/PostSession/Default

```
cp /boot/grub/menu.bkp /boot/grub/menu.lst
```

Then every time you log out that command will run and copy the backup over the potentially new one, if it's ever updated, it will be restored from the backup when you (or any user) logs out.
But, then if the updater installs new kernel, I won't see it on the grub menu, will I?

---

### Post by confused57 on 2007-06-15
Your menu.lst Window's entry needs to be either above the line ###BEGIN AUTOMAGIC KERNELS LIST or below the line ###END DEBIAN AUTOMAGIC....if it's in the section between these lines, it'll be deleted after each kernel update when update-grub is run.

---

### Post by musther on 2007-06-15
It it still gets replaced, then you could write a script to reinsert your windows option at the end of menu.lst and get that to run as I suggested, then any new entries will remain, of course the script will have to check whether the entry is already there first.

---

### Post by stchman on 2007-06-15
> **dijxtra said:**
> How do I stop updater from messing with my menu.lst? Of last 3 times I updated my system, my menu.lst changed twice by erasing my winXP entry. You can't imagine how irritating it is when your family members wake you up before noon because "I deleted their Windows". Help, please :-(

You obviously modified the menu.lst file to have Windows be first in the boot order.  When you upgrade the kernel is wants to be first.

You can do two things, make Windows the last on the boot list or don't upgrade the kernel.  When you leave Windows as the last on the list the kernel upgrades won't affect it then.

---

### Post by musther on 2007-06-15
If you make windows the last on the list, it can still be default (unless the kernel upgrade resets the default in menu.lst too).

---

### Post by dijxtra on 2007-06-16
> **confused57 said:**
> Your menu.lst Window's entry needs to be either above the line ###BEGIN AUTOMAGIC KERNELS LIST or below the line ###END DEBIAN AUTOMAGIC....if it's in the section between these lines, it'll be deleted after each kernel update when update-grub is run.
Ah, yes, this sounds reasonable. Thanks a lot! I will give that one a try.

---

### Post by stchman on 2007-06-18
> **musther said:**
> If you make windows the last on the list, it can still be default (unless the kernel upgrade resets the default in menu.lst too).

How do you do that.  Is there a grub tutorial somewhere?

Thanks

---

### Post by musther on 2007-06-18
Basic info about configuring is present as comments in menu.lst itself.  The section you're looking for is:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0
```

---

