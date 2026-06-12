---
title: "Can't update, or remove packages because partition is full"
date: 2013-03-09
forum: Installation &amp; Upgrades
---

### Post by GregoryMA on 2013-03-09
Hi, 

I have had a problem since (I think) 12.10 came out. The old kernels never get deleted automatically. So, the partition they are on is constantly filling up. Then I have to go in an manually delete them. I guess I wasn't on the ball enough because now the partition is full. This is creating huge problems for me because some dependancies are broken which makes my computer completely useless after about 4 or 5 minutes (it just turns off after freezing). When I try to fix this I get this error message.

```

greg@box:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.2.0-38-generic
The following NEW packages will be installed:
  linux-headers-3.2.0-38-generic
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
2 not fully installed or removed.
Need to get 0 B/985 kB of archives.
After this operation, 11.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 465779 files and directories currently installed.)
Unpacking linux-headers-3.2.0-38-generic (from .../linux-headers-3.2.0-38-generic_3.2.0-38.61_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-38-generic_3.2.0-38.61_amd64.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-38-generic/include/config/afs/fs.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-38-generic/include/config/afs/fs.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-38-generic_3.2.0-38.61_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

When I try to remove an old kernel to make space I get this error message:
```

greg@box:~$ sudo apt-get remove linux-image-3.2.0-29-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-image-3.2.0-29-generic is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-generic : Depends: linux-headers-3.2.0-38-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

This catch 22 is beyond me. I need help to sort this out.

Thanks, Greg

---

### Post by tgalati4 on 2013-03-09
Post the output of:

```
df -h
```

Linux is not tolerant of a file system's lack of space.  You typically need 10% free to be safe.

Try deleting everything in /var/cache/apt/archives.  **These are emergency procedures, normal users should not follow this blindly.**

```
cd /var/cache/apt/archives
ls -la
sudo rm *.deb
df -h
```

Then go to /boot and remove  boot packages except the last two versions.  It will look something like:

tgalati4@Mint14-Extensa /boot $ ls -la
total 49256
drwxr-xr-x  3 root root     4096 Feb 11 13:31 .
drwxr-xr-x 23 root root     4096 Feb 10 17:43 ..
-rw-r--r--  1 root root   844882 Oct  9 12:54 abi-3.5.0-17-generic
-rw-r--r--  1 root root   848290 Jan 24 05:38 abi-3.5.0-23-generic
-rw-r--r--  1 root root   147884 Oct  9 12:54 config-3.5.0-17-generic
-rw-r--r--  1 root root   147871 Jan 24 05:38 config-3.5.0-23-generic
-rw-r--r--  1 root root  1474560 Feb 11 13:19 fdboot.img
drwxr-xr-x  5 root root     4096 Feb 11 13:24 grub
-rw-r--r--  1 root root 15233289 Feb  7 08:25 initrd.img-3.5.0-17-generic
-rw-r--r--  1 root root 15238719 Feb 10 17:43 initrd.img-3.5.0-23-generic
-rw-r--r--  1 root root    26140 Feb 11 13:31 memdisk
-rw-r--r--  1 root root   176764 Jan  3 14:48 memtest86+.bin
-rw-r--r--  1 root root   178944 Jan  3 14:48 memtest86+_multiboot.bin
-rw-------  1 root root  2901710 Oct  9 12:54 System.map-3.5.0-17-generic
-rw-------  1 root root  2904246 Jan 24 05:38 System.map-3.5.0-23-generic
-rw-r--r--  1 root root  5129040 Nov 27 09:05 vmlinuz-3.5.0-17-generic
-rw-------  1 root root  5134032 Jan 24 05:38 vmlinuz-3.5.0-23-generic

Try removing any music, movies, pictures, or other personal media to some other storage--both for safe keeping and to free up space.

Once you have freed up 10% on the active partition, then run *sudo apt-get install -f* and start following it's instructions for repair.

Then go get a bigger drive and don't let it get to 90% full.

---

### Post by ibjsb4 on 2013-03-09
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-38-generic_3.2.0-38.61_amd64.deb (--unpack):  unable to create `/usr/src/linux-headers-3.2.0-38-generic/include/config/afs/fs.h.dpkg-new' (while 
processing `./usr/src/linux-headers-3.2.0-38-generic/include/config/afs/fs.h'): No space left on device

You need to remove some of those old kernels.  I use synaptic package manager for this,
but there are many ways to do it.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels+synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels+synaptic+package+manager&sa=Search&cof=FORID:9)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels&sa=Search&cof=FORID:9)

---

### Post by Dusenberg on 2013-03-26
I often have this problem on two laptops one running lubuntu 12.10 the other ubuntu 12.10.  The laptops are dual-boot with Win7 and only have 8G root partitions.  

In addition to what tgalati4 advised, I also clear out old linux-header versions from /usr/src as these take up large amounts of space.  The entries in /usr/src are directories and from a terminal I go through the list of those I want to remove and use 'sudo rm -R ' to do so.  

Here is an example of removing all version '24' directories - be v careful when using wildcards with rm -R as a typo could wipe out everything in the directory....... If you are at all uncertain, use the full directory name and do it one at a time.

```

j@j-laptop:~$ cd /usr/src
j@j-laptop:/usr/src$ ls
linux-headers-3.5.0-24          linux-headers-3.5.0-25-generic
linux-headers-3.5.0-24-generic  linux-headers-3.5.0-26
linux-headers-3.5.0-25          linux-headers-3.5.0-26-generic
j@j-laptop:/usr/src$ sudo rm -R linux-headers-3.5.0-24*
[sudo] password for j: 
j@j-laptop:/usr/src$ ls
linux-headers-3.5.0-25          linux-headers-3.5.0-26
linux-headers-3.5.0-25-generic  linux-headers-3.5.0-26-generic
```

After releasing disk space following an aborted update, I re-run the update from the terminal using the 'fix' option 
```

sudo apt-get -f update
```

---

