---
title: "dpkg: version 'uname -r' has bad syntax"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by zebrattt on 2010-10-19
I just upgraded to ubuntu 10.10 last week.  Everything was perfect.    

I don't remember what I did which caused the following error,  probably  uninstalling bootchart.

dpkg: version 'uname -r' has bad syntax: version string has embedded spaces


I doubted dpkg package has some errors,  and tried to reinstall it.
the following command got same error:
sudo apt-get install --reinstall  dpkg   

then i booted the system using live cd and tried to reinstalled dpkg from live cd to root  on hard disk,  same error. 

I also copied  /var/lib/dpkg/available from live cd,  I still get the same error.


The error looks like  the dpkg command considers  'uname -r' as a string, rather than a command which executes to get a result string.


any ideas or suggestion for solving the problem?   thanks.




```
 

dpkg: version 'uname -r' has bad syntax: version string has embedded spaces
dpkg: version 'uname -r' has bad syntax: version string has embedded spaces
dpkg: version 'uname -r' has bad syntax: version string has embedded spaces
update-initramfs: Generating /boot/initrd.img-uname
grep: /boot/config-uname: No such file or directory
WARNING: missing /lib/modules/uname
Device driver support needs thus be built-in linux image!
FATAL: modules must be specified using absolute paths.
"uname" is a relative path
FATAL: Could not load /lib/modules/uname/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname/modules.dep: No such file or directory
&#12290;&#12290;&#12290;
FATAL: Could not load /lib/modules/uname/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname/modules.dep: No such file or directory
WARNING: Couldn't open directory /tmp/mkinitramfs_u8yLz4/lib/modules/2.6.35-22-generic: No such file or directory
FATAL: Could not open /tmp/mkinitramfs_u8yLz4/lib/modules/2.6.35-22-generic/modules.dep.temp for writing: No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic
update-initramfs: Generating /boot/initrd.img-uname
grep: /boot/config-uname: No such file or directory
WARNING: missing /lib/modules/uname
Device driver support needs thus be built-in linux image!
FATAL: modules must be specified using absolute paths.
"uname" is a relative path
FATAL: Could not load /lib/modules/uname/modules.dep: No such file or directory
&#12290;&#12290;&#12290;
FATAL: Could not load /lib/modules/uname/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/uname/modules.dep: No such file or directory
WARNING: Couldn't open directory /tmp/mkinitramfs_7G48N6/lib/modules/2.6.35-22-generic: No such file or directory
FATAL: Could not open /tmp/mkinitramfs_7G48N6/lib/modules/2.6.35-22-generic/modules.dep.temp for writing: No such file or directory
update-initramfs: Generating /boot/initrd.img--r
/usr/sbin/mkinitramfs: option requires an argument -- 'r'
W: non-GNU getopt
update-initramfs: failed for /boot/initrd.img--r
dpkg: error processing bootchart (--configure):
subprocess installed post-installation script returned error exit status 1



```

---

### Post by zebrattt on 2010-10-19
It looks like a fixed bug:

[https://bugs.launchpad.net/ubuntu/+source/ufw/+bug/618410](https://bugs.launchpad.net/ubuntu/+source/ufw/+bug/618410)

---

### Post by zebrattt on 2010-10-20
should I reinstall shell related stuff?

---

### Post by zebrattt on 2010-10-23
> **zebrattt said:**
> It looks like a fixed bug:

[https://bugs.launchpad.net/ubuntu/+source/ufw/+bug/618410](https://bugs.launchpad.net/ubuntu/+source/ufw/+bug/618410)


I finally found the problem and solution, with help from other great linux guys on mitbbs.com linux forum. 


the reason may be the script error in bootchart,  possible error is `uname -r` is written as 'uname -r'

solution:  delete the following garbage and reinstall bootchart  ( the error happened during the removal of bootchart, so that bootchart is still on my machine)


sudo rm /boot/initrd.img-uname
sudo rm /boot/initrd.img-uname -r
sudo rm /var/lib/initramfs-tools/uname
sudo rm /var/lib/initramfs-tools/uname -r
then, reinstall bootchart and  pybootchartgui


at least, my apt-get works normal now.

---

