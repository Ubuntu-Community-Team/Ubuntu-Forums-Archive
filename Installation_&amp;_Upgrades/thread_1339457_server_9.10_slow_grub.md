---
title: "server 9.10 slow grub"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by lbharti on 2009-11-27
I am facing this weird delay after the screen displays:  
```
Grub Loading.. 
```
and keeps spinning the boot device for at least 30 seconds. After that it boots normally.

My system configuration is as follows:
- PATA hard drive (not bootable) => sda
- SATA hard drive (with boot and / partitions) => sdb
- SATA hard drive => sdc

It seems to me that grub keeps scanning for the bootable partitions until it finds it.

I have tried installing using grub 
```
root (hd1,2)
setup (hd1)
```

but it returns errors about missing files.

```
grub-install /dev/sdb and /dev/sdb1
``` complete successfully, but the problem remains the same.

What should I do?

---

### Post by oldfred on 2009-11-27
There is a known bug on multidrive systems where grub spends a lot of extra time rescanning.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS
sudo dpkg-reconfigure grub-pc

---

