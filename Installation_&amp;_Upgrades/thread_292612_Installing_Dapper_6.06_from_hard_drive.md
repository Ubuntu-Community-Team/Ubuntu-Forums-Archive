---
title: "Installing Dapper 6.06 from hard drive"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by whatusername on 2006-11-04
Right now, I am trying to get 6.06 installed from my hard drive. I am following the CD approach from: [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows) . I mounted the ISO (it's the alternate install one) in Alcohol 52%, I copy the files to C:\ubuntu\, and I get grldr and put it into the root of C:\. I edit menu.lst and  boot.ini. After that, I restarted my computer and went to the install, the start of the installation starts up fine, then when it checks for the CD, it says it can't find it.


If the contents of menu.lst and boot.ini are of help, here they are:
menu.lst
```
title Ubuntu 6.06 installer
kernel   (hd0,0)/ubuntu/install/vmlinuz root=/dev/ram0 devfs=mount,dall ramdisk_size=17000
initrd   (hd0,0)/ubuntu/install/initrd.gz
```

boot.ini
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
c:\grldr="Ubuntu 6.06 installer"

```

EDIT: I'd also like to know if it's best to use NTFS or FAT32 for my partition.

---

