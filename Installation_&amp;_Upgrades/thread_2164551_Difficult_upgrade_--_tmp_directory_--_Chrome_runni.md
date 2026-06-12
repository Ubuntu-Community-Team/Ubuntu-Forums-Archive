---
title: "Difficult upgrade -- /tmp directory -- Chrome running out of memory"
date: 2013-07-31
forum: Installation &amp; Upgrades
---

### Post by JGT on 2013-07-31
Hi

I Upgraded from 12.04 to 13.04 over the weekend. Grub couldn't find my partitions afterwards so I had to recover using a boot repair disk.

Things are okay apart from two problems:

1) When I booted for the first time, my PC said the tmp directory was missing. (I don't have a log of the exact message, sorry). My root directory still lists the tmp directory highlighted in green. I can cd into the tmp directory though.

2) When I use Chromium browser, tabs keep running out of memory. Youtube rarely works.

I think these two things are related. What can I do? 

-- Thanks





Chrome keeps runig out

---

### Post by dino99 on 2013-08-01
i suppose your swap partition is not activated. Check that /etc/fstab uuids match the "sudo blkid" output
and remember to clean your system: clean/autoclean/autoremove/gtkorphan/bleachbit

---

### Post by JGT on 2013-08-01
Thank-you. I barely know how to follow your instructions. I'm usually happy to experiment.

```
john@john-Dell-DV051:~$ cat /etc/fstab uuids
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=7213dfa0-b28c-44b1-8666-c5a2c301dd12 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=15a48bde-14c9-4ad9-8ba6-123faf98a53a none            swap    sw              0       0
cat: uuids: No such file or directory
```

then

```
john@john-Dell-DV051:~$ sudo blkid
[sudo] password for john: 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0310" TYPE="vfat" 
/dev/sda2: UUID="E0FCAE34FCAE053E" TYPE="ntfs" 
/dev/sda3: LABEL="DellRestore" TYPE="vfat" 
/dev/sda5: UUID="7213dfa0-b28c-44b1-8666-c5a2c301dd12" TYPE="ext3" 
/dev/sda6: UUID="15a48bde-14c9-4ad9-8ba6-123faf98a53a" TYPE="swap" 
```

I don't know what to do with:```
clean/autoclean/autoremove/gtkorphan/bleachbit
```

---

### Post by JGT on 2013-08-02
Um, I've worked out that bleachbit is a program. I've installed it but it has GUI options like "shred" and "wipe" which I do not wish to try out.

I think that the following is telling me that the swap partition isn't mounted, as you suspected:

```
# <file system> **<mount point>**   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=7213dfa0-b28c-44b1-8666-c5a2c301dd12 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=15a48bde-14c9-4ad9-8ba6-123faf98a53a **none**            swap    sw              0       0
```

---

### Post by JGT on 2013-08-07
bump

---

### Post by SlugSlug on 2013-08-07
fstab is fine

try 

```
 sudo swapon
```


also 

post output of

```
 df -h
```

```
 free -m
```

```
 ls -l /
```

---

### Post by JGT on 2013-08-23
I tried sudo swapon -a

then:

df -h

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        19G   17G  983M  95% /
udev            236M  4.0K  236M   1% /dev
tmpfs            98M  840K   97M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            244M   68K  244M   1% /run/shm
none            100M     0  100M   0% /run/user
```

free -m

```
           total       used       free     shared    buffers     cached
Mem:           486        461         25          0          6        299
-/+ buffers/cache:        155        331
Swap:          941         70        870

```

ls -l /

```
total 96
drwxr-xr-x   2 root root  4096 Jul 26 02:10 bin
drwxr-xr-x   3 root root  4096 Aug 20 18:43 boot
drwxr-xr-x   2 root root  4096 Aug 22  2012 cdrom
drwxr-xr-x  16 root root  4360 Aug 23 18:39 dev
drwxr-xr-x 162 root root 12288 Aug 23 20:37 etc
drwxr-xr-x   3 root root  4096 Aug 22  2012 home
lrwxrwxrwx   1 root root    32 Aug 20 18:42 initrd.img -> boot/initrd.img-3.5.0-39-generic
lrwxrwxrwx   1 root root    33 Aug 20 18:41 initrd.img.old -> /boot/initrd.img-3.5.0-39-generic
drwxr-xr-x  21 root root  4096 Jul 26 01:48 lib
drwx------   2 root root 16384 Aug 22  2012 lost+found
drwxr-xr-x   3 root root  4096 Aug  6 21:29 media
drwxr-xr-x   2 root root  4096 Apr 19  2012 mnt
drwxr-xr-x   2 root root  4096 Apr 23  2012 opt
dr-xr-xr-x 141 root root     0 Aug 23 19:39 proc
drwx------   9 root root  4096 Aug  8 17:36 root
drwxr-xr-x  22 root root   780 Aug 23 20:37 run
drwxr-xr-x   2 root root 12288 Jul 26 01:52 sbin
drwxr-xr-x   2 root root  4096 Mar  5  2012 selinux
drwxr-xr-x   2 root root  4096 Apr 23  2012 srv
dr-xr-xr-x  13 root root     0 Aug 23 19:39 sys
drwxrwxrwt  10 root root  4096 Aug 23 21:31 tmp
drwxr-xr-x  10 root root  4096 Apr 23  2012 usr
drwxr-xr-x  14 root root  4096 Aug 23 07:11 var
lrwxrwxrwx   1 root root    29 Aug 20 18:42 vmlinuz -> boot/vmlinuz-3.5.0-39-generic
lrwxrwxrwx   1 root root    29 Aug 20 18:41 vmlinuz.old -> boot/vmlinuz-3.5.0-39-generic
```

---

### Post by JGT on 2013-09-11
Bump - not resolved yet

---

