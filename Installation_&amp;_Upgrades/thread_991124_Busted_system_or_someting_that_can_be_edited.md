---
title: "Busted system or someting that can be edited?"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by catdriver on 2008-11-23
When I run update manager, I get a message that my software index is broken, and I need to run sudo apt-get install -f.
I do so and get this out put.....

    chris@chris:~$ sudo apt-get install -f
    [sudo] password for chris:
    Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    The following packages will be REMOVED:
    linux-ubuntu-modules-2.6.22-14-generic
    linux-ubuntu-modules-2.6.24-17-generic
    0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
    2 not fully installed or removed.
    After this operation, 25.2MB disk space will be freed.
    Do you want to continue [Y/n]? Y
    (Reading database ... 193250 files and directories currently installed.)
    Removing linux-ubuntu-modules-2.6.22-14-generic ...
    FATAL: Could not open '/boot/System.map-2.6.22-14-generic': No such file or directory
    update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
    Cannot find /lib/modules/2.6.22-14-generic
    update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
    dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--remove):
    subprocess post-removal script returned error exit status 1
    Removing linux-ubuntu-modules-2.6.24-17-generic ...
    FATAL: Could not open '/boot/System.map-2.6.24-17-generic': No such file or directory
    update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic
    Cannot find /lib/modules/2.6.24-17-generic
    update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
    dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--remove):
    subprocess post-removal script returned error exit status 1
    Errors were encountered while processing:
    linux-ubuntu-modules-2.6.22-14-generic
    linux-ubuntu-modules-2.6.24-17-generic
    E: Sub-process /usr/bin/dpkg returned an error code (1)
    chris@chris:~$

Obviously these two packages are bustipated. I check /lib/linux-restricted, and they are simply not there, not is there any entry in 'lib/modules... The system.map files reported missing from /boot are definitely missing as well. I have no reference to those releases in my GRUB set up and the machine appears to run normally, except update manager and synaptic both crash....

This is an Hardy installation. 8.04LTS. Any thoughts?


I tried posting this on the tail of another upgrade thread and got no responses so I thought I would try a thread of it's own before I say &%$@ it and go Macbook Pro (which I'll do any way I suspect).

---

