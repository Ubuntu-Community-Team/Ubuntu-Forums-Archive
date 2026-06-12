---
title: "no cd-rom  install ubuntu server 8.04lts"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by frantzsong on 2010-01-09
i use the [http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-amd64/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-amd64/current/images/hd-media/) for 2 files
 
[IMG]http://archive.ubuntu.com/icons/compressed.gif[/IMG][initrd.gz]("http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-amd64/current/images/hd-media/initrd.gz")09-Jul-2009 02:03 5.9M [IMG]http://archive.ubuntu.com/icons/unknown.gif[/IMG][vmlinuz]("http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-amd64/current/images/hd-media/vmlinuz")09-Jul-2009 02:03 1.8M 
 
and the grub4dos.
boot.ini
> [boot loader]
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
timeout=3
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\grldr=Ubuntu install

menu.lst
> title Ubuntu 8.04 Server Setup
root (hd0,0) 
kernel /vmlinuz root=/dev/ram ramdisk_size=256000 devfs=mount,dall
initrd /initrd.gz 
boot
 
and i can run grub.
 
but when "choose language"
 
my keybroad dont work.
 
why?
 
many thanks.
 
computer info..
AMD3600+
a690g

---

