---
title: "Kernel recovery boot freeze"
date: 2009-07-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dentaku65 on 2009-07-28
On my machine if I choose to boot with the recovery Kernel (2.6.31-4-generic) the machine freeze right after the display of recovery menu. The only way to reboot the machine (beside hard reset) is the combination keys:
ALT+PRINT+reisub

---

### Post by dentaku65 on 2009-08-10
Bump!
Still happens with kernel 2.6.31-5-generic. Any idea?

---

### Post by dentaku65 on 2009-08-11
Ok fixed.
I've found that my grub.cfg has this entry

```
sudo cat /boot/grub/grub.cfg
```
> ### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-5-generic" {
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b9b35c5e-8eee-408e-a72a-9c0505620ad0
	linux	/boot/vmlinuz-2.6.31-5-generic root=UUID=b9b35c5e-8eee-408e-a72a-9c0505620ad0 ro splash #GRUB_DISABLE_LINUX_UUID=t
rue quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-5-generic
}
menuentry "Ubuntu, Linux 2.6.31-5-generic (recovery mode)" {
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set b9b35c5e-8eee-408e-a72a-9c0505620ad0
	linux	/boot/vmlinuz-2.6.31-5-generic root=UUID=b9b35c5e-8eee-408e-a72a-9c0505620ad0 ro single [COLOR="Red"]splash[/COLOR] #GRUB_DISABLE_LINUX
_UUID=true quiet
	initrd	/boot/initrd.img-2.6.31-5-generic
}

Removing splash entry it works... but I don't really understand how that entry has been insterted because I'm using the mantainer conf of grub :confused:

---

### Post by taavikko on 2009-08-11
> **dentaku65 said:**
> Ok fixed.


Removing splash entry it works... but I don't really understand how that entry has been insterted because I'm using the mantainer conf of grub :confused:

Because the some of the configs are read from "/etc/default/grub"
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

which will then insert them back to grub.cfg when update-grub is run.

---

### Post by psyke83 on 2009-08-11
dentaku,

This could also be due to KMS being initialized, which isn't stable on your 855GM chipset. Even if you set "nomodeset" in /etc/default/grub, booting in recovery mode will ignore this option.

KMS is not completely stable on our chipset yet. The xorg-edgers drivers are better, but occasionally things will freeze, or other issues will appear (currently, KMS works but refuses to initialize the XVideo extension).

---

