---
title: "Reset APT, get rid of obsolete packages, help I'm stuck!"
date: 2013-03-05
forum: Installation &amp; Upgrades
---

### Post by m666 on 2013-03-05
I'm running Lubuntu 12.10 liveCD, persistent install on FAT32-formatted 4GB pendrive (3.2GB casper file - Unetbootin method).
I can install packages, that's cool.
I tried to install alternative kernel but it failed.
Now I have linux-image-3.4.9-rt17-avl2-pae package as 'obsolete'.
It's not installed but whenever I try to install new package or upgrade the system, I get error:

lubuntu@lubuntu:~$ sudo apt-get install aptitude
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  aptitude-common libboost-iostreams1.49.0 libcwidget3
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev
Recommended packages:
  apt-xapian-index libparse-debianchangelog-perl
The following packages will be REMOVED:
  linux-image-3.4.9-rt17-avl2-pae
The following NEW packages will be installed:
  aptitude aptitude-common libboost-iostreams1.49.0 libcwidget3
0 upgraded, 4 newly installed, 1 to remove and 116 not upgraded.
2 not fully installed or removed.
Need to get 0 B/2,513 kB of archives.
After this operation, 71.1 MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 145934 files and directories currently installed.)
Removing linux-image-3.4.9-rt17-avl2-pae ...
update-initramfs: Deleting /boot/initrd.img-3.4.9-rt17-avl2-pae
lzma: (stdout): Write error: No space left on device
run-parts: /etc/kernel/postrm.d/initramfs-tools exited with return code 1
/usr/sbin/grub-probe: error: failed to get canonical path of /cow.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
dpkg: error processing linux-image-3.4.9-rt17-avl2-pae (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-3.4.9-rt17-avl2-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
lubuntu@lubuntu:~$ 

How to get rid of it? it's not in /boot, it's not in repos.

---

### Post by ibjsb4 on 2013-03-05
```
update-initramfs: Deleting /boot/initrd.img-3.4.9-rt17-avl2-pae
lzma: (stdout): Write error: [COLOR=#ff0000]No space left on device[/COLOR]
run-parts: /etc/kernel/postrm.d/initramfs-tools exited with return code 1
```

Sounds like you need to remove some of those old kernels.  I use synaptic for that, but there are other ways to do it.

[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=remove+old+kernels&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2Fresults%2F%3Fcx%3D006238239194895611142%3Au-ocqbntw_o%26q%3Dlist%2Ball%2Bkernels%2Bin%2Bterminal%26sa%3DSearch%26cof%3DFORID%3A9](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=remove+old+kernels&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2Fresults%2F%3Fcx%3D006238239194895611142%3Au-ocqbntw_o%26q%3Dlist%2Ball%2Bkernels%2Bin%2Bterminal%26sa%3DSearch%26cof%3DFORID%3A9)

---

### Post by m666 on 2013-03-06
Yes tried synaptic doesn't work

'no space left' because it's 'live cd'



lubuntu@lubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow            3.0G  1.4G  1.6G  47% /
udev            742M  4.0K  742M   1% /dev
tmpfs           301M  852K  300M   1% /run
/dev/sdb1       3.8G  3.8G     0 100% /cdrom
/dev/loop0      639M  639M     0 100% /rofs
tmpfs           751M  4.0K  751M   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            751M  596K  750M   1% /run/shm
none            100M  8.0K  100M   1% /run/user

lubuntu@lubuntu:~$ ls /cdrom/boot/
grub

lubuntu@lubuntu:~$ ls /boot
abi-3.5.0-17-generic        grub                            System.map-3.5.0-17-generic
abi-3.5.0-25-lowlatency     initrd.img-3.5.0-25-lowlatency  System.map-3.5.0-25-lowlatency
config-3.5.0-17-generic     memtest86+.bin                  vmlinuz-3.5.0-25-lowlatency
config-3.5.0-25-lowlatency  memtest86+_multiboot.bin

lubuntu@lubuntu:~$ ls /rofs/boot/
abi-3.5.0-17-generic     grub            memtest86+_multiboot.bin
config-3.5.0-17-generic  memtest86+.bin  System.map-3.5.0-17-generic
lubuntu@lubuntu:~$

---

### Post by m666 on 2013-03-06
Solution from the link provided doesn't work still the same error.
Well I have to reinstall the system I guess.

Thanks for reply!

---

### Post by dino99 on 2013-03-06
you're really funny, really  :P

if you boot on the livecd, all the commands are related to that livecd; which is (as you know) write protected (as its burned)

so apt is ok, but your brain not ;)

---

### Post by m666 on 2013-03-06
> **dino99 said:**
> you're really funny, really  :P

if you boot on the livecd, all the commands are related to that livecd; which is (as you know) write protected (as its burned)

so apt is ok, but your brain not ;)

Nothing wrong with my brain, mate. Read again first post.
It's PERSISTENT install.
I CAN install packages, make changes in /etc, it still there after reboot. Just the kernel upgrade caused problem.

---

### Post by m666 on 2013-03-06
lubuntu@lubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow            3.0G  1.4G  1.6G  47% /
udev            742M  4.0K  742M   1% /dev
tmpfs           301M  852K  300M   1% /run
/dev/sdb1       3.8G  3.8G     0 100% /cdrom
/dev/loop0      639M  639M     0 100% /rofs
tmpfs           751M  4.0K  751M   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            751M  568K  750M   1% /run/shm
none            100M  8.0K  100M   1% /run/user

/cow - that's where changes are written, physically it's 3.2GB disk image on pendrive.
In order to install kernel, system tries to write something on /rofs.

---

### Post by dino99 on 2013-03-06
sorry misunderstood

but 4 Gb for a persistent install is way too narrow, as the cache grow with updates, and /tmp needs room while decompressing/installing. 10-12 Gb is required, or everytime you need to wipe the cache first to make room.

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

An easy way to deal with the packages (kernel removal for example) is to install synaptic, then using it.

---

### Post by m666 on 2013-03-06
> 4 Gb for a persistent install is way too narrow, as the cache grow with updates, and /tmp needs room while decompressing/installing

lubuntu@lubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           751M  4.0K  751M   1% /tmp

/tmp is mounted in RAM so flushed after each reboot

> sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

I do it after each install/remove

> An easy way to deal with the packages (kernel removal for example) is to install synaptic, then using it.

I said already - synaptic generates the same error.

---

### Post by Cheesemill on 2013-03-06
You cant update or change the kernel when using a persistant USB setup.

The kernel lives in the root squashfs filesystem which is read only.

---

### Post by m666 on 2013-03-06
Well I know that!


I dont want to upgrade kernel anymore.
I want to remove it. But it's not installed. Funny.

REINSTALL

---

### Post by m666 on 2013-03-06
No need to reinstall.

lubuntu@lubuntu:~$ sudo find / -name linux-image-3*

lubuntu@lubuntu:~$ sudo rm -rf /var/lib/dpkg/info/linux-image-3.4*
lubuntu@lubuntu:~$ sudo rm -rf /var/lib/dpkg/info/linux-image-3.5*
lubuntu@lubuntu:~$ sudo rm -rf /var/crash/linux-image-3.4*
lubuntu@lubuntu:~$ sudo rm -rf /var/crash/linux-image-3.5*

Problem solved.
Thanks for replies!

---

