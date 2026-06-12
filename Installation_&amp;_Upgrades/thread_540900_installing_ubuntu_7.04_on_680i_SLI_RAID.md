---
title: "installing ubuntu 7.04 on 680i SLI RAID"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by hicotton02 on 2007-09-02
So i have searched around for the past couple of hours and tried to keep from making another "install ubuntu on a  fake raid" post but.....here goes..

this is what i have:
EVGA 680i SLI mobo
2x36GB WD raptors.
Intel pentium D 820
2GB PQI Ram
XFX 7900GS

This is what i did
Pop in the live cd
System>Administration>Synaptic Package Manager
i added the universe repository thingy and hit reload
installed dmraid
Applications>Accessories>Terminal
ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# dmraid -r
/dev/sda: nvidia, "nvidia_dijifjhj", stripe, ok, 72303838 sectors, data@ 0

I think my issue is there. If im correct, i should have both drives showing. Now, if i go into gParted ill see a /dev/sda and /dev/sdb but no /dev/mapper/nvidia_dijifjhiXXX

but... check this out:
root@ubuntu:~# ls -l /dev/mapper/
total 0
crw-rw---- 1 root root  10, 62 2007-09-02 08:55 control
brw-rw---- 1 root disk 254,  0 2007-09-02 09:12 nvidia_dijifjhj

Any Ideas?

---

### Post by hicotton02 on 2007-09-02
also here is a tad more info.

Command (m for help): p

Disk /dev/mapper/nvidia_dijifjhj: 37.0 GB, 37019516928 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_dijifjhj1               1          19      152586   83  Linux
/dev/mapper/nvidia_dijifjhj2              20         263     1959930   83  Linux
/dev/mapper/nvidia_dijifjhj3             264        4500    34033702+  83  Linux

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 22: Invalid argument.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
root@ubuntu:~# dmraid -r
/dev/sda: nvidia, "nvidia_dijifjhj", stripe, ok, 72303838 sectors, data@ 0
root@ubuntu:~# ls -l /dev/mapper/
total 0
crw-rw---- 1 root root  10, 62 2007-09-02 08:55 control
brw-rw---- 1 root disk 254,  0 2007-09-02 09:21 nvidia_dijifjhj
root@ubuntu:~# dmraid -s
*** Active Set
name   : nvidia_dijifjhj
size   : 72303744
stride : 128
type   : stripe
status : ok
subsets: 0
devs   : 1
spares : 0
root@ubuntu:~# mkfs -t ext3 /dev/mapper/nvidia_dijifjhj1
mke2fs 1.40-WIP (14-Nov-2006)
Could not stat /dev/mapper/nvidia_dijifjhj1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?

---

### Post by hicotton02 on 2007-09-02
no dice?

---

### Post by didijeeeke on 2007-12-07
Bumb

Same chipset same problem...

---

