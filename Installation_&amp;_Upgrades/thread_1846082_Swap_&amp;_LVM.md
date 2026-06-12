---
title: "Swap &amp; LVM"
date: 2011-09-18
forum: Installation &amp; Upgrades
---

### Post by mcc28x on 2011-09-18
Hi,

I am running Ubuntu 11.04 Server edition and used LVM to partition the disk. I noticed that my swap is not mounted.

[COLOR="Red"]The output of mount -l is:[/COLOR]

[I]/dev/mapper/hs-root on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/mapper/hs-tmp on /tmp type ext4 (rw,commit=0)
/dev/sda1 on /boot type ext4 (rw,commit=0)
/dev/mapper/hs-home on /home type ext4 (rw,commit=0)
/dev/mapper/hs-srv on /srv type ext4 (rw,commit=0)
/dev/mapper/hs-var on /var type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/mark/.Private on /home/mark type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=a278bf3ca53b0dcf,ecryptfs_fnek_sig=7faeb3841b44b256)
gvfs-fuse-daemon on /home/mark/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mark)[/I]


[COLOR="Red"]And swapon -va produces:[/COLOR]
[I]swapon on /dev/mapper/hs-swap
swapon: /dev/mapper/hs-swap: found swap signature: version 1, page-size 4, same byte order
swapon: /dev/mapper/hs-swap: pagesize=4096, swapsize=1996488704, devsize=1996488704
swapon: /dev/mapper/hs-swap: swapon failed: Device or resource busy
swapon on /dev/mapper/cryptswap1
swapon: /dev/mapper/cryptswap1: stat failed: No such file or directory[/I]

[COLOR="Red"]My /etc/fstab looks like this:
[/COLOR]
[I]# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/hs-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=1f67edb3-725a-4a18-8037-2a26bff58ce5 /boot           ext4    defaults        0       2
/dev/mapper/hs-home /home           ext4    defaults        0       2
/dev/mapper/hs-srv /srv            ext4    defaults        0       2
/dev/mapper/hs-tmp /tmp            ext4    defaults        0       2
/dev/mapper/hs-var /var            ext4    defaults        0       2
/dev/mapper/hs-swap none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
[/I]

[COLOR="Red"]and cat /proc/swaps [/COLOR]produces this:
[I]Filename				Type		Size	Used	Priority
/dev/dm-3                               partition	1949692	0	-1

[/I]

Can anyone tell me what to do to get my swap mounted properly?

Thanks

Mark

---

### Post by srs5694 on 2011-09-18
Swap space is not mounted -- at least, not in the same way that filesystems are mounted. Swap space does usually get listed in /etc/fstab, though, and your /etc/fstab file does contain a swap entry. There are several commands that can provide information on swap usage. The first is free:

```

$ **free -m**
             total       used       free     shared    buffers     cached
Mem:          7743       7491        252          0        191       4677
-/+ buffers/cache:       2623       5120
Swap:         6143         74       6069
```

This example shows swap space availability and use in the final column -- 6143 MiB of swap space is available, 74 MiB is used, and 6069 MiB is available.

The second command is swapon, and in particular its -s option:

```
$ **swapon -s**
Filename                Type        Size    Used    Priority
/dev/mapper/nessus-swap                 partition    6291452    76296    -1

```

This example shows that /dev/mapper/nessus-swap is a swap "partition" (it's actually a logical volume), with size and use information.

Given the information that you posted, I think your swap space is probably being used; however, you can check with these commands to verify this.

BTW, when posting the output of text-mode commands, it's generally best to enclose them between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags. This preserves the text-mode formatting, which is particularly important on commands that produce columnar output (like my "free -m" example). Without these tags, the forum software compresses multiple spaces down to one space, which can make it almost impossible to discern what's supposed to be in particular columns.

---

### Post by mcc28x on 2011-09-20
Thank you for your reply - my swap is working fine...


thankyou

---

