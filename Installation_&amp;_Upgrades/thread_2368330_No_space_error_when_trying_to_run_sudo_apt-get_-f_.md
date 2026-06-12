---
title: "No space error when trying to run sudo apt-get -f install"
date: 2017-08-09
forum: Installation &amp; Upgrades
---

### Post by johan855 on 2017-08-09
Hi,

I'm trying to update my ubuntu server, however, I am getting a no space available error while trying to run sudo apt-get -f install.

I see the issue is regarding the inodes, since:

```
df -h
```

Outputs:

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/root       7.8G  4.9G  2.5G  67% /
devtmpfs        494M     0  494M   0% /dev
tmpfs           496M  4.0K  496M   1% /dev/shm
tmpfs           496M  6.9M  489M   2% /run
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           496M     0  496M   0% /sys/fs/cgroup
tmpfs           100M     0  100M   0% /run/user/1001
/dev/xvdf       7.8G  153M  7.2G   3% /database

```

and

```
df -i

```
Outputs:

```
Filesystem     Inodes  IUsed  IFree IUse% Mounted on
/dev/root      524288 516118   8170   99% /
devtmpfs       126368    365 126003    1% /dev
tmpfs          126787      2 126785    1% /dev/shm
tmpfs          126787    485 126302    1% /run
tmpfs          126787      3 126784    1% /run/lock
tmpfs          126787     16 126771    1% /sys/fs/cgroup
tmpfs          126793      4 126789    1% /run/user/1001
/dev/xvdf      524288   1645 522643    1% /database

```

I'm trying to cleanup any old kernels by running:

```
sudp apt-get autoremove
```

but the Output is as follows:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-4.4.0-89-generic : Depends: linux-headers-4.4.0-89 but it is not installed
E: Unmet dependencies. Try using -f.



```

So I ran:
```

sudo apt-get -f install
```

but the output is:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-53 linux-headers-4.4.0-53-generic linux-headers-4.4.0-57 linux-headers-4.4.0-57-generic linux-headers-4.4.0-59 linux-headers-4.4.0-59-generic linux-headers-4.4.0-62 linux-headers-4.4.0-62-generic
  linux-headers-4.4.0-63 linux-headers-4.4.0-63-generic linux-headers-4.4.0-64 linux-headers-4.4.0-64-generic linux-headers-4.4.0-66 linux-headers-4.4.0-66-generic linux-headers-4.4.0-70 linux-headers-4.4.0-70-generic
  linux-headers-4.4.0-71 linux-headers-4.4.0-71-generic linux-headers-4.4.0-72 linux-headers-4.4.0-72-generic linux-headers-4.4.0-75 linux-headers-4.4.0-75-generic linux-headers-4.4.0-78 linux-headers-4.4.0-78-generic
  linux-headers-4.4.0-79 linux-headers-4.4.0-79-generic linux-headers-4.4.0-81 linux-headers-4.4.0-81-generic linux-headers-4.4.0-83 linux-headers-4.4.0-83-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-headers-4.4.0-89
The following NEW packages will be installed:
  linux-headers-4.4.0-89
0 upgraded, 1 newly installed, 0 to remove and 85 not upgraded.
6 not fully installed or removed.
Need to get 0 B/9,919 kB of archives.
After this operation, 70.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 467324 files and directories currently installed.)
Preparing to unpack .../linux-headers-4.4.0-89_4.4.0-89.112_all.deb ...
Unpacking linux-headers-4.4.0-89 (4.4.0-89.112) ...
dpkg: error processing archive /var/cache/apt/archives/linux-headers-4.4.0-89_4.4.0-89.112_all.deb (--unpack):
 unable to create '/usr/src/linux-headers-4.4.0-89/arch/frv/include/asm/device.h.dpkg-new' (while processing './usr/src/linux-headers-4.4.0-89/arch/frv/include/asm/device.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-4.4.0-89_4.4.0-89.112_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

So I feel I cannot remove old files which are taking up all of the space in my /usr/src/ folder because I have not enough space to fully unpack linux-headers-4.4.0-89_4.4.0-89?

Additional infor regarding the current kernel:

```
dpkg -l | grep linux-image
```

Output:
```

ii  linux-image-4.4.0-87-generic     4.4.0-87.110                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-89-generic     4.4.0-89.112                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-virtual              4.4.0.89.95                                amd64        This package will always depend on the latest minimal generic kernel image.



```

```
uname -r
```

Output:

```
4.4.0-89-generic

```

---

### Post by vocx on 2017-08-09
> **johan855 said:**
> ...

```
df -i

```
Outputs:

```
Filesystem     Inodes  IUsed  IFree IUse% Mounted on
/dev/root      524288 516118   8170   99% /
devtmpfs       126368    365 126003    1% /dev
tmpfs          126787      2 126785    1% /dev/shm
tmpfs          126787    485 126302    1% /run
tmpfs          126787      3 126784    1% /run/lock
tmpfs          126787     16 126771    1% /sys/fs/cgroup
tmpfs          126793      4 126789    1% /run/user/1001
/dev/xvdf      524288   1645 522643    1% /database

```

According to this question [https://unix.stackexchange.com/questions/117093/find-where-inodes-are-being-used](https://unix.stackexchange.com/questions/117093/find-where-inodes-are-being-used)
an "inode" is a file. Therefore, if you are running out of inodes, but you still have plenty of space, it means you have many many little files.

They suggest a find command to traverse your system, counting the number of files in that directory. The directory with the largest number of files is at the bottom. Then you can see which directories are producing all these small files. Sounds like it could be a logging program creating small logs somewhere in "/var".
```

find / -xdev - printf '%h\n' | sort | uniq -c | sort -k 1 -n

```

> 
```
Reading package lists... Done
dpkg: error processing archive **/var/cache/apt/archives/**linux-headers-4.4.0-89_4.4.0-89.112_all.deb (--unpack):
 unable to create '/usr/src/linux-headers-4.4.0-89/arch/frv/include/asm/device.h.dpkg-new' (while processing './usr/src/linux-headers-4.4.0-89/arch/frv/include/asm/device.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
** /var/cache/apt/archives/**linux-headers-4.4.0-89_4.4.0-89.112_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Removing things with "autoremove" is fine.

And since you basically have no space left, I would also run "clean".
```

sudo apt clean

```
This deletes all the packages that were downloaded whenever you install updates. It's basically equivalent to a "rm" command.
```

sudo rm /var/cache/apt/archives/*

```

---

### Post by ajgreeny on 2017-08-09
As you are running short of inodes in the root partition I suspect that the linux-header packages are behind this problem as they each add many hundreds of separate files to the system, and you have at least 13 surplus versions each with two packages.

Try removing some of the now old and unneeded versions of linux-headers with 
```
sudo dpkg -P linux-headers-4.4.0-{53,57,59,62,63,64,66,70,71,72,75,78,79}{,-generic}
``` which should remove most of those packages.  Once that has done its magic then run ```
sudo apt-get autoremove --purge
``` to double check everything is as it should be.

Using dpkg instead of apt or apt-get usually works in this situation as dpkg does not require as much headroom as apt.  Your major problem, however, is the small 7.8GB  size you chose for the root partition at install.

I realise that you do not have a huge amount of total space available, but if that is not possible to resolve, you may need to think about using a distro that needs less disk space, eg Xubuntu-core or Lubuntu-core.  You must, however, make sure that you regularly housekeep to remove those unwanted packages with the autoremove command as above.

---

