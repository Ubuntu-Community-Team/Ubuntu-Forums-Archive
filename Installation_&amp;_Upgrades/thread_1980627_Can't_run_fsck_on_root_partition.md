---
title: "Can't run fsck on root partition"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by bingasedu on 2012-05-15
I'm running Ubuntu 10.04 LTS and yesterday my machine started booting up with the root partition marked as read only. I booted from the 10.04 LTS install DVD and tried to run fsck on /dev/sdb1, but I keep getting this result:
```

ubuntu@ubuntu:~$ sudo fsck -yv /dev/sdb1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sdb1
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$

```The only unusual event that's occurred recently is that I was working on an rsynch script last Friday, which kept hanging and needing to be killed. I wouldn't expect that to have caused this level of problem, though.

I ran gparted, which reported that it couldn't find a valid filesystem superblock for /dev/sdb1.

Here's my fdisk output in case it's helpful:
```

ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160000000000 bytes
256 heads, 63 sectors/track, 19376 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19377   156249999+  ee  GPT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e1cf8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      120853   970751691   83  Linux
/dev/sdb2          120854      121601     6008310    5  Extended
/dev/sdb5          120854      121601     6008278+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

```Thanks very much for any help.

---

### Post by darkod on 2012-05-15
Are you sure it's not mounted in any way? If you try to check with:
df -h

What does it say?

---

### Post by bingasedu on 2012-05-15
Yes, at least as sure as I can be. In fact I tried to mount it but the command hung indefinitely - probably because the device appears to be busy to the mount command just as it does to fsck. Here's the output of df -h:
```

ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                  1.5G   75M  1.4G   5% /
none                  1.5G  292K  1.5G   1% /dev
/dev/sr1              695M  695M     0 100% /cdrom
/dev/loop0            667M  667M     0 100% /rofs
none                  1.5G  116K  1.5G   1% /dev/shm
tmpfs                 1.5G   32K  1.5G   1% /tmp
none                  1.5G   88K  1.5G   1% /var/run
none                  1.5G  4.0K  1.5G   1% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
ubuntu@ubuntu:~$

```

---

### Post by darkod on 2012-05-15
But you didn't try the fsck after the mount command, did you? In that case it might have been busy and locked by the mount try.

Did you try booting in a new fresh live mode session and doing only fsck, no mount, nothing. You don't even need the options, just:
sudo fsck /dev/sdb1

---

### Post by bingasedu on 2012-05-15
> **darkod said:**
> But you didn't try the fsck after the mount command, did you? In that case it might have been busy and locked by the mount try.
I tried the fsck first, and also tried it after attempting the mount.

> **darkod said:**
> Did you try booting in a new fresh live mode session and doing only fsck, no mount, nothing. You don't even need the options, just:
sudo fsck /dev/sdb1
I have done this several times - boot with the install DVD and run sudo fsck -yv /dev/sdb1 without doing anythig else. I don't believe I ever tried it with the options, but surely the options wouldn't cause a busy error.

The disk isn't mounted. There's something else going on here.

I just stumbled across a seemingly relevant discussion which claimed that the versions of fsck on the 10.XX live DVDs sometimes have problems, and that the 9.10 live DVD works more reliably when trying to repair 10.xx file systems. I just booted from the 9.10 live DVD and surprisingly fsck ran without complaint, and seems to have fixed the errors. I'm going to reboot and see what happens.

---

### Post by darkod on 2012-05-15
Cool.

---

### Post by bingasedu on 2012-05-15
I'll wait a day or two before claiming victory, but all signs are good at this point. My root partition is no longer read only, and various strange behaviors I observed (undoubtedly due to root being read only), have disappeared.

It seems odd that the 9.10 fsck would work where the 10.04 and 10.10 fsck versions fail. I just hope I can remember this the next time I need it!

Thanks for your help.

---

