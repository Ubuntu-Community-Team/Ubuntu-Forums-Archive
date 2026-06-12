---
title: "Installed GRUB to wrong partition"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by Prefectionist on 2007-12-20
I have a HP with a sort of "back-up" hard drive volume (in case of system malfunction due to any rotten new programs), and accidentally installed GRUB onto it instead of directly onto my Gusty partition. It's nothing severe, and I could probably live unbothered by it... it's just an annoying thought. I made a mistake and I want to undo it, you know?
I put GRUB on my Ubuntu partition no problem, I just want it off the back-up volume.
Since it's a volume with basically nothing on it but a recovery manager, I can't do anything from within. Not that I assume I'd be able to anyway... it is Vista, after all.
I don't have a Windows Vista installation CD.

Recovery Manager: (hd0,1)

Can anyone help?

---

### Post by eternicode on 2007-12-21
According to [syg00 at linuxquestions.org]("http://www.linuxquestions.org/questions/showthread.php?p=2694039#post2694039"):
> You don't "uninstall" a bootloader - you simply replace it with a new one

As nothing on Google is helping, my best guess is developers in general (be they MS or opensource devs) don't write uninstallers for bootloaders -- after all, imagine if a computer-illiterate got ahold of one...yikes...

If the "bootability" of the drive is the only thing bothering you, you can use fdisk or gparted to remove the boot flag from the partition.  Or you could do some research and see if you could "erase" the boot sector with dd....but I'd personally stick with fdisk ;)

Edit:
Silly me for not reading everything...

[quote="syg00"]
If all else fails, from a Linux console the following will erase a bootloader
```

dd if=/dev/zero of=/dev/hda bs=1 count=446

```
Type carefully !!!
[/quote]

Be sure to replace hda with the correct device!

Good luck!

---

