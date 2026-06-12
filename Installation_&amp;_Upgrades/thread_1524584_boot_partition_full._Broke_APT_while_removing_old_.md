---
title: "/boot partition full. Broke APT while removing old kernel!"
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by gansvv on 2010-07-05
Hi, My Ubuntu 8.04 server has ~37MB in a /boot partition. The partition got full during a recent update (df showed 100% usage in /boot) and I got this error.
```

dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-28-server_2.6.24-28.70_amd64.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./boot/vmlinuz-2.6.24-28-server': No space left on device

```

So, to remove some space from /boot I moved the *.bak files from /boot to a backup folder in my /home. Then after checking my current kernel with 
```

$uname -r
2.6.24-27-server

``` 

I proceeded to remove the unused, old kernel with
```

sudo apt-get remove linux-image-2.6.24-23-server

```

Somehow, this process got terminated in between again due to lack of space in /boot. Now, I get this error for every APT action.
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  linux-image-server: Depends: linux-image-2.6.24-28-server but it is not going to be installed
  linux-ubuntu-modules-2.6.24-23-server: Depends: linux-image-2.6.24-23-server but it is not going to be installed
  linux-ubuntu-modules-2.6.24-28-server: Depends: linux-image-2.6.24-28-server but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

I tried sudo apt-get -f install to clear broken packages, but it hangs at this error.
```

Removing linux-ubuntu-modules-2.6.24-23-server ...
FATAL: Could not open '/boot/System.map-2.6.24-23-server': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-23-server
Cannot find /lib/modules/2.6.24-23-server
update-initramfs: failed for /boot/initrd.img-2.6.24-23-server
dpkg: error processing linux-ubuntu-modules-2.6.24-23-server (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-23-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

These are the contents of /boot partition.
```

total 37M
drwxr-xr-x  4 root root 1.0K 2010-07-05 13:50 ./
drwxr-xr-x 24 root root 4.0K 2010-07-04 22:04 ../
-rw-r--r--  1 root root 411K 2010-03-24 09:39 abi-2.6.24-27-server
-rw-r--r--  1 root root 411K 2010-05-26 22:10 abi-2.6.24-28-server
-rw-r--r--  1 root root  73K 2010-03-24 09:39 config-2.6.24-27-server
-rw-r--r--  1 root root  73K 2010-05-26 22:10 config-2.6.24-28-server
drwxr-xr-x  2 root root 1.0K 2010-07-04 22:07 grub/
-rw-r--r--  1 root root 7.2M 2010-07-04 22:52 initrd.img-2.6.24-23-server.bak
-rw-r--r--  1 root root 7.5M 2010-04-20 12:01 initrd.img-2.6.24-27-server
-rw-r--r--  1 root root 7.5M 2010-07-04 22:52 initrd.img-2.6.24-27-server.bak
-rw-r--r--  1 root root 7.5M 2010-07-04 22:04 initrd.img-2.6.24-28-server
drwxr-xr-x  2 root root  12K 2009-06-15 15:42 lost+found/
-rw-r--r--  1 root root 101K 2007-09-28 07:03 memtest86+.bin
-rw-r--r--  1 root root 1.2M 2010-03-24 09:39 System.map-2.6.24-27-server
-rw-r--r--  1 root root 1.2M 2010-05-26 22:10 System.map-2.6.24-28-server
-rw-r--r--  1 root root 1.9M 2010-03-24 09:39 vmlinuz-2.6.24-27-server
-rw-r--r--  1 root root 1.9M 2010-05-26 22:10 vmlinuz-2.6.24-28-server

```

Did the partial run of autoremove -delete the System.map-2.6.24-23-server and corrupt the whole process. How can I solve this and clear APT? Please help!

---

### Post by plucky on 2010-07-06
> Removing linux-ubuntu-modules-2.6.24-23-server ...
FATAL: Could not open '/boot/System.map-2.6.24-23-server': No such file or directory


Try adding the file back into the /boot menu with ```
sudo touch /boot/System.map-2.6.24-23-server
sudo apt-get install -f
``` and see if it gets past where the error occurred.

Good Luck

---

### Post by gansvv on 2010-07-06
haha. Thanks a ton! :KS

Just adding the file actually worked. ;)
It gave me 
```

WARNING: Couldn't open directory /lib/modules/2.6.24-23-server: No such file or directory
FATAL: Could not open /lib/modules/2.6.24-23-server/modules.dep.temp for writing: No such file or directory

```

So I also added that directory and the file inside it. And, it ran fine. 

This buys me some time till I figure out how to increase /boot space or move it altogether to another drive. I got gparted installed now.

Thanks again!

> **plucky said:**
> Try adding the file back into the /boot menu with ```
sudo touch /boot/System.map-2.6.24-23-server
sudo apt-get install -f
``` and see if it gets past where the error occurred.

Good Luck

---

