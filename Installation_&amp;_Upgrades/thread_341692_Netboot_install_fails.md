---
title: "Netboot install fails"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by midna on 2007-01-19
Ok well I'm trying again and again to get the netboot to work for the amd64-alternate release for edgy. It worked great for the i386 edgy server release but I keep getting an error retrieving a file when trying to do the amd64. 

I have the ubuntu-6.10-alternate-amd64.iso mounted to /media/iso and a symlink at /var/www/ubuntu to that mount. I have no problem actually booting to the netboot stuff and starting the installation, it just errors out and asks me to change mirrors... but if I attempt to change mirrors, I just well... can't. It just goes right back to the error, I suspect that is because I have my local server set as the mirror but there is no way to change mirrors midprocess so I can't use my nice 10/100 connection for the files that work and a remote mirror for the files that don't.

Ideas anyone? Thanks in advance :-D

/var/lib/tftpboot/pxelinux.cfg/default shows:

```
DISPLAY ubuntu-installer/amd64/boot-screens/boot.txt

F1 ubuntu-installer/amd64/boot-screens/f1.txt
F2 ubuntu-installer/amd64/boot-screens/f2.txt
F3 ubuntu-installer/amd64/boot-screens/f3.txt
F4 ubuntu-installer/amd64/boot-screens/f4.txt
F5 ubuntu-installer/amd64/boot-screens/f5.txt
F6 ubuntu-installer/amd64/boot-screens/f6.txt
F7 ubuntu-installer/amd64/boot-screens/f7.txt
F8 ubuntu-installer/amd64/boot-screens/f8.txt
F9 ubuntu-installer/amd64/boot-screens/f9.txt
F0 ubuntu-installer/amd64/boot-screens/f10.txt

DEFAULT install

LABEL install
        kernel ubuntu-installer/amd64/linux
        append ks=http://192.168.1.254/ke.cfg vga=normal initrd=ubuntu-installer/amd64/initrd.gz ramdisk_size=21234 root=/dev/ram rw  --
LABEL linux
        kernel ubuntu-installer/amd64/linux
        append vga=normal initrd=ubuntu-installer/amd64/initrd.gz ramdisk_size=21234 root=/dev/ram rw  --
LABEL server
        kernel ubuntu-installer/amd64/linux
        append base-installer/kernel/linux/extra-packages-2.6= pkgsel/install-pattern=~t^ubuntu-standard$ pkgsel/language-pack-patterns= pkgsel/install-language-support=false vga=normal initrd=ubuntu-installer/amd64/initrd.gz ramdisk_size=21234 root=/dev/ram rw  --

LABEL expert
        kernel ubuntu-installer/amd64/linux
        append priority=low vga=normal initrd=ubuntu-installer/amd64/initrd.gz ramdisk_size=21234 root=/dev/ram rw  --
LABEL server-expert
        kernel ubuntu-installer/amd64/linux
        append base-installer/kernel/linux/extra-packages-2.6= pkgsel/install-pattern=~t^ubuntu-standard$ pkgsel/language-pack-patterns= pkgsel/install-language-support=false priority=low vga=normal initrd=ubuntu-installer/amd64/initrd.gz ramdisk_size=21234 root=/dev/ram rw  --

LABEL rescue
        kernel ubuntu-installer/amd64/linux
        append vga=normal initrd=ubuntu-installer/amd64/initrd.gz ramdisk_size=21234 root=/dev/ram rw  rescue/enable=true --

PROMPT 1
TIMEOUT 0
```

/var/www/ke.cfg shows:

```
#System language
lang en_US
#Language modules to install
langsupport en_US
#System keyboard
keyboard us
#System timezone
timezone --utc America/New_York
#Use Web installation
url --url http://192.168.1.254/ubuntu/
```

---

### Post by samarium on 2007-03-05
Transparent squid proxy doing url redirection, maybe combined with apt-cacher?

---

