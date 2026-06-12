---
title: "Cannot perform update"
date: 2013-09-05
forum: Installation &amp; Upgrades
---

### Post by alfirdaous on 2013-09-05
Hello everybody

I was truing to do a usual update, an error has appeared:

[CENTER][IMG]http://s18.postimg.org/6y25e89uh/update_Error.png[/IMG]
[/CENTER]


Thanks in advance

---

### Post by TheFu on 2013-09-05
Open a terminal.
Run```

sudo apt-get update && sudo apt-get dist-upgrade
```
Copy and past the results back here, please. No images.  We need to see the errors to help. That screen image didn't show the real error.

---

### Post by alfirdaous on 2013-09-05
here you go:

```

Fetched 18.3 MB in 4s (3,925 kB/s)
E: Write error - write (28: No space left on device)
E: Write error - write (28: No space left on device)
E: Prior errors apply to /var/cache/apt/archives/libframe6_2.2.4-0ubuntu0.12.04.1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libgnome2-bin_2.32.1-2ubuntu1.1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libgnome2-0_2.32.1-2ubuntu1.1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libgrail5_3.0.6-0ubuntu0.12.04.01_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libnm-util2_0.9.4.0-0ubuntu4.3_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libnm-glib4_0.9.4.0-0ubuntu4.3_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/network-manager_0.9.4.0-0ubuntu4.3_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/update-notifier_0.119ubuntu8.6_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/patch_2.6.1-3_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/update-notifier-common_0.119ubuntu8.6_all.deb
E: Prior errors apply to /var/cache/apt/archives/libgeis1_2.2.9.2-0ubuntu1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/gir1.2-networkmanager-1.0_0.9.4.0-0ubuntu4.3_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/printer-driver-hpijs_3.12.2-1ubuntu3.1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libsane-hpaio_3.12.2-1ubuntu3.1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/hplip_3.12.2-1ubuntu3.1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libhpmud0_3.12.2-1ubuntu3.1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/hplip-data_3.12.2-1ubuntu3.1_all.deb
E: Prior errors apply to /var/cache/apt/archives/printer-driver-hpcups_3.12.2-1ubuntu3.1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/php5-cli_5.3.10-1ubuntu3.8_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/php5-xsl_5.3.10-1ubuntu3.8_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/php5-mysql_5.3.10-1ubuntu3.8_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/php5-gd_5.3.10-1ubuntu3.8_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/php5-curl_5.3.10-1ubuntu3.8_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libapache2-mod-php5_5.3.10-1ubuntu3.8_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/php5-common_5.3.10-1ubuntu3.8_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libgrip0_0.3.5-0ubuntu1~12.04.1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libnm-glib-vpn1_0.9.4.0-0ubuntu4.3_amd64.deb

```

```

Errors were encountered while processing:
 apparmor
[ Rootkit Hunter version 1.3.8 ]
File updated: searched for 165 files, found 133
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

disk space:

```

# df -h
Filesystem      Size  Used Avail Use% Mounted on
rootfs           20G  6.9G   12G  38% /
/dev/root        20G  6.9G   12G  38% /
devtmpfs        993M  4.0K  993M   1% /dev
none            199M  2.7M  196M   2% /run
none            5.0M     0  5.0M   0% /run/lock
none            994M  4.0K  994M   1% /run/shm
overflow        1.0M 1020K  4.0K 100% /tmp
/dev/sda2       894G  801G   48G  95% /home

```

---

### Post by TheFu on 2013-09-05
How about 
**df -i**

I bet you are out of [inodes]("https://en.wikipedia.org/wiki/Inode"). 
It is likely that old kernels have been sucking the storage and inodes.
[http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt](http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt) has a script to create a command to clean them up.  This might be enough to make the system useable again, perhaps not. There is no way to know until you try.

---

### Post by alfirdaous on 2013-09-05
here you are:

```

# df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
rootfs          1281120 204255  1076865   16% /
/dev/root       1281120 204255  1076865   16% /
devtmpfs         254127   1460   252667    1% /dev
none             254231    876   253355    1% /run
none             254231      5   254226    1% /run/lock
none             254231      3   254228    1% /run/shm
overflow         254231    119   254112    1% /tmp
/dev/sda2      59514880 306561 59208319    1% /home

```

and then:

```

./kernel-cleanup.sh
INFO: New Kernel installed - reboot needed before cleanup attempts.
*** System restart required ***


# reboot

```

after that:

```

./kernel-cleanup.sh 

INFO: Current kernel is: linux-image-3.8.13-xxxx-std-ipv6-64

INFO: Kernel cleanup not necessary.
INFO: 0 kernels have been retained in addition to the currently used kernel.

```

update:

```

# apt-get update && apt-get -y upgrade

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up apparmor (2.7.102-0ubuntu3.9) ...
[ Rootkit Hunter version 1.3.8 ]
File updated: searched for 165 files, found 133


```

no error shown.

Strange thing that the reboot was not shown while login in, shall I add the clean up script to the weekly cron?

---

### Post by TheFu on 2013-09-05
Are you running these commands from a liveCD boot?

I'd expect / to be mounted on /dev/sda1 or something like that. If you use LVM, then there would be a /dev/mapper/something.  
What's with the rootfs stuff?

---

### Post by alfirdaous on 2013-09-05
> Are you running these commands from a liveCD boot?
No I am on an Ubuntu Desktop

>  I'd expect / to be mounted on /dev/sda1 or something like that. If you use LVM, then there would be a /dev/mapper/something.  

```

/dev/mapper$ ls
control

```

> What's with the rootfs stuff?

rootfs is it the /var location?

---

### Post by TheFu on 2013-09-06
> **alfirdaous said:**
> rootfs is it the /var location?

Your disks don't look normal to me.  Is this a WUBI install?

Here's what I expected (mix of regular and software RAID):
```

$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             19501440   5842880  13658560  30% /
/dev/sda6            257481536  85694200 158708020  36% /export
/dev/sde3            604756628 446964492 127072244  78% /Backups
/dev/md1             1912523780 1524075628 291297612  84% /raid
```

Or on an LVM box:```

$ df
Filesystem              1K-blocks      Used Available Use% Mounted on
/dev/mapper/qbe-root     11800496   2457156   8743892  22% /
udev                      4046136        12   4046124   1% /dev
tmpfs                     1622092       780   1621312   1% /run
none                         5120         0      5120   0% /run/lock
none                      4055220         0   4055220   0% /run/shm
cgroup                    4055220         0   4055220   0% /sys/fs/cgroup
/dev/sda1                  233191     50753    169997  23% /boot
/dev/mapper/qbe-export  165139820 149226616   7525364  96% /export
/dev/mapper/qbe-backups 154818540    202668 146751552   1% /backups
```


Or on a virtual machine:
```
$ df
Filesystem       1K-blocks      Used Available Use% Mounted on
/dev/vda1         13912144  11683052   1522380  89% /
udev                757168         4    757164   1% /dev
tmpfs               306256       360    305896   1% /run
none                  5120         0      5120   0% /run/lock
none                765640        76    765564   1% /run/shm
cgroup              765640         0    765640   0% /sys/fs/cgroup

```

I have no idea what a **rootfs** is.  Google implies that it has something to do with an encrypted file system + LVM setup, but I have no idea if that is true. Sorry, I can't help.

---

### Post by alfirdaous on 2013-09-06
Thanks [**[COLOR=#000000]TheFu[/COLOR]**]("http://ubuntuforums.org/member.php?u=1037685"), it is a desktop server, there is no RAID, and not WUBI, basic install on a computer

---

