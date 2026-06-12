---
title: "stuck installing xubuntu from hard drive"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by smile_sunshine on 2006-11-09
Hi, 
I've got sort of half way with installing xubuntu from an iso image on the hard drive (have another linux distro running on another partition) and got stuck. - any ideas?

so far I've:

1. mounted iso image using mount -o loop -t iso9660 [filename.iso] [location]
   to access the files

2. copied vmlinuz and initrd.gz from this

3. put vmlinuz, initrd.gz and the iso file in /boot/xubuntu

4. added this to lilo:
    
# Partition 4: ubuntu install
image = /boot/xubuntu/vmlinuz
    label = xubuntu
    initrd = /boot/xubuntu/initrd.gz
    root = /dev/ram0
    append = "devfs=mount, dall ramdisk_size=16000"  

5. rebooted the computer and booted this - it does boot but comes up with the following error messages:

mounting /dev/root on /root failed - no such device
mounting /root/dev on /dev/.static/dev failed -no such file or directory
mounting /sys on /root /sys failed - no such file or directory
target filesystem doesnt have /sbin/init
/bin/sh: can't access tty

It leaves me with a command line and something called busybox? but no autoinstaller or anything and I dont know how to install it from this??
 

- any ideas - how I can install it from this / how i get the autoinstaller up / or what I did wrong in booting it??

thanks :)

---

### Post by Osamabingandhi on 2006-11-11
sorry i have no help for you, got the same problem. My motherboard has nforce 570 that is managing the harddrives, maybe that is the problem. Sata drives +nforce 570. Maybe it is to new for ubuntu edgy?

---

### Post by smile_sunshine on 2006-11-12
hey,
dont think thats the problem with mine since my computer is olllld!
wondered if it might be because need specific hd-media version of vmlinuz and initrd.gz ?????

 ( here:   but cant get it to download, it just freezes firefox :(  ) 
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current//images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current//images/hd-media/)

---

