---
title: "Grub Issue After Vista Install"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by NomadTW on 2008-08-12
Ok, so I had ubuntu installed, and then i installed vista, no problem there.

I restored the grub loader, and thought I modified the menu.lst correctly to put vista on the list. and it does in fact come up on the list.

However, when I choose vista from the grub list the screen just flashes and it's still on the grub loader, and the only thing that works is booting to ubuntu...

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8675417c-d0c2-43b6-8ec8-2765da75eb64 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=8675417c-d0c2-43b6-8ec8-2765da75eb64 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8675417c-d0c2-43b6-8ec8-2765da75eb64 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8675417c-d0c2-43b6-8ec8-2765da75eb64 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST


title		Windows Vista
root		(hd0,3)
makeactive
chainloader+1

```

and my partition list

```


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9726    78124063+  83  Linux
/dev/sda2            9727       10334     4883760   82  Linux swap / Solaris
/dev/sda3   *       10335       19068    70154240+   b  W95 FAT32
/dev/sda4           19068       36484   139892736    7  HPFS/NTFS


```

Am I missing something somewhere?

---

### Post by logos34 on 2008-08-12
try

> root (0,**2**)

maybe vista put it's boot files on the fat32 partition

---

### Post by NomadTW on 2008-08-12
> **logos34 said:**
> try



maybe vista put it's boot files on the fat32 partition
no dice, same thing

no matter what i change it to it does the same thing, althoguh i didn't try changing it to 0 since I know that is where ubuntu is
and changing it to 4 says no partition

---

### Post by logos34 on 2008-08-12
I see what it is now--typo:

>  title        Windows Vista
root        (hd0,3)
makeactive
[COLOR=Red]chainloader+1[/COLOR]

Need a space--make it 

[COLOR=Blue]chainloader +1[/COLOR]

---

### Post by NomadTW on 2008-08-12
that did it. 

thanks man

---

### Post by logos34 on 2008-08-12
cool

enjoy

---

