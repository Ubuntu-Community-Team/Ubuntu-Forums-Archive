---
title: "Can't Update to 8.10 software index is messed up"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by Fr33Z3RBuRN on 2008-11-02
hey i am trying to update to 8.10 but for some annoying reason my computer says that the software index is preventing me from doing any updates, add/removing of software. I am getting annoyed because I tried everything i could think of and do not know what else i can do, my friend and I typed in terminal every code we can think of but maybe we are not getting something, anyone here know of something I can put in the terminal that will fix my software index or allow me to update to 8.10 without issues

---

### Post by cariboo on 2008-11-02
Post your /etc/apt/sources.list so that we can have a look at it.

Jim

---

### Post by Fr33Z3RBuRN on 2008-11-02
ok in the terminal I'll type in sudo apt-get install updates and get


$ sudo apt-get install updates
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package updates
$ 


Or if I open the Update Manager it will give me this

Run a partial upgrade, to install as many updates as possible.

This can be caused by:
A previous upgrade which didn't complete
Problems with some of the installed software
Unofficial software packages not provided by ubuntu
normal changes of a pre-release version of ubuntu 

If i click partial upgrade it will run but then give me this

Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

Wine


OR If i click close out of that box about the running a partial upgrade it will say 

software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

After doing that in the terminal i'll get this

$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-21-generic
0 upgraded, 0 newly installed, 1 to remove and 153 not upgraded.
1 not fully installed or removed.
After this operation, 17.2MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 149198 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-21-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-21-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
Cannot find /lib/modules/2.6.24-21-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-21-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-21-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-21-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

So yeah i have absolutely no clue on where to go from here

---

