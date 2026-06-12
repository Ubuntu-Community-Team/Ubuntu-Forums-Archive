---
title: "UBuntu upgrade fails - No space left on device - encrypted installation"
date: 2017-01-06
forum: Installation &amp; Upgrades
---

### Post by nicolasdiogo on 2017-01-06
]Hello


unfortunately, i have a really annoying case of bad upgrade on my laptop 15.04 (i think)

I tried upgrading to the latest version 16.10 (?)


and i have the dreaded result of:

```

dpkg --configure -a
dpkg: error: unable to open/create status database lockfile: No space left on device

```


I am not keen on rebooting yet, since I am not sure if I will be able to restart it afterwards.
However, it would be great to have some assistance .. soonish?!



while trying to understand the situation i have:


tried to remount the partitions with no success with: ```
mount -a
```

and checked the storage too, but i can not find the reason for the ROOT to be 'disappeared'

```

df -i
Filesystem                              Inodes IUsed   IFree IUse% Mounted on
udev                                   4107709   695 4107014    1% /dev
tmpfs                                  4112511  1133 4111378    1% /run
/dev/mapper/vg_dsk_00-lv_root_00_crypt       0     0       0     - /
tmpfs                                  4112511    23 4112488    1% /dev/shm
tmpfs                                  4112511     7 4112504    1% /run/lock
tmpfs                                  4112511    17 4112494    1% /sys/fs/cgroup
/dev/nvme0n1p6                           61056   313   60743    1% /boot
/dev/nvme0n1p2                               0     0       0     - /boot/efi
/dev/sda2                                    0     0       0     - /opt/mnt01
/dev/mapper/vg_dsk_00-lv_root_00_crypt       0     0       0     - /home
cgmfs                                  4112511    13 4112498    1% /run/cgmanager/fs
tmpfs                                  4112511    37 4112474    1% /run/user/1000
/home/theuser/.Private                       0     0       0     - /home/theuser

```



```

df -h
Filesystem                              Size  Used Avail Use% Mounted on
udev                                     16G     0   16G   0% /dev
tmpfs                                   3.2G  1.9M  3.2G   1% /run
/dev/mapper/vg_dsk_00-lv_root_00_crypt  224G  192G   31G  87% /
tmpfs                                    16G  1.5M   16G   1% /dev/shm
tmpfs                                   5.0M  4.0K  5.0M   1% /run/lock
tmpfs                                    16G     0   16G   0% /sys/fs/cgroup
/dev/nvme0n1p6                          922M  207M  668M  24% /boot
/dev/nvme0n1p2                          256M   30M  227M  12% /boot/efi
/dev/sda2                               368G  355G   12G  97% /opt/mnt01
/dev/mapper/vg_dsk_00-lv_root_00_crypt  224G  192G   31G  87% /home
cgmfs                                   100K     0  100K   0% /run/cgmanager/fs
tmpfs                                   3.2G   76K  3.2G   1% /run/user/1000
/home/theuser/.Private                    224G  192G   31G  87% /home/theuser

```


dmesg:
```

[605921.317628] ecryptfs_do_create: Failure to create dentry in lower fs; rc = [-28]
[605921.317630] ecryptfs_create: Failed to create file inlower filesystem
[605921.355468] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-28]
[605921.355471] ecryptfs_write: Error encrypting page; rc = [-28]
[605921.355472] Error attempting to zero out the remainder of the end page on reducing truncate; rc = [-28]
[605921.407575] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-28]
[605921.407578] ecryptfs_write_end: Error encrypting page (upper index [0x0000000000000029])
[605921.452884] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-28]
[605921.452887] ecryptfs_write_end: Error encrypting page (upper index [0x0000000000000029])
[605921.521542] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-28]
[605921.521554] ecryptfs_write_end: Error encrypting page (upper index [0x0000000000000029])
[605921.647531] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-28]
[605921.647533] ecryptfs_write_end: Error encrypting page (upper index [0x0000000000000002])
[605921.742106] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-28]
[605921.742109] ecryptfs_write_end: Error encrypting page (upper index [0x000000000000000b])
[605921.830778] ecryptfs_do_create: Failure to create dentry in lower fs; rc = [-28]
[605921.830780] ecryptfs_create: Failed to create file inlower filesystem
[605921.953820] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-28]
[605921.953822] ecryptfs_write_end: Error encrypting page (upper index [0x000000000000002e])
[605921.979266] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-28]
[605921.979274] ecryptfs_write_end: Error encrypting page (upper index [0x000000000000002e])
[605922.006229] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-28]
[605922.006238] ecryptfs_writepage: Error encrypting page (upper index [0x0000000000000000])
[605922.145937] ecryptfs_do_create: Failure to create dentry in lower fs; rc = [-28]
[605922.145939] ecryptfs_create: Failed to create file inlower filesystem
[605922.252553] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-28]
[605922.252556] ecryptfs_write_end: Error encrypting page (upper index [0x0000000000000099])

```


please let me know what else i can do to clarify this problem.

thanks,
nicolas

---

### Post by ajgreeny on 2017-01-06
Did you try to make that upgrade in a single operation?

If so, I am not surprised that it failed as you can upgrade only from one version to the next, eg 16.04 to 16.10, or from one LTS version to the next LTS version, eg 14.04 to 16.04.

The command to remount all partitions of your system, actually only those in the fstab file, needs to be run as root so is **sudo mount -a**; you appear to have tried it as user, not root.

I also note you are using encryption or LVM about which I know almost nothing so can not help in any way with that.

---

### Post by nicolasdiogo on 2017-01-06
> **ajgreeny said:**
> Did you try ....


I did try the commands as root using **sudo -i** first


If the upgrades are not supposed to be done between versions, one should expect at least a warning reminding the user of the eminent Mess that they are letting themselves into ....


Unfortunately, it seems that I have to bit the bullet, and reboot !

Wish me luck!


Thanks,

---

### Post by ajgreeny on 2017-01-06
How did you do the upgrade; using command line or a GUI application such as synaptic or software-centre?

Perhaps you simply manually edited the software sources file **/etc/apt/sources.list**?

---

### Post by nicolasdiogo on 2017-01-07
> **ajgreeny said:**
> How did you do the upgrade ...

I have followed the path provided by Ubuntu.
Started the app that does upgrades (GUI), and click next all the way.

Effectively, it suggested for me to upgrade to the latest version available.


It seems that Ubuntu is very good in installing on an 'encrypted' drive - but the process of upgrade is not quite so smooth.
The 'encrypted' root was unmounted midway through the process.

After rebooting, and choosing the previous kernel (not the latest that failed to install), it completed all the process of 'recovering' by:
```

dpkg --configure -a

```


After a few more, commands to remove the unnecessary packages and installing missing ones and everything is up and running:
```

apt-get --purge autoremove
apt-get -f install

```


I might even try to use Unity again - instead of my gnome3.


Thanks for reaching out.  It would be good to have a bit more testing for users that installed their laptops on an encrypted disk and missed a release.


Kind Regards,

Nicolas

---

### Post by ian-weisser on 2017-01-07
> **nicolasdiogo said:**
> It seems that Ubuntu is very good in installing on an 'encrypted' drive - but the process of upgrade is not quite so smooth.
You, the hardware user, are responsible for upgrading your system in a timely manner.
That's a minimum requirement of any Linux distro.
You didn't do that, and the problem you encountered is your consequence.

Unless you silenced the notifications, your system warned you repeatedly when Ubuntu 15.10 was available for a safe, reliable upgrade...until 15.10 hit EOL in June 2016.
It's not Ubuntu's fault (nor this community, which includes many testers and volunteers that make Ubuntu great) that you ignored those notifications.

Since your system has received no security upgrades in over a year, and has been vulnerable to known, published exploits for over a year, I suggest that a complete wipe-and-reinstall more appropriate than an upgrade. If your system is compromised, any new backdoors may survive an upgrade.

---

