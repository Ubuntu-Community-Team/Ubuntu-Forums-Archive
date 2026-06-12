---
title: "Unable to install linux headers because no space left on device?"
date: 2017-12-26
forum: Installation &amp; Upgrades
---

### Post by jamesscott1983 on 2017-12-26
Updating Ubuntu 14.04 LTS on parents old computer and get "packages have unmet dependencies" error
```
roger@roger-ubuntu:~$ sudo apt-get install
[sudo] password for roger: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-headers-generic-lts-xenial : Depends: linux-headers-4.4.0-104-generic but it is not installed
E: Unmet dependencies. Try using -f.
```

but cannot install because "no space left on device"

```
roger@roger-ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  account-plugin-windows-live libgconf2-4 libllvm3.5 libntdb1 libupstart1
  linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
  linux-headers-4.4.0-34 linux-headers-4.4.0-34-generic linux-headers-4.4.0-78
  linux-headers-4.4.0-78-generic linux-image-3.16.0-30-generic
  linux-image-4.4.0-34-generic linux-image-4.4.0-78-generic
  linux-image-extra-3.16.0-30-generic linux-image-extra-4.4.0-34-generic
  linux-image-extra-4.4.0-78-generic python-ntdb
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-4.4.0-104-generic
The following NEW packages will be installed
  linux-headers-4.4.0-104-generic
0 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
2 not fully installed or removed.
Need to get 0 B/784 kB of archives.
After this operation, 15.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 1500908 files and directories currently installed.)
Preparing to unpack .../linux-headers-4.4.0-104-generic_4.4.0-104.127~14.04.1_amd64.deb ...
Unpacking linux-headers-4.4.0-104-generic (4.4.0-104.127~14.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/linux-headers-4.4.0-104-generic_4.4.0-104.127~14.04.1_amd64.deb (--unpack):
 unable to create `/usr/src/linux-headers-4.4.0-104-generic/include/config/blk/dev/rsxx.h.dpkg-new' (while processing `./usr/src/linux-headers-4.4.0-104-generic/include/config/blk/dev/rsxx.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-4.4.0-104-generic_4.4.0-104.127~14.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

and cannot auto-remove old linux headers because
```
roger@roger-ubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-headers-generic-lts-xenial : Depends: linux-headers-4.4.0-104-generic but it is not installed
```

There is still apparently 2.8GB free for /USR/SRC

Next steps?

---

### Post by Impavidus on 2017-12-26
There's a limit both for the total size of the files on your file system and for the number of files. The latter may be your problem. To check, run```
df -h
df -i
```

You may be able to use the lower-level dpkg tool to remove the old header packages.```
sudo dpkg -P linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
```That should make some room.

---

### Post by leunam12 on 2017-12-26
Did you already try ```
sudo apt-get -f install
``` as suggested?

---

### Post by jamesscott1983 on 2017-12-26
Yes!
The lower level dpkg tool is the sort of thing that I was hoping for I guess. and thats worked I believe!
We're now back on track and auto-removed all the old junk.
Thank you ever so much!

---

