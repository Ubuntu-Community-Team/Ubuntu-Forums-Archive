---
title: "Internal drive MBR gone after feisty install to external drive"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by eoghanmurray on 2007-12-18
Hello,
   My friend decided that he wanted to have Ubuntu on his external hard drive, so he came round to my house and I left him with my PC for a while, and he installed it via the Live CD, but it's written GRUB to the internal drive! Now, to boot into my own Ubuntu installation, I have to slam F12 while booting, change the GRUB reference to (hd0,1) and manually boot. Is there a way to overwrite this and restore GRUB?

Thanks very much :D

I really need this quickly. Thanks.

---

### Post by Pumalite on 2007-12-18
You can reinstall Grub with this:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
When you install to external drive, disconnect all internal drives, otherwise, part of Grub will be in your internal MBR and part in the external drive.

---

### Post by eoghanmurray on 2007-12-19
Thanks very much! Just the thing. Can't believe I didn't think of that - it's happened before :D

---

### Post by Pumalite on 2007-12-19
You are welcome. Good luck.

---

### Post by da3v on 2008-02-16
Why does grub try to split itself across drives in this scenario?  I wanted to experiment with Ubuntu without trashing my XP machine, so I created a 7.04 live CD, booted from it, ran install to my USB drive, and all seemed to go well. -Except I now HAD to have my USB drive in order to boot into either XP or Ubuntu. This was irritating, but something I could live with until my USB drive was damaged. Now I can no longer boot from my original drive, because Grub chokes without what it needs is on the missing drive USB. Hopefully I can restore my XP mbr and get back to where I started, but this was a very, very bad first experience.

---

### Post by Pumalite on 2008-02-16
Restore your XP MBR with Install CD>Recovery>FIXMBR>FIXBOOT
Or Super Grub (google it)

---

### Post by dstew on 2008-02-16
> Why does grub try to split itself across drives in this scenario?Grub is a multi-boot loader, that is, it can boot several different operating systems. It is actually a very large and capable program. The Master Boot Record of any disk has only space for 512 bytes of code. Grub cannot put its whole program there, it has to put the other, larger part (stage2) somewhere in the file system. If you install Linux on the USB drive, and then tell grub to install into (hd0), which is the default behavior, it will be installed in such a way as to look in the USB drive for its stage2. Your friend probably did this by mistake. He should have told grub to install into the USB drive partition instead.

If you want to make it so grub will be able to boot without the USB drive in place, you need to have a grub stage2 file somewhere on your hard disk, AND you have to install grub in the MBR in such a way that is uses the hard-disk stage2 instead of the USB stage2.

Since you already have an Ubuntu system in place, you have a stage2 on your hard disk, in the /boot/grub folder of your Ubuntu partition. You just need to re-install grub to use that particular stage2 file.

The easiest way is to boot a Live CD, open a terminal window, and enter the command```
grub
```That gets you the grub command line, with the grub> prompt. At the grub command line, enter```
find /boot/grub/stage2
```Whatever answer it gives, use as the argument to the root statment```
root (hd0,0)
```Then, install grub into the MBR with```
setup (hd0)
quit
```Then reboot. You should get your old dual-boot menu back. You can add a menu item to boot the USB external drive if you want by editing /boot/grub/menu.lst

---

