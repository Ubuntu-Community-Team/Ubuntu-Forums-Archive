---
title: "[SOLVED] Grub dual boot problem, not updating to latest kernel."
date: 2008-07-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-07-16
Got 8.04 on sda1 and Intrepid on sda2.

Grub is on sda1 I think. So just done the kernel updates but menu.lst not been updated by the system.

How do I do this.

---

### Post by BwackNinja on 2008-07-16
Chances are that you've got two menu.lst's, one for each drive. Only real way I see is to do it manually or probably a ```
sudo grub-update
``` while in your first drive will autoupdate it.

---

### Post by philinux on 2008-07-16
Tried that in my Hardy install but it does not update the Intrepid entries. Still got 2.6.26-3 instead of 2.6.26-4. It updated grub on sdb aarrghh.
```

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9d1cb08e-4895-4fdf-986e-8426ce01b211 ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9d1cb08e-4895-4fdf-986e-8426ce01b211 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9d1cb08e-4895-4fdf-986e-8426ce01b211 ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9d1cb08e-4895-4fdf-986e-8426ce01b211 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu intrepid (development branch), kernel 2.6.26-3-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.26-3-generic root=UUID=3128b8b9-3eae-4bd4-9e4d-a012ce016ccf ro splash vga=792 
initrd		/boot/initrd.img-2.6.26-3-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu intrepid (development branch), kernel 2.6.26-3-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.26-3-generic root=UUID=3128b8b9-3eae-4bd4-9e4d-a012ce016ccf ro single 
initrd		/boot/initrd.img-2.6.26-3-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu intrepid (development branch), kernel Last successful boot (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/last-good-boot/vmlinuz root=UUID=3128b8b9-3eae-4bd4-9e4d-a012ce016ccf ro last-good-boot single 
initrd		/boot//boot/last-good-boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu intrepid (development branch), memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

---

### Post by Naddiseo on 2008-07-16
I'm in a similar boat; my grub is on my Intrepid partition. For now I'm just updating manually, it's not much hassle really.

---

### Post by philinux on 2008-07-16
> **Naddiseo said:**
> I'm in a similar boat; my grub is on my Intrepid partition. For now I'm just updating manually, it's not much hassle really.

Got it sorted by a bit of digging on here.

[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

Just to recap.

Hardy is on hd0 = sda
Intrepid on hd1 = sdb

Grub was living on hd0. So using the guide I installed grub to hd1 and then in menu.lst on Hardy use the chainloader which then fires up menu.lst on Intrepid. Brilliant. So now I can get rid of any Intrepid stanzas on Hardy and vice versa. All kernel updates now automatic.

Only thing is it's highlighting the memtest instead of first kernel. Have to solve that one.

[edit] that was easy, startupmanager had it as the default, how no idea.

---

### Post by Gina on 2008-07-16
I've been bugged by that too.  I thought there ought to be a way but never got round to pursuing it - just edited menu.lst.  Thank you very much for your reply :)

---

### Post by philinux on 2008-07-16
Glad to help Gina.

This has been bothering me ever since I got my new pc with 2 hard drives.

Here's my menu.lst i didn't bother with the boot line and it works fine.
```
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9d1cb08e-4895-4fdf-986e-8426ce01b211 ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9d1cb08e-4895-4fdf-986e-8426ce01b211 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9d1cb08e-4895-4fdf-986e-8426ce01b211 ro splash vga=792 quiet
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9d1cb08e-4895-4fdf-986e-8426ce01b211 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title Intrepid Ibex Development
root (hd1,0)
chainloader +1
```

---

### Post by Gina on 2008-07-17
So delightfully simple :lolflag:

I know that's now it's done with a Windoze dual-boot - don't know why I didn't try it with multi Ubuntus...

---

### Post by philinux on 2008-07-17
Exactly, now my menu.lst's on both drives just refer to there own OS.

I just had a brain wave yesterday while googling for an answer. Why don't I look on the tips and tutorial here. Low and behold there it was all the time.

---

### Post by xebian on 2008-07-17
> **philinux said:**
> 
Only thing is it's highlighting the memtest instead of first kernel. Have to solve that one.

[edit] that was easy, startupmanager had it as the default, how no idea.

In grub menu.list change the default to what is your desired kernel
```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#

default         0


```

---

### Post by philinux on 2008-07-17
> **xebian said:**
> In grub menu.list change the default to what is your desired kernel
```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#

default         0


```

I know how to do that but sum had changed it on it's own to memtest.

---

### Post by Gina on 2008-08-02
Well, I've been trying to sort out chainloader but I'm missing something.  However, I tried the alternative listed of **configfile** eg.```
title        Ubuntu Studio 8.04
configfile   (hd1,1)/boot/grub/menu.lst
```That works perfectly :)

---

### Post by philinux on 2008-08-03
Another way to get grub sorted.:)

I assume you tried installing grub to (hd1,1)

---

### Post by Gina on 2008-08-03
> **philinux said:**
> I assume you tried installing grub to (hd1,1)Yes, I did.
I must say - it's lovely to have a tidy menu rather than all that clutter I used to have :lolflag:

---

### Post by philinux on 2008-09-22
> **Gina said:**
> Well, I've been trying to sort out chainloader but I'm missing something.  However, I tried the alternative listed of **configfile** eg.```
title        Ubuntu Studio 8.04
configfile   (hd1,1)/boot/grub/menu.lst
```That works perfectly :)


Ha ha, marvelous. Just install Kubuntu 8.1 to my spare hard drive for a bit of excitement. Ubuntu is just to stable.

I remembered this thread. Worked a treat.

---

