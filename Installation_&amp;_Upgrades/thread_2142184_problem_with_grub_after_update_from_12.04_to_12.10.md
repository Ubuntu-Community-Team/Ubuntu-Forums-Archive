---
title: "problem with grub after update from 12.04 to 12.10"
date: 2013-05-04
forum: Installation &amp; Upgrades
---

### Post by kari0ca on 2013-05-04
Hi there, 


Im having a problem with grub after the update from kubuntu 12.04 to 12.10.
i have tried several hints that i have googled, but none of them worked for me.


This is my fake raid 0 configuration:
[IMG]http://i40.tinypic.com/2mqj311.png[/IMG]
pdc_cejhgegiib1 -> winxp 
pdc_cejhgegiib5 -> win7
pdc_cejhgegiib6 -> Kubuntu
pdc_cejhgegiib7 -> storage


when i tried to fix this problem, ive followed this post:  [http://askubuntu.com/questions/19789/restoring-grub2-on-software-raid-0-using-livecd-after-windows-7-wiped-it](http://askubuntu.com/questions/19789/restoring-grub2-on-software-raid-0-using-livecd-after-windows-7-wiped-it)
```
cat /proc/partitions
```
the result was:
```
major minor  #blocks  name


   7        0     658380 loop0
   8        0  488386584 sda
   8       16  488386584 sdb
   8       32  488386584 sdc
   8       33  488375968 sdc1
 253        0  976562432 dm-0
 253        1   10241406 dm-1
 253        3  256003776 dm-3
 253        4   51199123 dm-4
 253        5  659106756 dm-5
 253        6      11136 dm-6
```


the next step was:
```
sudo grub-mkdevicemap -m -
```
the result:
```

(hd0)   /dev/disk/by-id/ata-ST3500418AS_6VM5CFFW
(hd1)   /dev/disk/by-id/ata-ST3500418AS_5VM74093
(hd2)   /dev/disk/by-id/ata-SAMSUNG_HD502HI_S1ZVJ50Z559745
(hd3)   /dev/mapper/pdc_cejhgegiib
```


after that:
```
$ sudo mount /dev/mapper/pdc_cejhgegiib6 /mnt
$ sudo mount --bind /dev /mnt/dev
$ sudo mount --bind /proc /mnt/proc
$ sudo mount --bind /sys /mnt/sys
```


then I have done:
```
sudo grub-mkdevicemap -m - | sudo grub-probe --device-map=/proc/self/fd/0 --target=device /mnt
```
Ive got:
```
/dev/mapper/pdc_cejhgegiib6
```


the next step was:
```
sudo grub-mkdevicemap -m - | sudo grub-probe --device-map=/proc/self/fd/0 --target=drive /mnt
```
the result:
```
(hd3,msdos6)
```


then the final steps
```
sudo chroot /mnt /bin/bash
sudo update-grub
```
and this was the result:
```
sudo: unable to resolve host ubuntu
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-28-generic
Found initrd image: /boot/initrd.img-3.5.0-28-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found Windows 7 (loader) on /dev/mapper/pdc_cejhgegiib1
done
```


the grand finale:
```
sudo grub-install /dev/mapper/pdc_cejhgegiib  or
sudo grub-install --root-directory=/mnt /dev/mapper/pdc_cejhgegiib

```
for my surprise:
```
Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.
```


this is my log
[http://paste.ubuntu.com/5632393/](http://paste.ubuntu.com/5632393/)


can anyone help on this?

---

### Post by dino99 on 2013-05-05
you first need to fix that "unknown" filesystem about that raid0 
 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://translate.google.com/translate?hl=fr&ie=UTF8&prev=_t&sl=fr&tl=en&u=http://www.sylvainlasnier.fr/blog/probleme-grub2-avec-un-fake-raid-sur-ubuntu-quantal-1210](http://translate.google.com/translate?hl=fr&ie=UTF8&prev=_t&sl=fr&tl=en&u=http://www.sylvainlasnier.fr/blog/probleme-grub2-avec-un-fake-raid-sur-ubuntu-quantal-1210)

---

