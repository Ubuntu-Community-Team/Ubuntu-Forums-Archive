---
title: "Prob with boot.img.gz of dapper 6.0.6"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by titics on 2006-06-06
Hello guys,

im writing here cuz i have some prob for one USB bootable with dapper. With this same USB stick i did one brezzy bootable. Yesterday i downloaded the file boot.img.gz of dapper 6.0.6 from :

[http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/boot.img.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/boot.img.gz)

or

[http://ftp.interlegis.gov.br/pub/ubuntu/archive/dists/dapper/main/installer-i386/current/images/hd-media/boot.img.gz](http://ftp.interlegis.gov.br/pub/ubuntu/archive/dists/dapper/main/installer-i386/current/images/hd-media/boot.img.gz)

after the download i extracted the boot.img and i opened it with Winimage for create my USB bootable. So when i opened the boot.img with Winimage i have the following files:

boot.txt
disk.lbl
f1.txt
f2.txt
f3.txt
f4.txt
f5.txt
f6.txt
f7.txt
f8.txt
f9.txt
f10.txt
initrd.gz
ldlinux.sys
linux
splash.rle
syslinux.cfg

In my syslinux.cfg i have it :

```
DISPLAY boot.txt

F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt

DEFAULT install

LABEL install
    kernel linux
    append vga=normal initrd=initrd.gz ramdisk_size=10804 root=/dev/rd/0 rw  --
LABEL linux
    kernel linux
    append vga=normal initrd=initrd.gz ramdisk_size=10804 root=/dev/rd/0 rw  --
LABEL server
    kernel linux
    append base-installer/kernel/linux/extra-packages-2.6= pkgsel/install-pattern=~t^ubuntu-standard$ pkgsel/language-pack-patterns= pkgsel/install-language-support=false vga=normal initrd=initrd.gz ramdisk_size=10804 root=/dev/rd/0 rw  --

LABEL expert
    kernel linux
    append DEBCONF_PRIORITY=low vga=normal initrd=initrd.gz ramdisk_size=10804 root=/dev/rd/0 rw  --
LABEL server-expert
    kernel linux
    append base-installer/kernel/linux/extra-packages-2.6= pkgsel/install-pattern=~t^ubuntu-standard$ pkgsel/language-pack-patterns= pkgsel/install-language-support=false DEBCONF_PRIORITY=low vga=normal initrd=initrd.gz ramdisk_size=10804 root=/dev/rd/0 rw  --

LABEL rescue
    kernel linux
    append vga=normal initrd=initrd.gz ramdisk_size=10804 root=/dev/rd/0 rw  rescue/enable=true --

PROMPT 
```

And when i put the USB stick on my pc and when he is booting i got ```
Boot Error
```

Thx in advance for all help ;)

Good day

---

### Post by titics on 2006-06-06
No one got idea ?

---

### Post by titics on 2006-06-06
Ok i'll w8 some future release ..

Thx anyway

---

