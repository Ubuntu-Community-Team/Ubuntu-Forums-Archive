---
title: "can GRUB load from the-same-device-it-is-installed-onto"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by natirips on 2008-08-31
Okay, what I want would be to make GRUB's menu.lst have something like this:

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
**root		(the-disk-grub-is-on,0)**
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=af5d28d9-d902-4f57-a34d-56778e43e926 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```instead of```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
**root		(hd0,0)**
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=af5d28d9-d902-4f57-a34d-56778e43e926 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```

I haven't tried this because I clearly doubt it would work literaly like this... But is there a way to do that?

---

### Post by caljohnsmith on 2008-09-01
> **natirips said:**
> Okay, what I want would be to make GRUB's menu.lst have something like this:

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
**root		(the-disk-grub-is-on,0)**
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=af5d28d9-d902-4f57-a34d-56778e43e926 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```instead of```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
**root		(hd0,0)**
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=af5d28d9-d902-4f57-a34d-56778e43e926 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```

I haven't tried this because I clearly doubt it would work literaly like this... But is there a way to do that?
No, unfortunately you can't do that. And when you say "the-disk-grub-is-on," that is actually a little ambiguous because in your case Grub actually resides in two places: in the MBR of your boot HDD, but Grub also has its system files (menu.lst, stage2) in some other partition which may not necessarily be on the boot HDD. :)

---

### Post by natirips on 2008-09-01
> **caljohnsmith said:**
> No, unfortunately you can't do that. And when you say "the-disk-grub-is-on," that is actually a little ambiguous because in your case Grub actually resides in two places: in the MBR of your boot HDD, but Grub also has its system files (menu.lst, stage2) in some other partition which may not necessarily be on the boot HDD. :)
Not necessarily, but they are in this case (note that the example I've given above is not from the menu.lst of my experimental system which has the problem, but from my main computer (the one I'm typing this from)).



Anyway, I mean like this:

If I install an OS or two on a hard drive, now grub works fine with the computer that was used to install it (with the proper boot order settings in BIOS).

But when I plug the disk in another computer or rearrange disks within the same computer, it won't work anymore (acctually it loads up fine until it reaches the point at which I have to select an OS, but there's no OS on the selected, for example, hd2 and I have to modify GRUB's menu entries from, for example, hd2 to hd3).

So I was thinking if there is a way to make GRUB autodetect from which physical device's (which hd#'s) MBR is it loading (like the Live CDs's boot loaders)?

---

### Post by caljohnsmith on 2008-09-01
> **natirips said:**
> Not necessarily, but they are in this case (note that the example I've given above is not from the menu.lst of my experimental system which has the problem, but from my main computer (the one I'm typing this from)).



Anyway, I mean like this:

If I install an OS or two on a hard drive, now grub works fine with the computer that was used to install it (with the proper boot order settings in BIOS).

But when I plug the disk in another computer or rearrange disks within the same computer, it won't work anymore (acctually it loads up fine until it reaches the point at which I have to select an OS, but there's no OS on the selected, for example, hd2 and I have to modify GRUB's menu entries from, for example, hd2 to hd3).

So I was thinking if there is a way to make GRUB autodetect from which physical device's (which hd#'s) MBR is it loading (like the Live CDs's boot loaders)?
If you are loading an OS that is on the same HDD as Grub's MBR is on, then the OS will always use (hd0,X). But the OSs on the other HDDs may change from (hd1,X) to (hd2,X) or something else as you mention if you rearrange your HDDs. And no, Grub has not automatic mechanism for detecting that. You could modify your Grub's menu on start up "on the fly" by selecting the OS you want to boot, and pressing "e" to edit it. Then you can change (hd1,X) to (hd2,X) or whatever you want.

---

### Post by natirips on 2008-09-01
> **caljohnsmith said:**
> If you are loading an OS that is on the same HDD as Grub's MBR is on, then the OS will always use (hd0,X). But the OSs on the other HDDs may change from (hd1,X) to (hd2,X) or something else as you mention if you rearrange your HDDs. And no, Grub has not automatic mechanism for detecting that. You could modify your Grub's menu on start up "on the fly" by selecting the OS you want to boot, and pressing "e" to edit it. Then you can change (hd1,X) to (hd2,X) or whatever you want.

I know how to edit grub's menu ""on the fly"", I just thought if I could work-around it somehow...but a gouess not I can't. Thanks for you effort anyway. I will just try seeking for another boot loader.

---

### Post by clinto on 2008-09-01
I'm not positive, but I think grub has to start on the mbr of the first drive.

However, either way, if you have your machine looking to one place to start grub and then you change it, it's not going to know the next time you boot and will just hang... unless maybe you set the jumper on that hdd to master instead of cable select... I'm not sure if that would work or not.

what caljohnsmith said :p

---

### Post by natirips on 2008-09-04
Hmmm... I sure had a delay since the last post, but that's because I broke the (experimental) system I needed the help for so it took me quite some time to fix it. Anyway here's the significant part (list of OSes) of the menu.lst that causes "problems":
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
**root		(hd1,0)**
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b16596b6-760e-4927-8766-ba71121b669f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b16596b6-760e-4927-8766-ba71121b669f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title		Rendom DOS
root		(hd0,0)
makeactive
chainloader	+1

title		Rendom Linux
root		(hd0,1)
kernel	/vmlinuz root=/dev/hda2 ro
```The last two entries ("Rendom" ones) are just for convinient way temporary booting from another device and are a copy-paste of examples that exist in default menu.lst in commented form.

So the point of the post was: is there a way to make grub (which is installed on the same drive as the OS) boot from that very same device (i.e. hd0, hd1, ...) it (grub) was booted from (but without doing it manually every time I reorder disks). Note that each physical drive that has OS(es) on it has it's own grub (although there's just one of them right now[NOPARSE]:)[/NOPARSE].

It's nothing of severe improtance, just that I thought **if** there's a way to do it I'd like to know it....

Edit: As for master/slave; I have an ancient no-name motherboard in my experimental computer which allows me to boot from any disk (be it primary or secondary, hdd fdd or cd/dvd, pata or sata, master or slave, usb or ide).

---

