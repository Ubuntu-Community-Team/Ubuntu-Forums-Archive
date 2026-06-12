---
title: "linux-headers-3.2.0-37-generic-pae fails to update"
date: 2013-02-04
forum: Installation &amp; Upgrades
---

### Post by blumf on 2013-02-04
12.04 32-bit

Problem upgrading...


sudo apt-get update

then

sudo apt-get upgrade
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-37-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.
```

So..

sudo apt-get -f upgrade
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following NEW packages will be installed
  linux-headers-3.2.0-37 linux-headers-3.2.0-37-generic-pae
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/12.7 MB of archives.
After this operation, 67.5 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 481804 files and directories currently installed.)
Unpacking linux-headers-3.2.0-37 (from .../linux-headers-3.2.0-37_3.2.0-37.58_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-37_3.2.0-37.58_all.deb (--unpack):
 error creating directory `./usr/src/linux-headers-3.2.0-37/arch/m32r/platforms/opsput': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking linux-headers-3.2.0-37-generic-pae (from .../linux-headers-3.2.0-37-generic-pae_3.2.0-37.58_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-37-generic-pae_3.2.0-37.58_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-37-generic-pae/include/config/hisax/sct/quadro.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-37-generic-pae/include/config/hisax/sct/quadro.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-37_3.2.0-37.58_all.deb
 /var/cache/apt/archives/linux-headers-3.2.0-37-generic-pae_3.2.0-37.58_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Well, that's not right, there's over a gig of space on root so that disk full error is bogus. Is it a corrupted package?

---

### Post by turbocon on 2013-02-05
I have the exact same issue down to the amount of memory I have left. You wouldn't happen to have a cr-48 would you?

---

### Post by blumf on 2013-02-05
No, it's some Acer Revo thing (using it for XBMC)

FWIW...

df -h
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       7.6G  6.0G  1.2G  84% /
udev           1000M  4.0K 1000M   1% /dev
tmpfs           403M  872K  402M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1007M  124K 1007M   1% /run/shm
/dev/sda6       450G  1.2G  426G   1% /home
```

No shortage of disk space

---

### Post by blumf on 2013-02-05
Ah! This is interesting...

df -i
```
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda1        499968 495894     4074  100% /
udev             215767    517   215250    1% /dev
tmpfs            219415    441   218974    1% /run
none             219415      3   219412    1% /run/lock
none             219415      5   219410    1% /run/shm
/dev/sda6      29900800  11944 29888856    1% /home
```

This might be the cause of the disk full message, a shortage of inodes.

Might have to mess about with the partitions :(

---

### Post by blumf on 2013-02-05
Okay. Using

```
sudo find . -xdev -type f | cut -d "/" -f 2 | sort | uniq -c | sort -n
```

I identified some directories that had a lot of inodes and were unused.
```
sudo rm -r /usr/src/linux-headers-3.2.0-2*
```
(probably a better way of doing this via apt-get or dpkg, they were from old kernel packages)

This cleared enough inode space for apt-get to install the problem packages.

Now:

df -i
```
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda1        499968 384534   115434   77% /
udev             215767    517   215250    1% /dev
tmpfs            219415    441   218974    1% /run
none             219415      3   219412    1% /run/lock
none             219415      5   219410    1% /run/shm
/dev/sda6      29900800  11944 29888856    1% /home
```

Will probably reinstall the system with ReiserFS or something else with dynamic inode allocation later.

---

