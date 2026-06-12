---
title: "[SOLVED] Fails on removal of kernel module."
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by secondstage on 2008-10-18
I booted up and encountered GRUB with two kernels, so I booted into the newest one, and tried to remove the old one. In this the old one is 2.6.24-19-rt. I marked "remove" in synaptic, and it failed. So I brushed it off and said the heck with it. But now when I go to install a program, both synaptic, and apt-get try to remove linux-ubuntu-modules-2.6.24-19-rt, and install said program. They fail saying....
```
john@John:~$sudo apt-get install gnump3d

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  zinf
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-19-rt
The following NEW packages will be installed:
  gnump3d
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 634kB of archives.
After this operation, 12.5MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://ftp.usf.edu hardy/universe gnump3d 3.0-2 [634kB]
Fetched 634kB in 1s (434kB/s)   
Preconfiguring packages ...
(Reading database ... 160914 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-19-rt ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-rt

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-rt
dpkg: error processing linux-ubuntu-modules-2.6.24-19-rt (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-19-rt
E: Sub-process /usr/bin/dpkg returned an error code (1)
john@John:~$ 


```

---

### Post by Pumalite on 2008-10-18
Post:
df -h

---

### Post by secondstage on 2008-10-19
```
john@John:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             182G   51G  123G  30% /
varrun               1007M  120K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M   64K 1007M   1% /dev
devshm               1007M  164K 1007M   1% /dev/shm
lrm                  1007M   40M  968M   4% /lib/modules/2.6.24-21-rt/volatile
/dev/sda6              46M   40M  3.5M  92% /boot
john@John:~$ 

```

---

### Post by Pumalite on 2008-10-19
That 92% on /boot might be your problem.

---

### Post by secondstage on 2008-10-20
So just resize it?

EDIT: I resized the /dev/sda6 partition to 64 MB, bringing the percent used down to 70%. The old kernel is now removable, thanks a bunch.

---

