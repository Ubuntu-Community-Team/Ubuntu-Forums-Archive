---
title: "Dual boot with Ubuntu &amp; WinMagic Encryption"
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by NilsE on 2008-10-27
I have Windows on one hard drive and Ubuntu on another hard drive.  I currently have grub on the Ubuntu drive and boot directly to Ubuntu by default via setting it as the primary or first drive in the BIOS.  On the occasions when I need to boot Windows I do it via the alternate boot options of the BIOS by selecting the Windows drive.

I would like to use grub but I can not put grub on the Windows drive due to WinMagic taking over the boot control.

So, my questions is has anyone setup a WinMagic boot in the grub menu? And if so how?

---

### Post by lemming465 on 2008-10-28
I haven't set that up, but two possible options:

1) try something in /boot/grub/menu.lst like

title           xp-encrypted
root            (hd0,0)
chainloader     +0

2) you can get windows (XP or Vista) bootloaders to chain to grub, with some effort.

---

### Post by NilsE on 2008-10-29
> **lemming465 said:**
> I haven't set that up, but two possible options:

1) try something in /boot/grub/menu.lst like

title           xp-encrypted
root            (hd0,0)
chainloader     +0

2) you can get windows (XP or Vista) bootloaders to chain to grub, with some effort.
Thanks

I will give it a shot.  Worst case that looks like it should pick up and act on the WinMagic takeover of the MBR.

---

### Post by NilsE on 2008-11-01
I am able to get it to find the XP bootrecord but since it is encrypted it get an error 13: Invalid error..... so I don't think it will work.

Thanks

---

