---
title: "Pb boot grub 64 bits"
date: 2005-02-24
forum: Installation &amp; Upgrades
---

### Post by Urania on 2005-02-24
Hello,
I am using for a very long time Debian 32 bits on my 64 bits laptop.
So i am testing ubuntu 64 bits on my laptop.

My partitions :

hda1 - windows
hda 2 - /
hda 3 - swap
hda 4 - 
hda 5 - /usr
hda 6 - /var
hda 7 -  /boot
hda 8 -  /home
hda 9 -  /tmp
hda 10 - / 
hda 11 - swap

For Ubuntu, i am using hda10 and hda11.
I want to use the Grub using by debian to start my Ubuntu 64bits.
So in my grub debian i put :

title          Ubundu 64, kernel 2.6.8
root            (hd0,9)
kernel          /boot/vmlinuz root=/dev/hda10 ro
savedefault
boot

When i start i have this error message :

VFS: Cnnot open root device "hda10" on unknow block (0,0)
Please append a correct "roo=" boot option ......

A long time i did not see this message ;)

Any idea ?

Thx

---

### Post by p!=f on 2005-02-24
[QUOTE=Urania]
So in my grub debian i put :

title          Ubundu 64, kernel 2.6.8
root            (hd0,9)
kernel          /boot/vmlinuz root=/dev/hda10 ro
savedefault
boot

When i start i have this error message :

VFS: Cnnot open root device "hda10" on unknow block (0,0)
Please append a correct "roo=" boot option ......

A long time i did not see this message ;)

Any idea ?

Thx[/QUOTE]
Aren't you missing initrd line?
```

title           Ubuntu, kernel 2.6.11-rc4-nitro1
root            (hd0,6)
kernel          /vmlinuz-2.6.11-rc4-nitro1 root=/dev/sda4 ro video=vesafb:ypan,1280x1024-32@85 quiet splash
initrd          /initrd.img-2.6.11-rc4-nitro1
savedefault
boot

```

---

