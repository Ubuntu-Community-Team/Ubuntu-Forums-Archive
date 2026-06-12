---
title: "error upgrading kernel"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by laurentgedm on 2010-12-17
Hello world,

On my system, KPackageKit encounters an error when trying to upgrade from kernel 2.6.35-22 to 2.6.35-23:

```
subprocess installed post-installation script returned error exit status 2
```

What should i do?



edit: can it be due to the size of my /boot partition?

```
root@lau-linux:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8              24G  1.2G   22G   6% /
none                  998M  244K  998M   1% /dev
none                 1005M  628K 1004M   1% /dev/shm
none                 1005M   96K 1005M   1% /var/run
none                 1005M     0 1005M   0% /var/lock
/dev/sda1              22G  3.4G   19G  16% /usr
/dev/sda5              37M   27M  8.3M  77% /boot
/dev/sda9              65G   41G   22G  66% /home
/dev/sda6              71G   64G  3.7G  95% /home/Data
/dev/sdb1             917G   96G  775G  11% /home/Media
```

---

### Post by sikander3786 on 2010-12-17
No your root partition shouldn't cause that problem.

We need to see the _complete_ output of this command from your terminal.

```
sudo apt-get upgrade
```

---

### Post by laurentgedm on 2010-12-17
```

lau@lau-linux:~$ sudo apt-get upgrade
[sudo] password for lau: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.35-23-generic (2.6.35-23.41) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-2.6.35-23-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.35-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-23-generic; however:
  Package linux-image-2.6.35-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.23.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):                                                                                                                                
 dependency problems - leaving unconfigured                                                                                                                                        
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.                                                                                                                                                  
                                 Errors were encountered while processing:
 linux-image-2.6.35-23-generic                                                                                                                                                     
 linux-image-generic
 linux-generic                                                                                                                                                                     
E: Sub-process /usr/bin/dpkg returned an error code (1)


```


EDIT:

It looks like a space problem.
I don't know how to solve this.
Can i remove any of those files?

```

root@lau-linux:/boot# ls -ls
total 25853                                                                                                                                                                        
  689 -rw-r--r-- 1 root root   700477 2010-10-17 02:37 abi-2.6.35-22-generic                                                                                                       
  689 -rw-r--r-- 1 root root   700602 2010-11-24 13:46 abi-2.6.35-23-generic
  121 -rw-r--r-- 1 root root   122604 2010-10-17 02:37 config-2.6.35-22-generic                                                                                                    
  121 -rw-r--r-- 1 root root   122604 2010-11-24 13:46 config-2.6.35-23-generic
    4 drwxr-xr-x 3 root root     4096 2010-10-23 10:16 grub                                                                                                                        
10782 -rw-r--r-- 1 root root 10996207 2010-11-15 19:38 initrd.img-2.6.35-22-generic
   12 drwxr-xr-x 2 root root    12288 2010-10-16 18:51 lost+found
  163 -rw-r--r-- 1 root root   165084 2010-09-24 20:16 memtest86+.bin
  165 -rw-r--r-- 1 root root   167264 2010-09-24 20:16 memtest86+_multiboot.bin
 2298 -rw-r--r-- 1 root root  2342386 2010-10-17 02:37 System.map-2.6.35-22-generic                                                                                                
 2298 -rw-r--r-- 1 root root  2342871 2010-11-24 13:46 System.map-2.6.35-23-generic
    2 -rw-r--r-- 1 root root     1335 2010-10-17 02:41 vmcoreinfo-2.6.35-22-generic
    2 -rw-r--r-- 1 root root     1336 2010-11-24 13:48 vmcoreinfo-2.6.35-23-generic
 4253 -rw-r--r-- 1 root root  4336016 2010-10-17 02:37 vmlinuz-2.6.35-22-generic
 4254 -rw-r--r-- 1 root root  4336912 2010-11-24 13:46 vmlinuz-2.6.35-23-generic

```

---

### Post by sikander3786 on 2010-12-17
Yes now I feel this is causing the problem.

> /dev/sda5              37M   27M  8.3M  77% /boot

Why did you create that small partition for /boot? The recommended size is 512 MB at least.

You can remove the older kernels following this guide.

[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

Remember, it is recommended that you keep at least one older kernel as a backup plan.

---

### Post by rajeeja on 2010-12-17
Hi Guys,

I have the same problem and I cannot boot with any of the kernels. However I can get to the safe mode. 

Please let me know how to remove the kernel in command line?


Also, during the upgrade there were some warnings:
...
(gtk-update-icon-cache:2498): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory
...

Many thanks,

---

### Post by laurentgedm on 2010-12-17
I removed initrd.img-2.6.35-22-generic and it worked afterwards.

---

### Post by sikander3786 on 2010-12-17
> **rajeeja said:**
> Hi Guys,

I have the same problem and I cannot boot with any of the kernels. However I can get to the safe mode. 

Please let me know how to remove the kernel in command line?


Also, during the upgrade there were some warnings:
...
(gtk-update-icon-cache:2498): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory
...

Many thanks,
What do you mean by "cannot boot with any of the kernels"? Any errors, blank screen or what?

Why do you want to remove kernels? I fear that wouldn't solve your problem.

From Grub menu, select Recovery mode > Drop to root shell and try these commands.

Bring up your internet:
```
dhclient eth0
```

Where eth0 is your network interface.

```
sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

```
sudo apt-get update && sudo apt-get upgrade
```

Reboot:

```
sudo shutdown -r now
```

> **laurentgedm said:**
> I removed initrd.img-2.6.35-22-generic and it worked afterwards.


Glad to know it worked for you :-)

Happy Ubuntu-ing!

---

