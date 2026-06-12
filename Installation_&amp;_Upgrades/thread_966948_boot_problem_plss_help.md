---
title: "boot problem plss help"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by kaushikashwin on 2008-11-01
i installed ubuntu 8.10 in E:(10GB partition) from vista 32bit x86
everythin went fine.installed.
but during boot,even ubuntu screen appears but after that i get this msg

current working directory (ie,the relative path) is ubuntu/disks
     [linux-bzImage,setup 0x3000 , size =0x220cb0]
     [linux-initrd @ 0x7e5a1000 , 0xB0dac8 bytes]
loading please wait
gave up waiting for root device.   commom problem:
   -boot args(cat  /proc/cmdline)
       -check rootdelay=(did system wait long enough?)
       -check root=(did system wait long for right device?)
   -missing modules (cat /proc/modules ; IS /dev)
ALERT! /dev/disk/by-UUID/9E08EBBF08EB9495  does not exist.dropping to shell!


Busybox v1.10.2 (ubuntu 1:1.10.2-(ubuntu6)built-in shell(ash)
enter help for a list of built in commands

(initrafns) [35.656279]ata1.00:revalidation failed (errno=-19)



i donno wat this s n i m new to linux.plss help me solve this pblm n plss do a detail explanation coz i donno abt those commands.thnk u ppl in advance.

---

### Post by laney_1 on 2008-11-01
it seems that something failed to install,

try reinstalling with the live cd,

i'm kinda new to ubuntu as well so i might not be correct:(

laney_1

---

### Post by hocutth on 2008-11-03
I get exactly the same messages starting with the 'Gave up waiting for root device'

I did check the uuid and it does exist.  The problem with the alert message is that '/dev/disk' does not exist.

I've tried both the graphical and the alternative install with the same results.

Pointers will be greatly appreciated.

---

### Post by kaushikashwin on 2008-11-03
i gav up n installed 8.04 n its sound pblm in 8.04 n i m ](*,) for it

---

