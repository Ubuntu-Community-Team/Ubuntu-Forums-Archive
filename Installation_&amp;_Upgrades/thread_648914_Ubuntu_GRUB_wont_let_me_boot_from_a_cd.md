---
title: "Ubuntu GRUB wont let me boot from a cd"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by GustavTheLion on 2007-12-24
when i had windows i could boot from a cd by pressing some F button during startup. now that iv'e installed xubuntu's grub, i can't boot from cd's anymore, and the grub is broken, it just says "GRUB" nothing else, no options nothing.

however i can boot ONLY from a xu/ku/u-buntu live cd


i did have fedora 8, and it still is on my harddrive, i would like to use it if i can, anyone have any suggestions?

---

### Post by dward526 on 2007-12-24
can you enter the BIOS settings of your system?

If so, you can change the boot order.

As well, the 'F$' command to select a boot source is a BIOS command, and it should not be affected by grub.  

To attempt a fix of grub from the live cd however, run it, then from command line run

```
 sudo aptitude install grub 
```

or something to that effect, I am not 100% about the specific name of the grub package.

It is also strange that you can only boot form the Ubuntu live cd's.  You can also Try getting a copy of the 'Super GRUB Disc' and running it to repair grub, it is a boot-time utility.

Just some ideas to get you started.

---

### Post by GustavTheLion on 2007-12-24
thanks the sgd did boot

and i removed grub.

but still i can only boot from ubuntu live cd's- does ubuntu have some defense system i can turn off?

---

### Post by logos34 on 2007-12-24
> **GustavTheLion said:**
> thanks the sgd did boot

and i removed grub.

but still i can only boot from ubuntu live cd's- does ubuntu have some defense system i can turn off?

Why did you do that?  Xubuntu grub shouldn't be the problem preventing you from booting cds... it's gotta be some other issue.  Now you can only boot the OS's on the hard disk with SGD or ubuntu cd!

Why not try to reinstall grub?  Hopefully it will work, but maybe not.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If you don't want to have to enter the bios to change the boot order every time you want to boot from cd, there's a way to add a 'boot cd' grub menu entry:

[http://ubuntuforums.org/showthread.php?t=168693&highlight=sbm+syslinux+boot+cd](http://ubuntuforums.org/showthread.php?t=168693&highlight=sbm+syslinux+boot+cd)

---

