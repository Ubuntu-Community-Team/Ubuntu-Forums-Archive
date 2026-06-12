---
title: "remove grub folder completely and install it again(ubuntu 12.04)"
date: 2012-05-30
forum: Installation &amp; Upgrades
---

### Post by hamidhqs on 2012-05-30
this is my /boot Dir screenshot. and as you see there are grub,burg and another boot folder which has other grub files in it :confused:  all of these is because I had a problem to install burg and then reinstalling grub....
but now i'm going to remove all of them and install grub2 to neat it.
how can i do it???
```
 hamid@IDA-PC:~$ ls /boot/
abi-3.0.0-12-generic         initrd.img-3.2.0-24-generic
abi-3.0.0-15-generic         lost+found
abi-3.0.0-16-generic         memtest86+.bin
abi-3.0.0-17-generic         memtest86+_multiboot.bin
abi-3.2.0-24-generic         proc
boot                         System.map-3.0.0-12-generic
burg                         System.map-3.0.0-15-generic
config-3.0.0-12-generic      System.map-3.0.0-16-generic
config-3.0.0-15-generic      System.map-3.0.0-17-generic
config-3.0.0-16-generic      System.map-3.2.0-24-generic
config-3.0.0-17-generic      vmcoreinfo-3.0.0-12-generic
config-3.2.0-24-generic      vmcoreinfo-3.0.0-15-generic
dev                          vmcoreinfo-3.0.0-16-generic
extlinux                     vmcoreinfo-3.0.0-17-generic
grub                         vmlinuz-3.0.0-12-generic
initrd.img-3.0.0-12-generic  vmlinuz-3.0.0-15-generic
initrd.img-3.0.0-15-generic  vmlinuz-3.0.0-16-generic
initrd.img-3.0.0-16-generic  vmlinuz-3.0.0-17-generic
initrd.img-3.0.0-17-generic  vmlinuz-3.2.0-24-generic
```

---

### Post by darkod on 2012-05-30
It depends whether you can boot or you need to work from live mode.

If you can boot, you can completely remove any package and settings with:
sudo apt-get remove --purge <package_name>

So, to clean up burg it would be like (I guess, because I never use burg):
sudo apt-get remove --purge burg

To completely remove grub2, it's:
sudo apt-get remove --purge grub-pc grub-common

Then to install grub2 and create the config files:
sudo apt-get install grub-pc
sudo grub-mkconfig
sudo grub-install /dev/sdX (depends where you want to install it, like /dev/sda)

---

