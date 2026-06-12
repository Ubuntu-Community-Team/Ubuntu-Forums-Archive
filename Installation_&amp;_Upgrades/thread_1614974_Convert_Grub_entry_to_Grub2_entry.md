---
title: "Convert Grub entry to Grub2 entry?"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by iDleR on 2010-11-06
Hi guys! So here's the thing. I have two partition in my netbook (plus swap):
  /dev/sda4 with Ubuntu 10.4 /dev/sda5 with Centos 5.5
  I use Ubuntu obviously. Centos is there because I need to run some  test on that distro. The problem is Centos uses Grub and Ubuntu uses  Grub2.
  This is /boot/grub/menu.lst from Centos:
  ```
default=0 timeout=5 splashimage=(hd0,4)/boot/grub/splash.xpm.gz
  title CentOS (2.6.18-194.17.4.el5xen)
        root (hd0,4)
        kernel /boot/xen.gz-2.6.18-194.17.4.el5
        module /boot/vmlinuz-2.6.18-194.17.4.el5xen ro root=LABEL=/1 rhgb quiet
        module /boot/initrd-2.6.18-194.17.4.el5xen.img
title CentOS (2.6.18-194.el5xen)
        root (hd0,4)
        kernel /boot/xen.gz-2.6.18-194.el5
        module /boot/vmlinuz-2.6.18-194.el5xen ro root=LABEL=/1 rhgb quiet
        module /boot/initrd-2.6.18-194.el5xen.img
``` The /boot/grub/grub.cfg from Ubuntu:
  ```
menuentry "CentOS release 5.5 (Final) (on /dev/sda5)" {
        insmod ext2
        set root='(hd0,5)'
        search --no-floppy --fs-uuid --set 66daaf1a-53b0-4e12-96f3-db01d52e12d1
        linux /boot/vmlinuz-2.6.18-194.17.4.el5xen root=/dev/sda5
}
menuentry "CentOS release 5.5 (Final) (on /dev/sda5)" {
        insmod ext2
        set root='(hd0,5)'
        search --no-floppy --fs-uuid --set 66daaf1a-53b0-4e12-96f3-db01d52e12d1
        linux /boot/vmlinuz-2.6.18-194.el5xen root=/dev/sda5
}
``` This was generated running update-grub2 and grub-install under Ubuntu. It's not working. It gives me something like *bad magic number*.
  How can I convert the grub1 entry in a grub2 shape?

---

### Post by dabl on 2010-11-06
The format of your "other OS" entries doesn't look quite right, in comparison to the one on my Kubuntu 10.10 system:

```
menuentry "Debian GNU/Linux, with Linux 2.6.36-0.slh.3-aptosid-amd64 (on /dev/sdc1)" {
	insmod part_msdos
	insmod jfs
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set dfd5d21c-b8d7-4dd7-8d44-ac3146008354
	linux /boot/vmlinuz-2.6.36-0.slh.3-aptosid-amd64 root=UUID=dfd5d21c-b8d7-4dd7-8d44-ac3146008354 ro quiet quiet
	initrd /boot/initrd.img-2.6.36-0.slh.3-aptosid-amd64
}
```

In particular, note the "set root=" format, and also that you don't show an initrd entry.

The "bad magic number" appears to be an issue between BIOS and some kernels:

[http://ubuntuforums.org/showthread.php?t=1546640&page=2](http://ubuntuforums.org/showthread.php?t=1546640&page=2)

---

### Post by dino99 on 2010-11-06
grub & grub2 are not good friends, so only install grub2 (grub-pc) on /dev/sda and remove grub on Centos and menu.lst too, then update grub2

---

### Post by oldfred on 2010-11-06
Your grub2 entry is missing initrd:

/boot/initrd-2.6.18-194.17.4.el5xen.img

If the update to grub is not finding it correctly, I would copy entry to 40_custom and add the initrd line. Then you could turn off os prober so you do not have duplicate entries.

There used to be  an issue relating to magic numbers, but I thought they fixed it:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix)

---

