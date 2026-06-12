---
title: "Resize /boot"
date: 2015-04-01
forum: Installation &amp; Upgrades
---

### Post by jsland on 2015-04-01
Updates keep nagging about not enough space in boot.  This occurs before every new image update.  When using synaptic to remove older images can you safely use; mark for complete removal.

When removing older images the amount of disk space cleared is only a fraction of what the reported size of the image is/was.

This has only been a problem with 14.04.  What has changed.

What can be done to increase the size of /boot.

---

### Post by Bashing-om on 2015-04-01
jsland; Hello;;

Oh My ;
> 
What can be done to increase the size of /boot.


That is a question whose response involves a number of factors.
The 1st is why bother ? It is a lot of bother to resize partitions and does entail some risk of data loss.
Good housekeeping will in the majority of cases alleviate the /boot congestion. 
```

sudo apt-get autoremove

```
Will now remove old kernels, leaving the current and 1 for a backup.

Let's examine the situation as is, and see what might be done.
Post back the outputs - Between Code Tags - of terminal commands:
```

df -h
df -i
sudo fdisk -lu
sudo parted -l
dpkg -l | grep linux-
ls -al /

```

And we see where go from here.

[INDENT][INDENT]a start
[INDENT][INDENT][INDENT]but not complete
[INDENT][INDENT][INDENT]'til the paper work is done
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by rob-wilkins on 2015-04-03
[**[COLOR=#DD4814][B]Bashing-om**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1111508"), May I get in on this discussion? I have the same problem. Here are the results from your list of terminal commands..


======== start ==========
```
rob@rob-desktop:~$ df -h
Filesystem                          Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root         454G   19G  413G   5% /
none                                4.0K     0  4.0K   0% /sys/fs/cgroup
udev                                7.6G   12K  7.6G   1% /dev
tmpfs                               1.6G  1.4M  1.6G   1% /run
none                                5.0M     0  5.0M   0% /run/lock
none                                7.6G  148K  7.6G   1% /run/shm
none                                100M   56K  100M   1% /run/user
/dev/sdc2                           237M  182M   43M  82% /boot
/dev/sdc1                           511M  3.4M  508M   1% /boot/efi
/dev/mapper/isw_djegbcjfhd_Volume1  1.8T  101G  1.7T   6% /media/rob/beast
rob@rob-desktop:~$ ^C
rob@rob-desktop:~$ 
```

=================================

```
rob@rob-desktop:~$ df -i
Filesystem                            Inodes  IUsed     IFree IUse% Mounted on
/dev/mapper/ubuntu--vg-root         30179328 545880  29633448    2% /
none                                 1982842      2   1982840    1% /sys/fs/cgroup
udev                                 1979008    551   1978457    1% /dev
tmpfs                                1982842    606   1982236    1% /run
none                                 1982842      3   1982839    1% /run/lock
none                                 1982842      6   1982836    1% /run/shm
none                                 1982842     32   1982810    1% /run/user
/dev/sdc2                              62496    311     62185    1% /boot
/dev/sdc1                                  0      0         0     - /boot/efi
/dev/mapper/isw_djegbcjfhd_Volume1 122101760 321437 121780323    1% /media/rob/beast
rob@rob-desktop:~$ 
```

===========================

```
rob@rob-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 512.1 GB, 512110190592 bytes
255 heads, 63 sectors/track, 62260 cylinders, total 1000215216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  1000215215   500107607+  ee  GPT

Disk /dev/mapper/isw_djegbcjfhd_Volume1: 2000.4 GB, 2000395833344 bytes
255 heads, 63 sectors/track, 243200 cylinders, total 3907023112 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_djegbcjfhd_Volume1 doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-root: 494.4 GB, 494445527040 bytes
255 heads, 63 sectors/track, 60112 cylinders, total 965713920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 16.9 GB, 16852713472 bytes
255 heads, 63 sectors/track, 2048 cylinders, total 32915456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table
rob@rob-desktop:~$ 
```

===========================

```
rob@rob-desktop:~$ sudo parted -l
Model: ATA ST2000DM001-1ER1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  2000GB  2000GB  ext4


Model: ATA ST2000DM001-1ER1 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  2000GB  2000GB  ext4


Model: ATA SAMSUNG MZHPU512 (scsi)
Disk /dev/sdc: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name                  Flags
 1      1049kB  538MB  537MB  fat32        EFI System Partition  boot
 2      538MB   794MB  256MB  ext2
 3      794MB   512GB  511GB                                     lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 494GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  494GB  494GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 16.9GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  16.9GB  16.9GB  linux-swap(v1)


Model: Linux device-mapper (mirror) (dm)
Disk /dev/mapper/isw_djegbcjfhd_Volume1: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  2000GB  2000GB  ext4


rob@rob-desktop:~$ 
```

========================================

```
rob@rob-desktop:~$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.11                                            all          Firmware for Linux kernel drivers
ii  linux-headers-3.13.0-44                               3.13.0-44.73                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-44-generic                       3.13.0-44.73                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-45                               3.13.0-45.74                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic                       3.13.0-45.74                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-46                               3.13.0-46.79                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                       3.13.0-46.79                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-48                               3.13.0-48.80                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-48-generic                       3.13.0-48.80                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.48.55                                        amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-45-generic                         3.13.0-45.74                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-46-generic                         3.13.0-46.79                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-48-generic                         3.13.0-48.80                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                   3.13.0-45.74                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-48-generic                   3.13.0-48.80                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                                  3.13.0-48.80                                        amd64        Linux Kernel Headers for development
ii  linux-signed-generic                                  3.13.0.48.55                                        amd64        Complete Signed Generic Linux kernel and headers
ii  linux-signed-image-3.13.0-44-generic                  3.13.0-44.73                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-45-generic                  3.13.0-45.74                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-46-generic                  3.13.0-46.79                                        amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-48-generic                  3.13.0-48.80                                        amd64        Signed kernel image generic
ii  linux-signed-image-generic                            3.13.0.48.55                                        amd64        Signed Generic Linux kernel image
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
rob@rob-desktop:~$ 
```

==============================

```
rob@rob-desktop:~$ ls -al /
total 163
drwxr-xr-x  23 root root  4096 Mar 25 07:25 .
drwxr-xr-x  23 root root  4096 Mar 25 07:25 ..
drwxr-xr-x   2 root root 12288 Apr  3 09:55 bin
drwxr-xr-x   5 root root  3072 Apr  3 10:54 boot
-rw-r--r--   1 root root 52627 Jan 19 06:02 btusb.ko
drwxrwxr-x   2 root root  4096 Jan 12 05:31 cdrom
drwxr-xr-x  16 root root  4260 Apr  3 11:09 dev
drwxr-xr-x 149 root root 12288 Apr  3 11:30 etc
drwxr-xr-x   3 root root  4096 Jan 12 05:32 home
lrwxrwxrwx   1 root root    33 Mar 25 07:25 initrd.img -> boot/initrd.img-3.13.0-48-generic
lrwxrwxrwx   1 root root    33 Feb 19 15:52 initrd.img.old -> boot/initrd.img-3.13.0-46-generic
drwxr-xr-x  27 root root  4096 Mar 13 12:18 lib
drwxr-xr-x   2 root root  4096 Feb 27 00:23 lib64
drwx------   2 root root 16384 Jan 12 05:30 lost+found
drwxr-xr-x   3 root root  4096 Jan 12 05:38 media
drwxr-xr-x   4 root root  4096 Mar  2 15:59 mnt
drwxr-xr-x   3 root root  4096 Apr  3 09:49 opt
dr-xr-xr-x 259 root root     0 Apr  3 10:22 proc
drwx------   8 root root  4096 Mar 12 05:00 root
drwxr-xr-x  24 root root   780 Apr  3 10:54 run
drwxr-xr-x   2 root root 12288 Apr  3 09:45 sbin
drwxr-xr-x   2 root root  4096 Jul 22  2014 srv
dr-xr-xr-x  13 root root     0 Apr  3 10:22 sys
drwxrwxrwt   8 root root  4096 Apr  3 11:17 tmp
drwxr-xr-x  11 root root  4096 Feb 24 09:47 usr
drwxr-xr-x  13 root root  4096 Jul 22  2014 var
lrwxrwxrwx   1 root root    30 Mar 25 07:25 vmlinuz -> boot/vmlinuz-3.13.0-48-generic
lrwxrwxrwx   1 root root    30 Feb 19 15:52 vmlinuz.old -> boot/vmlinuz-3.13.0-46-generic
rob@rob-desktop:~$ 
```

===== end =====

Thanks for taking a look. Any suggestions will be appreciated.

---

### Post by rob-wilkins on 2015-04-03
I tried using gparted to shrink the lvm partition to make roo so I could  increase the size of /boot, but gparted indicates lvm partition has  only 16mib unused, which does not seem to reflect the actual usage. If  it makes a difference, the sdc physical disk is a M.2 Ultra pciex4 ssd.

---

### Post by Bashing-om on 2015-04-03
rob-wilkins; Hey !

You too are affected by:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)
Bug: /boot created to small .
Please subscribe and add your voice.

I know nothing of LVM .. so unable to advise on re-sizing. What you can do is to run terminal command:
```

sudo apt-get autoremove

```
to remove the old kernels, safely;
after each new kernel install .. and you should be able to deal with that small /boot . Other than that little thing, all else looks good.

[INDENT][INDENT][INDENT]one of those things[/INDENT][/INDENT][/INDENT]

---

### Post by rob-wilkins on 2015-04-03
Thanks so much for taking a look at my issue. I will definitely subscribe to that bug thread. I had run the sudo apt-get autoremove prior to posting the other data and I am still about 47.6mb shy of being able to update the latest linux base update as the system is. 
After running 
> sudo apt-get autoremove

and as reccomended by the software updater:
> sudo apt-get clean

I still get this message when I try to install the 66.9 bMB update.

> The upgrade needs a total of 91.8 MB free space on disk '/boot'. Please free at least an additional 47.6 MB of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

I appreciate you assistance. If you have any additional ideas for me, please share them. Otherwise, I will run with what you posted above.

Have a great day!

---

### Post by rob-wilkins on 2015-04-03
I figured out how to remove the extra versions that autoremove was ignoring by using synaptic package manager. I guess autoremove does not remove images that are still available on the server.

---

### Post by Bashing-om on 2015-04-03
rob-wilkins; Well ..

"autoremove" I had expected to remove -44 and -45 kernels, giving you the room. -maybe they were marked as 'manual' and thus 'autoremove' would not touch them - (??)

```

sysop@1404mini:~$ uname -r
3.13.0-48-generic
sysop@1404mini:~$

```
is the latest kernel.

Let's look and see what is left now for cleanup:
```

dpkg -l | grep linux-

```
I expect to see packages marked 'rc' ( Removed but Config files remain) .

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT][INDENT]sometimes, not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jsland on 2015-04-05
Thanks for jumping in rob-wilkins and keeping the thread active.

For me on this release, 14.04 Studio, the autoremove cmd in terminal has never done anything particularly useful.  Nor has bleachbit.  Last go 'round for this update problem the old images where removed in a brute force manner of deleting files and using synaptic to clear out what autoremove is purported to do.

Using dpkg -l | grep linux- there are a lot of rc labeled image parts remaining going back all the way to -24.  Latest v. here is -46

what looks interesting to me is this:  Disk /dev/mapper/ubuntu--gnome--vg-root doesn't contain a valid partition table

---

### Post by jsland on 2015-04-05
Maybe someone can tell me what is being said in the following;

2) Systems where linux-image-<version>-{generic,server,goldfish,lowlatency} don't get suggested for autoremoval after upgrade to newer versions of linux-{generic,server,goldfish,lowlatency}/linux-image-{generic,server,goldfish,lowlatency}. Mostly because some dkms-based kernel-modules are installed like NVIDIA/AMD propietary video drivers or VirtualBox. dkms recommends virtual package linux-image provided by each and every linux-image-<version>-{generic,server,goldfish,lowlatency}. That prevents their autoremoval as long as dkms is installed and apt is configured not to autoremove recommended packages (Apt::AutoRemove::RecommendsImportant).

Between 'dkms' and reconfiguring apt what is a logical way to clear up the problem for some of us with {generic,server,goldfish,lowlatency}

---

### Post by ian-weisser on 2015-04-05
> **jsland said:**
> Between 'dkms' and reconfiguring apt what is a logical way to clear up the problem for some of us with {generic,server,goldfish,lowlatency}

One logical way would be for apt to be much more clever about marking and virtual packages...however, that opens a whole new range of rare, hard-to-diagnose, harder-to-triage possible bugs.

Another logical way would be to change the dkms dependences from virtual packages to real binary packages...but again, that might cause more problems than it solves for many users.

Another logical way for some users has been to reinstall without encryption/LVM that they were not using anyway.

There are many logical ways depending upon your needs.

The simplest workaround for many users, for now, is to merely mark the calendar, and manually conduct this minor maintenance chore every month or two until a better fix arrives.

---

### Post by jsland on 2015-04-06
Thanks Ian.  The last suggestion is the best one.

Clearing out all but the current image with synaptic using Mark for Complete Removal clears out alot more space than just using Mark for Removal on the older images.  Complete Removal also doesn't seem to break anything as it often does when using it on other packages.

---

### Post by Bashing-om on 2015-04-06
jsland; Hey;

An additional explanation of what might be taking place, and a means of coping:
[http://ubuntuforums.org/showthread.php?t=2256452](http://ubuntuforums.org/showthread.php?t=2256452)

Ian, I always look forward to your instruction.

[INDENT][INDENT]all a process of learning
[/INDENT][/INDENT]

---

### Post by v3.xx on 2015-04-06
Nice link Bashing
```
apt-mark showauto ^linux-image-
```
I can see that coming in handy, LVM or not.

---

### Post by Bashing-om on 2015-04-06
v3.xx; Heh ;

So many
 real smart people frequent this forum.
> **v3.xx said:**
> Nice link Bashing
```
apt-mark showauto ^linux-image-
```
I can see that coming in handy, LVM or not.

(you are on that list :) )
Never can tell what gems of expertise one will pick up

[INDENT][INDENT][INDENT][INDENT]next
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jsland on 2015-04-06
Using;
     dpkg -S /lib/modules | sed s/:.\*// 
shows the older headers ranging back to ver. -24

Can the older headers be safely removed by manually deleting them from /lib/modules without causing stability issues

---

### Post by Bashing-om on 2015-04-06
jsland; Nope;

That would bite the hand that feeds the system . At all cost avoid going behind the package manager's back.
Use the package manager to do this:

Something like
```

sudo apt-get purge linux-headers-3.13.0-{24,27,28}

```
should work nicely.
This should remove those packages from ' /lib/modules ' and all else.
- and yes one could use the GUI application synaptic to do this -

EDIT: Order of operations:
1. remove linux-image-XXXX
2. remove linux-image-extra-XXXX
3. remove linux-headers-XXXX-generic
4. remove linux-headers-XXXX

[INDENT][INDENT]it is not nice to fool mother apt
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2015-04-06
Bashing-om is quite right.
DO NOT manually delete files, including headers, that were installed by the package manager. Down that path lies great, great frustration.

1) Remove old kernels, including headers, by simply using autoremove
```
sudo apt-get autoremove
```

2) Sometimes autoremove, for several possible valid reasons, doesn't work. Then remove the kernel *image* package, and the header will become an orphaned dependency and eligible for autoremoval. This is a clean way to remove old kernels.
```
sudo apt-get remove linux-image-3.16.0-29-generic
sudo apt-get autoremove
```

3) On rare occasions (related to the way *apt-marking* works), a header package is left behind, orphaned after the image package is removed. Removing the header package is as simple as:
```
sudo apt-get remove linux-headers-3.16.0-29-generic
```

---

