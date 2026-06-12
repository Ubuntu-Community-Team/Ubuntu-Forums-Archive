---
title: "faild to boot both default and fallback entries"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by wthpr0 on 2010-10-12
I'm getting this error on ubuntu server 10.04
```
faild to boot both default and fallback entries
```

now i know kinda why it's doing this becuse i'm trying to change the kernal it's running on. But now i can't find away to get back to original kernal :( 

Here is the output of my boot folder:
```
root@bt:~# ls /mnt/hdb1/boot/
abi-2.6.32-21-server     config-2.6.33.7-rt29.backup  initrd.img-2.6.32-24-server      System.map-2.6.32-24-server      vmlinuz-2.6.32-21-server
abi-2.6.32-24-server     grub                         initrd.img-2.6.33.7-rt29.backup  System.map-2.6.33.7-rt29.backup  vmlinuz-2.6.32-24-server
 config-2.6.26-2-amd64    initrd.img-2.6.26-2-amd64    memtest86+.bin                   vmcoreinfo-2.6.32-21-server
 config-2.6.32-21-server  initrd.img-2.6.28.1          System.map-2.6.26-2-amd64        vmcoreinfo-2.6.32-24-server
 config-2.6.32-24-server  initrd.img-2.6.32-21-server  System.map-2.6.32-21-server      vmlinuz-2.6.26-2-amd64
```

btw: have it booted in BT4 right now since i can't boot ubuntu-server

---

