---
title: "disable dmsetup"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by asundaresan on 2006-07-14
Hi,

I have 3 hard discs in a RAID0 mode. The RAID is performed in hardware. When dapper boots up the device is recognised as **/dev/sda** and it has a single ext3 formatted partition **/dev/sda1**. However on subsequent boots, it refuses to mount.

It says that /dev/sda1 is busy or already mounted although it isn't mounted. I found later that dmsetup is managing this device. 

```
dmsetup remove sda1
```

solved the problem. 

Is it enough to disable dmsetup managing **/dev/sda*** by editing **/etc/lvm/lvm.conf** to include 
```
    filter = [ "r|/dev/cdrom|" "r|/dev/sda*|" ]

```

Thanks,
Aravind.

---

### Post by asundaresan on 2006-07-15
This has been fixed. The problem was the startup script **/etc/init.d/evms**. I don't know if evms is really necessary for me and since the machine is not run as a desktop, I guess it isn't. It can be removed by
```

update-rc.d -f evmd remove

```

---

