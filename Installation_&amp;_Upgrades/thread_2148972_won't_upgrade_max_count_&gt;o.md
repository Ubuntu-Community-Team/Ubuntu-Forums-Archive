---
title: "won't upgrade max count &gt;o"
date: 2013-05-27
forum: Installation &amp; Upgrades
---

### Post by eddymo on 2013-05-27
I have the red dot warning - says I have unmet dependencies. Running update says file is downloaded but won't install. Install from terminal prduces this:

:~$ sudo apt-get -f install
[sudo] password for ed: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-32 linux-headers-3.2.0-32-generic
  linux-headers-3.2.0-32-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.2.0-44-generic-pae
The following NEW packages will be installed:
  linux-headers-3.2.0-44-generic-pae
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/979 kB of archives.
After this operation, 11.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 551369 files and directories currently installed.)
Unpacking linux-headers-3.2.0-44-generic-pae (from .../linux-headers-3.2.0-44-generic-pae_3.2.0-44.69_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-44-generic-pae_3.2.0-44.69_i386.deb (--unpack):
 error creating symbolic link `./usr/src/linux-headers-3.2.0-44-generic-pae/include/linux/if_bonding.h': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-44-generic-pae_3.2.0-44.69_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ed@ed-PCG-FXA49-UC:~$

disk size
@ed-PCG-FXA49-UC:~$ sudo df -h
[sudo] password for ed: 
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       8.7G  6.5G  1.8G  79% /
udev            241M  4.0K  241M   1% /dev
tmpfs           100M  796K   99M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            248M   80K  248M   1% /run/shm
ed@ed-PCG-FXA49-UC:~$ 

I've tried cleaning, updating,upgrading purging all with the same results. Can anyone help?

Thanks
Ed

---

### Post by efflandt on 2013-05-27
Did you do "sudo apt-get autoremove" yet? How many old kernels are still on the system.

Is that a USB memory stick (although odd size) or Wubi install (within Windows).  In any case, it appears that you need more space or larger partition for whatever files you have on it. If it is in Wubi maybe the block size is big enough that small files occupy much more space than the data, making free blocks limited for all the files of Linux headers.

---

### Post by eddymo on 2013-05-27
> **efflandt said:**
> Did you do "sudo apt-get autoremove" yet? How many old kernels are still on the system.

Is that a USB memory stick (although odd size) or Wubi install (within Windows).  In any case, it appears that you need more space or larger partition for whatever files you have on it. If it is in Wubi maybe the block size is big enough that small files occupy much more space than the data, making free blocks limited for all the files of Linux headers.

Was at one time dedicated windows computer loaded 12.04 in oct 12 with a small partition. Now set up as dual boot but only ubuntu works.
Computer always up to date till yesterday. I'am sure there are old kernals on system - not sure how to remove. Ubuntu was installed via bootable cd in oct 12. 

Same errors after running autoremove.

How do I safely remove old kernels?

btw thanks for the reply - Ed

---

### Post by eddymo on 2013-05-28
After resizing my partition (root) using a Gparted live cd I was able to apt-get -f install which updated the unmet dependencies. Apt-get autoremove cleaned up the uneeded kernels and the red warning dot is gone. I'm happy again!

---

