---
title: "Mount Failed on boot (press m then type mount -a)"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by charliehorse55 on 2010-06-12
Every time I boot Ubuntu, I get a disk error. Something about drives failed to mount. 

It complains about my /home drive. 

The solution is to 

1. Press "M" for manual recovery
2. Type "mount -a" (remounts all drives)
3. Type "exit" (exit from recovery shell)

BTW, / is a 32 GB SSD

/home is a 1 TB WD Caviar Black


How can I fix this error? It's very annoying to have to do this every time I reboot. (also it means that reboot after power failure wont work, im running a personal server, so this is a necessity.)

My fstab

cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=cca6df12-a6c0-48d0-9795-d3a4ce274b14 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda1 during installation
UUID=6dc298d9-d391-48fd-b34d-3119b8645d24 /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=b0352158-c39f-4097-af5b-d1887eeb0bf7 none            swap    sw              0       0

```

---

