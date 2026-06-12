---
title: "[SOLVED] Problem with interrupted kernel update"
date: 2007-06-25
forum: Installation &amp; Upgrades
---

### Post by mneisen on 2007-06-25
Hi,

I'm running Feisty and just tried to upgrade a remote machine to the current kernel. Unfortunately, the network connection broke down during upgrade. Upon reconnect, I tried

```
sudo apt-get dist-upgrade
```

again, but got the following message:

```
mneisen@farm2:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  linux-image-generic: Depends: linux-image-2.6.20-16-generic but it is not installed
  linux-restricted-modules-2.6.20-16-generic: Depends: linux-image-2.6.20-16-generic but it is not installed
E: Unmet dependencies. Try using -f.
```

The suggested command yields:
```
mneisen@farm2:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-2.6.20-16-generic
Suggested packages:
  linux-doc-2.6.20 linux-source-2.6.20
The following NEW packages will be installed:
  linux-image-2.6.20-16-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/23.8MB of archives.
After unpacking 71.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 91277 files and directories currently installed.)
Unpacking linux-image-2.6.20-16-generic (from .../linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb (--unpack):
 unable to create `./boot/vmlinuz-2.6.20-16-generic': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead!

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.20-15-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

And even a direct "attack" :D via dpkg is to no avail:
```
mneisen@farm2:~$ sudo dpkg -i /var/cache/apt/archives/linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb
(Reading database ... 91277 files and directories currently installed.)
Unpacking linux-image-2.6.20-16-generic (from .../linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb (--install):
 unable to create `./boot/vmlinuz-2.6.20-16-generic': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead!

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.20-15-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb
```

What is especially odd about all this is the line stating that there is no space left on the device:
```
unable to create `./boot/vmlinuz-2.6.20-16-generic': No space left on device
```

I have two partitions:
[LIST]
[*]/boot with more than 100M of free space
[*]/ with more than 150G (!) of free space
[/LIST]

So I cannot really see where there is too little space to unpack and/or install kernel-related files.

Has anybody any help?! I'd really appreciate!

Thanks in advance!

Kind regards
Martin Eisenhardt

---

### Post by Sp4rKy on 2007-06-25
if it sais there is no space left ... there is no space left :)
Can you do a du --max-depth=0 -h /boot , a df -h and a sudo fdisk -l ?

---

### Post by mneisen on 2007-06-25
Hi Sp4rky,

> **Sp4rKy said:**
> if it sais there is no space left ... there is no space left :)
Can you do a du --max-depth=0 -h /boot , a df -h and a sudo fdisk -l ?

no problem:

```
mneisen@farm2:~$ sudo du --max-depth=0 -h /boot
11M     /boot
```

```
mneisen@farm2:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md1              147G  2.0G  145G   2% /
varrun                506M  104K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  108K  506M   1% /proc/bus/usb
udev                  506M  108K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
/dev/md0              126M   16M  109M  13% /boot
```

The "sudo fdisk -l" is a bit tricky since it is a RAID setup, but anyway:

```
mneisen@farm2:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          16      128488+  fd  Linux raid autodetect
/dev/sda2              17         138      979965   82  Linux swap / Solaris
/dev/sda3             139        9729    77039707+  fd  Linux raid autodetect

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          16      128488+  fd  Linux raid autodetect
/dev/sdb2              17         138      979965   82  Linux swap / Solaris
/dev/sdb3             139        9729    77039707+  fd  Linux raid autodetect

Disk /dev/md0: 131 MB, 131465216 bytes
2 heads, 4 sectors/track, 32096 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 157.7 GB, 157777133568 bytes
2 heads, 4 sectors/track, 38519808 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md1 doesn't contain a valid partition table
```

In my view, it is OK for md0 and md1 to have no partition tables since they *are* the partitions for /boot and /, respectively.

I am looking forward to your suggestions!

Kind regards
Martin Eisenhardt

---

### Post by Sp4rKy on 2007-06-25
i'm not expert with raid ...
anyway , i guess dpkg get a bad view of your system ...
can you try a dd if=/dev/zero of=/boot/file , wait it stops (with error), and check the size of this file ...

---

### Post by mneisen on 2007-06-25
Hi Sp4rKy,

> **Sp4rKy said:**
> i'm not expert with raid ...
anyway , i guess dpkg get a bad view of your system ...
can you try a dd if=/dev/zero of=/boot/file , wait it stops (with error), and check the size of this file ...

again, no problem with that :D :
```
mneisen@farm2:~$ sudo dd if=/dev/zero of=/boot/file
dd: writing to `/boot/file': No space left on device
224489+0 records in
224488+0 records out
114937856 bytes (115 MB) copied, 4.31681 seconds, 26.6 MB/s
```

and

```
mneisen@farm2:~$ ls -lisav /boot/file
32 112360 -rw-r--r-- 1 root root 114937856 2007-06-25 23:03 /boot/file
```

Sadly, the free space on that device matches what df reports, and it should be enough for the kernel.

Thanks for your help so far; do you have further suggestions?

Kind regards
Martin Eisenhardt

---

### Post by Sp4rKy on 2007-06-26
grrr, so there is really 115Mo , and the kernel package shouldn't take more ...

---

### Post by mneisen on 2007-06-26
> **Sp4rKy said:**
> grrr, so there is really 115Mo , and the kernel package shouldn't take more ...

Yes, that's what really strange. I could perfectly understand the afore-mentioned problems if at least one of the partitions was really maxed out. But as it seems there is enough space.

So, does anybody has an idea how to fix this?! Any mythical dpkg incantations or other rites? :-D

Kind regards
Martin

---

### Post by mneisen on 2007-06-26
Hi all,

thanks for the suggestions how to solve my problem. Alas, they all failed - and did so rightly for one very important reason:

```

mneisen@farm2:/$ sudo e2fsck /dev/md0
e2fsck 1.40-WIP (14-Nov-2006)
boot: clean, 32/32 files, 4109/32096 blocks

```

Yep, there were only 32 inodes on the partition, which is not enough to install more than one kernel on it. 

What strikes me as especially odd is the fact that I installed this system with the vanilla "Alternate Install CD" for Feisty. I have three systems with identical hardware, and this problem is imminent on two of them (I checked) but not on the third one.

More oddness than I like ... :-P

Kind regards
Martin

---

### Post by az on 2007-06-26
> **mneisen said:**
> 
Yep, there were only 32 inodes on the partition, which is not enough to install more than one kernel on it. 

What strikes me as especially odd is the fact that I installed this system with the vanilla "Alternate Install CD" for Feisty. I have three systems with identical hardware, and this problem is imminent on two of them (I checked) but not on the third one.

More oddness than I like ... :-P

Kind regards
Martin

Please file a bug report.

---

### Post by mneisen on 2007-06-26
> **az said:**
> Please file a bug report.

For what package/project?

---

### Post by az on 2007-06-26
Partman.

The installer packages are udebs, which mean they don't appear with the other packages in the archive and they do not have things like manpages and documentation since they are meant to be small.  It's a real pain to figure out which package to file a bug report against.

However, the new launchpad bug reporting interface helps a bit:

There are no matching bugs to "partman creates boot partition with only 32 inodes"

---

