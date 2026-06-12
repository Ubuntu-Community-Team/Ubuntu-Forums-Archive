---
title: "Ubuntu, Fedora and compiling kernel"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by jcd2020 on 2007-09-18
Hi,
I'm dual-booting Ubuntu 7.04 and Fedora Core 6 and all was well until I tried to compile new kernel on Fedora. When trying to boot this new kernel (the 2.6.18 which came with the install still works)I'm getting a kernel panic preceded by these messages: "Switchroot: mount failed No such file or directory", "unable to access resume device /dev/sda9" "could not find filesystem /dev/root/". I compiled the sources with no errors, and used .config file from the working kernel.
This is cat /etc/fstab in fedora:
```
LABEL=/                 /                       ext3    defaults        1 1
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
/dev/sda10              /media/stuff            vfat    defaults        0 0
proc                    /proc                   proc    defaults        0 0
sysfs                   /sys                    sysfs   defaults        0 0
/dev/sda9               swap                    swap    defaults        0 0
/dev/sda8               swap                    swap    defaults        0 0

```
and in ubuntu:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=d873b8d0-f1e0-4838-8595-445ab3bd2e55 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=ce9dfb8a-ec94-49fa-8d9c-c3e6df450e62 /media/lin2     ext3    defaults        0       2
# /dev/sda10
UUID=927F-576B  /media/stuff    vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=6A84565E84562D37 /media/vista    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=80188F34188F286C /media/winxp    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=a917ccdb-355b-4f28-bf29-6c81ad97fab8 none            swap    sw              0       0
# /dev/sda9
UUID=048faf57-2cb7-460b-84b9-59a753730c97 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```
sda6 is ubuntu, sda7 is fedora. These are the contents of ubuntu's menu.lst regarding fedora: ```

title           Fedora Core 6 2.6.22.1S
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.22.1S ro root=/dev/sda7 selinux=0
initrd          /boot/initrd-2.6.22.1S.img

title           Fedora Core 6 2.6.18
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.18-1.2798.fc6 ro root=/dev/sda7 selinux=0
initrd          /boot/initrd-2.6.18-1.2798.fc6.img


``` 
The latter works, the former doesn't. When I compiled new kernel I used make mrproper, make menuconfig, make all, make modules_install and make install.  Could my problems be caused by the lack of grub.conf file on the fedora's partition?
Thank you for any help.

---

### Post by Pumalite on 2007-09-18
Who owns the Grub?.

---

### Post by jcd2020 on 2007-09-18
Ubuntu on sda6

---

### Post by Pumalite on 2007-09-18
In Ubuntu terminal:
sudo fdisk -lu
cat /boot/grub/menu.lst
Post the output of both here.

---

### Post by jcd2020 on 2007-09-18
I've just finished compiling kernel 2.6.18.1 and it works. Earlier I've read somewhere that there are some differences in with drivers for SATA drives between 2.6.18 and 2.6.22, and they cause similar problems, so that's probably it. Also, how can I change something in kernel sources so there's a custom message in the output of uname -a (besides changing local version in the config)?

---

### Post by Pumalite on 2007-09-18
Glad you got it working! I'm sure you can keep your kernel version in your memory; especially after you compiled it yourself.

---

