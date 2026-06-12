---
title: "Howto remove kernel 2.6.22-14-server"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by ola on 2008-06-17
Hi,

I had some minor problems with removing an old kernel today.
```

$ sudo apt-get remove linux-image-2.6.22-14-server
...
Removing linux-ubuntu-modules-2.6.22-14-server ...
FATAL: Could not open '/boot/System.map-2.6.22-14-server': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-server
Cannot find /lib/modules/2.6.22-14-server
update-initramfs: failed for /boot/initrd.img-2.6.22-14-server
dpkg: error processing linux-ubuntu-modules-2.6.22-14-server (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Since it wanted a file it couldn't find (the FATAL error above) I created the file with:
```

$ sudo touch /boot/System.map-2.6.22-14-server

```

And ran the remove again
```


$ sudo apt-get remove linux-image-2.6.22-14-server
...
Removing linux-ubuntu-modules-2.6.22-14-server ...
WARNING: Couldn't open directory /lib/modules/2.6.22-14-server: No such file or directory
FATAL: Could not open /lib/modules/2.6.22-14-server/modules.dep.temp for writing: No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-server
Cannot find /lib/modules/2.6.22-14-server
update-initramfs: failed for /boot/initrd.img-2.6.22-14-server
dpkg: error processing linux-ubuntu-modules-2.6.22-14-server (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Now it failed to find one directory and one file so I created them with:
```

$ sudo mkdir /lib/modules/2.6.22-14-server
$ sudo touch /lib/modules/2.6.22-14-server/modules.dep.temp

```

And ran the remove once again
```

$ sudo apt-get remove linux-image-2.6.22-14-server

```
And the remove went fine.

**Update:** I had similar issues when removing 2.6.24-16-server
```

$ sudo apt-get remove linux-image-2.6.24-16-server
...
Removing linux-ubuntu-modules-2.6.24-16-server ...
FATAL: Could not open '/boot/System.map-2.6.24-16-server': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-16-server
Cannot find /lib/modules/2.6.24-16-server
update-initramfs: failed for /boot/initrd.img-2.6.24-16-server
dpkg: error processing linux-ubuntu-modules-2.6.24-16-server (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-16-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

$ sudo touch /boot/System.map-2.6.24-16-server

$ sudo apt-get remove linux-image-2.6.24-16-server
...
Removing linux-ubuntu-modules-2.6.24-16-server ...
WARNING: Couldn't open directory /lib/modules/2.6.24-16-server: No such file or directory
FATAL: Could not open /lib/modules/2.6.24-16-server/modules.dep.temp for writing: No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-16-server
Cannot find /lib/modules/2.6.24-16-server
update-initramfs: failed for /boot/initrd.img-2.6.24-16-server
dpkg: error processing linux-ubuntu-modules-2.6.24-16-server (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-16-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
$ sudo mkdir /lib/modules/2.6.24-16-server
$ sudo touch /lib/modules/2.6.24-16-server/modules.dep.temp

```

(Added this thread since I couldn't find any similar posts. Hope it helps someone.)

---

### Post by aloyr on 2009-07-05
thank you very much! i was having the same type of issue with different packages and after search everywhere this is the only post that had the info i needed to get the issue fixed.

---

### Post by euchrid on 2010-06-13
Thank you so much for this. Clear concise instructions, easy to follow and still useful two years on! 

This fixed some problems for me (after the Lucid upgrade) with outdated kernels and kernel modules that could not be removed successfully through Synaptic or apt-get autoclean.

---

