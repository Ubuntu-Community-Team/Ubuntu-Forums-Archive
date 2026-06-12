---
title: "Can't install or uninstall software.  Software Center says error."
date: 2015-11-08
forum: Installation &amp; Upgrades
---

### Post by MechaMechanism on 2015-11-08
I can't install or uninstall because of this error and I don't know how to fix.

```
nate@saturn:~$ sudo apt-get -f install
[sudo] password for nate: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  bbswitch-dkms dkms fonts-dejavu fonts-dejavu-extra lib32gcc1 libc6-i386
  libcuda1-331 libvdpau1 linux-headers-3.13.0-32
  linux-headers-3.13.0-32-generic linux-headers-3.13.0-37
  linux-headers-3.13.0-37-generic linux-headers-3.13.0-40
  linux-headers-3.13.0-40-generic linux-image-3.13.0-32-generic
  linux-image-3.13.0-37-generic linux-image-3.13.0-40-generic
  linux-image-extra-3.13.0-32-generic linux-image-extra-3.13.0-37-generic
  linux-image-extra-3.13.0-40-generic linux-image-generic nvidia-prime
  nvidia-settings screen-resolution-extra ttf-dejavu ttf-dejavu-core
  ttf-dejavu-extra
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.13.0-67-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.13.0-67-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/15.2 MB of archives.
After this operation, 42.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 650322 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-67-generic_3.13.0-67.110_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-67-generic (3.13.0-67.110) ...
No apport report written because the error message indicates a disk full error
                                                                              dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-67-generic_3.13.0-67.110_amd64.deb (--unpack):
 unable to create `/boot/config-3.13.0-67-generic.dpkg-new' (while processing `./boot/config-3.13.0-67-generic'): No space left on device
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-67-generic_3.13.0-67.110_amd64.deb
[ Rootkit Hunter version 1.4.0 ]
File updated: searched for 168 files, found 137
E: Sub-process /usr/bin/dpkg returned an error code (1)
nate@saturn:~$
```

[ATTACH=CONFIG]265419[/ATTACH]

---

### Post by pqwoerituytrueiwoq on 2015-11-08
1st run this
[FONT=courier new]sudo apt-get autoclean[/FONT]
you will now have a little space
next we need to remove old kernels
next run 
[FONT=courier new]sudo apt-get autoremove --purge[/FONT] (if you get a no free space error reboot and try it again)
if you get a error about broken packages come back to this after the next command, you may need to run [FONT=courier new]sudo apt-get clean[/FONT] which will clear all apt cache, not just the obsolete stuff
then reboot (unless someone knows a command to make the system realize there is now free space)
then run this
[FONT=courier new]sudo apt-get install -f[/FONT]

id recommend installing synaptic and using it to remove any other old kernels, i suggest keeping the newest 2 (at lest that is the way i do it)

---

### Post by ajgreeny on 2015-11-08
You presumably have a separate /boot partition as a result of using either encryption or LVM partitioning, both of which make a /boot partition by default when you install; unfortunately a /boot partition which is often much too small, particularly if you are not in the habit of cleaning out old kernels.

If the above instructions do not work, as they may not if you have very little space left, come back again and we can go further.

**DO NOT** under any circumstances remove any files from /boot manually using the terminal or file manager as that may cause other difficult problems; use only the package management system to do this.

---

### Post by MechaMechanism on 2015-11-08
> **ajgreeny said:**
> You presumably have a separate /boot partition as a result of using either encryption or LVM partitioning, both of which make a /boot partition by default when you install; unfortunately a /boot partition which is often much too small, particularly if you are not in the habit of cleaning out old kernels.

If the above instructions do not work, as they may not if you have very little space left, come back again and we can go further.

**DO NOT** under any circumstances remove any files from /boot manually using the terminal or file manager as that may cause other difficult problems; use only the package management system to do this.I do have lvm and whole disk encryption.  My boot partition and grub are on a sd card.  My sd card is 2gb with about 600mb used.  I tried to remove kernels below 3.13.67 but apt-get would not do it.  Would dpkg work?  I suspect you are right.  I do need to remove kernels.  Maybe dpkg is the way to go.  You will have to show me as i am not sure about what to do with dpkg assuming that is the next step.

]

---

### Post by ajgreeny on 2015-11-08
Show us the output of ```
dpkg -l | grep linux-image
``` which will list the kernel versions installed and we can try dpkg -P commands for the first one or two old kernels and then try to autoremove the rest.

---

### Post by MechaMechanism on 2015-11-08
> **ajgreeny said:**
> Show us the output of ```
dpkg -l | grep linux-image
``` which will list the kernel versions installed and we can try dpkg -P commands for the first one or two old kernels and then try to autoremove the rest.

```
nate@saturn:~$ dpkg -l | grep linux-image
ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-36-generic                         3.13.0-36.63                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-37-generic                         3.13.0-37.64                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-39-generic                         3.13.0-39.66                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-40-generic                         3.13.0-40.69                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-43-generic                         3.13.0-43.72                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-45-generic                         3.13.0-45.74                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-49-generic                         3.13.0-49.83                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-51-generic                         3.13.0-51.84                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-52-generic                         3.13.0-52.86                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-55-generic                         3.13.0-55.94                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-57-generic                         3.13.0-57.95                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-61-generic                         3.13.0-61.100                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-65-generic                         3.13.0-65.106                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-66-generic                         3.13.0-66.108                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic                   3.13.0-36.63                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic                   3.13.0-37.64                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                   3.13.0-39.66                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-40-generic                   3.13.0-40.69                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                   3.13.0-43.72                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                   3.13.0-45.74                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic                   3.13.0-49.83                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-51-generic                   3.13.0-51.84                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic                   3.13.0-52.86                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic                   3.13.0-55.94                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-57-generic                   3.13.0-57.95                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-61-generic                   3.13.0-61.100                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic                   3.13.0-65.106                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-66-generic                   3.13.0-66.108                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-extra-3.13.0-67-generic                   3.13.0-67.110                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                                   3.13.0.67.73                                        amd64        Generic Linux kernel image
nate@saturn:~$
```

---

### Post by ajgreeny on 2015-11-08
OK, let's try command ```
sudo dpkg -P linux-image-3.13.0-{32,34,36,37,39,40,43,44,45,49,51,52,55,57,61}-generic
``` as a start and see if that works as it should, though with lack of space it may still throw an error.

---

### Post by MechaMechanism on 2015-11-08
> **ajgreeny said:**
> OK, let's try command ```
sudo dpkg -P linux-image-3.13.0-{32,34,36,37,39,40,43,44,45,49,51,52,55,57,61}-generic
``` as a start and see if that works as it should, though with lack of space it may still throw an error.

Looked on the internet, found this.  Should be enough free space.```
nate@saturn:~$ sudo df -i
Filesystem                     Inodes  IUsed     IFree IUse% Mounted on
/dev/mapper/sol-earth_crypt 238092288 780291 237311997    1% /
none                          1022063      2   1022061    1% /sys/fs/cgroup
udev                          1018190    582   1017608    1% /dev
tmpfs                         1022063    612   1021451    1% /run
none                          1022063      5   1022058    1% /run/lock
none                          1022063      9   1022054    1% /run/shm
none                          1022063     24   1022039    1% /run/user
/dev/sdg1                      122160    377    121783    1% /boot
/home/nate/.Private         238092288 780291 237311997    1% /home/nate
nate@saturn:~$
```Tried your command.```
nate@saturn:~$ sudo dpkg -P linux-image-3.13.0-{32,34,36,37,39,40,43,44,45,49,51,52,55,57,61}-generic
[sudo] password for nate: 
dpkg: dependency problems prevent removal of linux-image-3.13.0-32-generic:
 linux-image-extra-3.13.0-32-generic depends on linux-image-3.13.0-32-generic.

dpkg: error processing package linux-image-3.13.0-32-generic (--purge):
 dependency problems - not removing
dpkg: warning: ignoring request to remove linux-image-3.13.0-34-generic which isn't installed
dpkg: dependency problems prevent removal of linux-image-3.13.0-36-generic:
 linux-image-extra-3.13.0-36-generic depends on linux-image-3.13.0-36-generic.

dpkg: error processing package linux-image-3.13.0-36-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-37-generic:
 linux-image-extra-3.13.0-37-generic depends on linux-image-3.13.0-37-generic.

dpkg: error processing package linux-image-3.13.0-37-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-39-generic:
 linux-image-extra-3.13.0-39-generic depends on linux-image-3.13.0-39-generic.

dpkg: error processing package linux-image-3.13.0-39-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-40-generic:
 linux-image-extra-3.13.0-40-generic depends on linux-image-3.13.0-40-generic.

dpkg: error processing package linux-image-3.13.0-40-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-43-generic:
 linux-image-extra-3.13.0-43-generic depends on linux-image-3.13.0-43-generic.

dpkg: error processing package linux-image-3.13.0-43-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-44-generic:
 linux-image-extra-3.13.0-44-generic depends on linux-image-3.13.0-44-generic.

dpkg: error processing package linux-image-3.13.0-44-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-45-generic:
 linux-image-extra-3.13.0-45-generic depends on linux-image-3.13.0-45-generic.

dpkg: error processing package linux-image-3.13.0-45-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-49-generic:
 linux-image-extra-3.13.0-49-generic depends on linux-image-3.13.0-49-generic.

dpkg: error processing package linux-image-3.13.0-49-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-51-generic:
 linux-image-extra-3.13.0-51-generic depends on linux-image-3.13.0-51-generic.

dpkg: error processing package linux-image-3.13.0-51-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-52-generic:
 linux-image-extra-3.13.0-52-generic depends on linux-image-3.13.0-52-generic.

dpkg: error processing package linux-image-3.13.0-52-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-55-generic:
 linux-image-extra-3.13.0-55-generic depends on linux-image-3.13.0-55-generic.

dpkg: error processing package linux-image-3.13.0-55-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-57-generic:
 linux-image-extra-3.13.0-57-generic depends on linux-image-3.13.0-57-generic.

dpkg: error processing package linux-image-3.13.0-57-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.13.0-61-generic:
 linux-image-extra-3.13.0-61-generic depends on linux-image-3.13.0-61-generic.

dpkg: error processing package linux-image-3.13.0-61-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-3.13.0-32-generic
 linux-image-3.13.0-36-generic
 linux-image-3.13.0-37-generic
 linux-image-3.13.0-39-generic
 linux-image-3.13.0-40-generic
 linux-image-3.13.0-43-generic
 linux-image-3.13.0-44-generic
 linux-image-3.13.0-45-generic
 linux-image-3.13.0-49-generic
 linux-image-3.13.0-51-generic
 linux-image-3.13.0-52-generic
 linux-image-3.13.0-55-generic
 linux-image-3.13.0-57-generic
 linux-image-3.13.0-61-generic
nate@saturn:~$
```

---

### Post by matt_symes on 2015-11-08
Hi

Try this slightly modified command as linux-image-extra... is causing dependency issues.

dpkg should be smart enough to remove the -image-extra- package before the -image- package but if it's not then the -image-extra- packages can be removed manually first followed by the -image- packages.

Copy and paste it into the terminal

```
sudo dpkg -P linux-image{-extra}-3.13.0-{32,36,37,39,40,43,44,45,49,51,52,55,57,61}-generic
```

> **MechaMechanism said:**
> Looked on the internet, found this.  Should be enough free space.```
nate@saturn:~$ sudo df -i
Filesystem                     Inodes  IUsed     IFree IUse% Mounted on
/dev/mapper/sol-earth_crypt 238092288 780291 237311997    1% /
none                          1022063      2   1022061    1% /sys/fs/cgroup
udev                          1018190    582   1017608    1% /dev
tmpfs                         1022063    612   1021451    1% /run
none                          1022063      5   1022058    1% /run/lock
none                          1022063      9   1022054    1% /run/shm
none                          1022063     24   1022039    1% /run/user
/dev/sdg1                      122160    377    121783    1% /boot
/home/nate/.Private         238092288 780291 237311997    1% /home/nate
nate@saturn:~$
```


The command you ran will (and has) displayed the number of inodes free on those partitions, not the amount of free space.

BTW: There's no need for *sudo* in the df -i command you ran.

To see the amount of free space, try this command instead.

```
df -h
```

You may want to remove the corresponding header files for those kernels as well.

Kind regards

---

### Post by MechaMechanism on 2015-11-08
> **matt_symes said:**
> Hi

Try this slightly modified command as linux-image-extra... is causing dependency issues.

dpkg should be smart enough to remove the -image-extra- package before the -image- package but if it's not then the -image-extra- packages can be removed manually first followed by the -image- packages.

Copy and paste it into the terminal

```
sudo dpkg -P linux-image{-extra}-3.13.0-{32,36,37,39,40,43,44,45,49,51,52,55,57,61}-generic
```



The command you ran will (and has) displayed the number of inodes free on those partitions, not the amount of free space.

BTW: There's no need for *sudo* in the df -i command you ran.

To see the amount of free space, try this command instead.

```
df -h
```

You may want to remove the corresponding header files for those kernels as well.

Kind regards
Didn't work, the command gave error.  ```
nate@saturn:~$ sudo dpkg -P linux-image{-extra}-3.13.0-{32,36,37,39,40,43,44,45,49,51,52,55,57,61}-generic
[sudo] password for nate: 
dpkg: error: --purge needs a valid package name but 'linux-image{-extra}-3.13.0-32-generic' is not: illegal package name in specifier 'linux-image{-extra}-3.13.0-32-generic': character `{' not allowed (only letters, digits and characters `-+._')

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !
nate@saturn:~$
```

```
nate@saturn:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/sol-earth_crypt  3.5T  325G  3.0T  10% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         3.9G  4.0K  3.9G   1% /dev
tmpfs                        799M  1.4M  798M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         3.9G  688K  3.9G   1% /run/shm
none                         100M   36K  100M   1% /run/user
/dev/sdg1                    1.9G  614M  1.2G  35% /boot
/home/nate/.Private          3.5T  325G  3.0T  10% /home/nate
nate@saturn:~$
```

---

### Post by MechaMechanism on 2015-11-08
Here's a screen shot from the program Disk.

---

### Post by matt_symes on 2015-11-08
Hi

Typo ! Missed out a comma. Spot it if you can :)

```
sudo dpkg -P linux-image{-extra,}-3.13.0-{32,36,37,39,40,43,44,45,49,51,52,55,57,61}-generic
```

Does it complete successfully ?

Kind regards

---

### Post by MechaMechanism on 2015-11-08
> **matt_symes said:**
> Hi

Typo ! Missed out a comma. Spot it if you can :)

```
sudo dpkg -P linux-image{-extra,}-3.13.0-{32,36,37,39,40,43,44,45,49,51,52,55,57,61}-generic
```

Does it complete successfully ?

Kind regardsIt looks like they completed successfully.  What should I do next?  Use software center or updater?

---

### Post by matt_symes on 2015-11-08
Hi

Next type

```
sudo apt-get -f install
```

This will fix any errors that may be lingering in the package manager.

Next we should remove all the header files associated with those kernels.

```
sudo dpkg -P linux-headers-3.13.0-{32,36,37,39,40,43,44,45,49,51,52,55,57,61}-generic
```

Finally post the output of 

```
df -h && df -i
```

Kind regards

---

### Post by MechaMechanism on 2015-11-08
> **matt_symes said:**
> Hi

Next type

```
sudo apt-get -f install
```

This will fix any errors that may be lingering in the package manager.

Next we should remove all the header files associated with those kernels.

```
sudo dpkg -P linux-headers-3.13.0-{32,36,37,39,40,43,44,45,49,51,52,55,57,61}-generic
```

Finally post the output of 

```
df -h && df -i
```

Kind regards

It wants to install a bunch of old kernels.```
nate@saturn:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  bbswitch-dkms dkms fonts-dejavu fonts-dejavu-extra lib32gcc1 libc6-i386
  libcuda1-331 libvdpau1 linux-headers-3.13.0-32 linux-headers-3.13.0-37
  linux-headers-3.13.0-40 linux-image-3.13.0-40-generic
  linux-image-extra-3.13.0-40-generic linux-image-generic nvidia-prime
  nvidia-settings screen-resolution-extra ttf-dejavu ttf-dejavu-core
  ttf-dejavu-extra
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.13.0-39-generic linux-image-3.13.0-40-generic
  linux-image-3.13.0-43-generic linux-image-3.13.0-44-generic
  linux-image-3.13.0-45-generic linux-image-3.13.0-49-generic
  linux-image-3.13.0-51-generic linux-image-3.13.0-52-generic
  linux-image-3.13.0-55-generic linux-image-3.13.0-57-generic
  linux-image-3.13.0-61-generic linux-image-3.13.0-67-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
  linux-headers-3.13.0-39-generic linux-headers-3.13.0-40-generic
  linux-headers-3.13.0-43-generic linux-headers-3.13.0-44-generic
  linux-headers-3.13.0-45-generic linux-headers-3.13.0-49-generic
  linux-headers-3.13.0-51-generic linux-headers-3.13.0-52-generic
  linux-headers-3.13.0-55-generic linux-headers-3.13.0-57-generic
  linux-headers-3.13.0-61-generic
The following NEW packages will be installed:
  linux-image-3.13.0-39-generic linux-image-3.13.0-40-generic
  linux-image-3.13.0-43-generic linux-image-3.13.0-44-generic
  linux-image-3.13.0-45-generic linux-image-3.13.0-49-generic
  linux-image-3.13.0-51-generic linux-image-3.13.0-52-generic
  linux-image-3.13.0-55-generic linux-image-3.13.0-57-generic
  linux-image-3.13.0-61-generic linux-image-3.13.0-67-generic
0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
13 not fully installed or removed.
Need to get 0 B/586 MB of archives.
After this operation, 507 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.
nate@saturn:~$
``````
nate@saturn:~$ df -h && df -i
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/sol-earth_crypt  3.5T  323G  3.0T  10% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         3.9G  4.0K  3.9G   1% /dev
tmpfs                        799M  1.4M  798M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         3.9G  160K  3.9G   1% /run/shm
none                         100M   36K  100M   1% /run/user
/dev/sdg1                    1.9G  614M  1.2G  35% /boot
/home/nate/.Private          3.5T  323G  3.0T  10% /home/nate
Filesystem                     Inodes  IUsed     IFree IUse% Mounted on
/dev/mapper/sol-earth_crypt 238092288 583528 237508760    1% /
none                          1022063      2   1022061    1% /sys/fs/cgroup
udev                          1018190    582   1017608    1% /dev
tmpfs                         1022063    612   1021451    1% /run
none                          1022063      5   1022058    1% /run/lock
none                          1022063      8   1022055    1% /run/shm
none                          1022063     25   1022038    1% /run/user
/dev/sdg1                      122160    377    121783    1% /boot
/home/nate/.Private         238092288 583528 237508760    1% /home/nate
nate@saturn:~$
```

---

### Post by matt_symes on 2015-11-09
Ho

Open a terminal and type

```
sudo apt-get autoremove
```

Does that return any errors ?

If not then type (again)

```
sudo apt-get -f install
```

Does it still want to install those old kernels ?

Free space and and inode count on /boot is now looking very good so it just a case of fixing apt.

Kind regards

---

### Post by ajgreeny on 2015-11-09
Just as a guard against wrong-doings I always run that autoremove command first using the simulate option, ie ```
sudo apt-get -s autoremove
```and can check carefully what is going to be removed before it really happens.

There was obviously something strange going on in your system with a /boot partition of that size running out of space, but you certainly did have a lot of kernels installed, so perhaps it was not too surprising. However, apt then wanting to add back in kernels that we wanted to remove; there must have been dependencies left behind which still required those kernels, but hopefully the autoremove command will now be able to take care of it all for you.

It is worth running that autoremove command reasonably regularly, particularly as you have a separate /boot partition.

---

### Post by matt_symes on 2015-11-09
Hi

> **ajgreeny said:**
> Just as a guard against wrong-doings I always run that autoremove command first using the simulate option, ie ```
sudo apt-get -s autoremove
```and can check carefully what is going to be removed before it really happens.

This is solid advice. It'll highlight any potential issues you may have.

Kind Regards

---

### Post by MechaMechanism on 2015-11-09
> **ajgreeny said:**
> Just as a guard against wrong-doings I always run that autoremove command first using the simulate option, ie ```
sudo apt-get -s autoremove
```and can check carefully what is going to be removed before it really happens.

There was obviously something strange going on in your system with a /boot partition of that size running out of space, but you certainly did have a lot of kernels installed, so perhaps it was not too surprising. However, apt then wanting to add back in kernels that we wanted to remove; there must have been dependencies left behind which still required those kernels, but hopefully the autoremove command will now be able to take care of it all for you.

It is worth running that autoremove command reasonably regularly, particularly as you have a separate /boot partition.

So I simulated the command first.  Seemed fine.  So I ran the real one and it looks like something still depends on things.  Just so you know I used to use the proprietary Nvidia drivers, but have switched to nouveau, maybe a driver, video or something else depends on the kernels?.

```
nate@saturn:~$ sudo apt-get autoremove
[sudo] password for nate: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-3.13.0-39-generic : Depends: linux-image-3.13.0-39-generic but it is not installed
 linux-image-extra-3.13.0-40-generic : Depends: linux-image-3.13.0-40-generic but it is not installed
 linux-image-extra-3.13.0-43-generic : Depends: linux-image-3.13.0-43-generic but it is not installed
 linux-image-extra-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic but it is not installed
 linux-image-extra-3.13.0-45-generic : Depends: linux-image-3.13.0-45-generic but it is not installed
 linux-image-extra-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic but it is not installed
 linux-image-extra-3.13.0-51-generic : Depends: linux-image-3.13.0-51-generic but it is not installed
 linux-image-extra-3.13.0-52-generic : Depends: linux-image-3.13.0-52-generic but it is not installed
 linux-image-extra-3.13.0-55-generic : Depends: linux-image-3.13.0-55-generic but it is not installed
 linux-image-extra-3.13.0-57-generic : Depends: linux-image-3.13.0-57-generic but it is not installed
 linux-image-extra-3.13.0-61-generic : Depends: linux-image-3.13.0-61-generic but it is not installed
 linux-image-extra-3.13.0-67-generic : Depends: linux-image-3.13.0-67-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.13.0-67-generic but it is not installed
E: Unmet dependencies. Try using -f.
nate@saturn:~$
```

---

### Post by matt_symes on 2015-11-09
Hi

> **MechaMechanism said:**
> ```
nate@saturn:~$ sudo apt-get autoremove
[sudo] password for nate: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-3.13.0-39-generic : Depends: linux-image-3.13.0-39-generic but it is not installed
 linux-image-extra-3.13.0-40-generic : Depends: linux-image-3.13.0-40-generic but it is not installed
 linux-image-extra-3.13.0-43-generic : Depends: linux-image-3.13.0-43-generic but it is not installed
 linux-image-extra-3.13.0-44-generic : Depends: linux-image-3.13.0-44-generic but it is not installed
 linux-image-extra-3.13.0-45-generic : Depends: linux-image-3.13.0-45-generic but it is not installed
 linux-image-extra-3.13.0-49-generic : Depends: linux-image-3.13.0-49-generic but it is not installed
 linux-image-extra-3.13.0-51-generic : Depends: linux-image-3.13.0-51-generic but it is not installed
 linux-image-extra-3.13.0-52-generic : Depends: linux-image-3.13.0-52-generic but it is not installed
 linux-image-extra-3.13.0-55-generic : Depends: linux-image-3.13.0-55-generic but it is not installed
 linux-image-extra-3.13.0-57-generic : Depends: linux-image-3.13.0-57-generic but it is not installed
 linux-image-extra-3.13.0-61-generic : Depends: linux-image-3.13.0-61-generic but it is not installed
 linux-image-extra-3.13.0-67-generic : Depends: linux-image-3.13.0-67-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.13.0-67-generic but it is not installed
E: Unmet dependencies. Try using -f.
nate@saturn:~$
```

There is something wrong with your package system there. Let's try to find out what.

Can you post the output of these commands. We'll take a look at just one of the problematic kernels, assuming the same problem affects all of them.

```
dpkg -l linux-image{-extra,}-3.13.0-67-generic
```

That's a small L above.

```
apt-cache policy linux-image{-extra,}-3.13.0-67-generic
```

Kind regards

---

### Post by ajgreeny on 2015-11-09
Yes, I thought we had already removed all those unwanted linux-image-extra versions, but apparently not.
```
dpkg --list | grep linux-image-extra*
``` will tell us all of the "extra" kernel versions that remain in spite of our best attempts to remove them.

---

### Post by MechaMechanism on 2015-11-10
Did the following as suggested.

```
nate@saturn:~$ dpkg -l linux-image{-extra,}-3.13.0-67-generic
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                  Version                                             Architecture Description
+++-=====================================================-===================================================-============-===============================================================================
in  linux-image-3.13.0-67-generic                         <none>                                              amd64        (no description available)
iU  linux-image-extra-3.13.0-67-generic                   3.13.0-67.110                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
```


```
apt-cache policy linux-image{-extra,}-3.13.0-67-generic
linux-image-extra-3.13.0-67-generic:
  Installed: 3.13.0-67.110
  Candidate: 3.13.0-67.110
  Version table:
 *** 3.13.0-67.110 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
linux-image-3.13.0-67-generic:
  Installed: (none)
  Candidate: 3.13.0-67.110
  Version table:
     3.13.0-67.110 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
```

```
dpkg --list | grep linux-image-extra*
pH  linux-image-extra-3.13.0-39-generic                   3.13.0-39.66                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
pH  linux-image-extra-3.13.0-40-generic                   3.13.0-40.69                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
pH  linux-image-extra-3.13.0-43-generic                   3.13.0-43.72                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
pH  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
pH  linux-image-extra-3.13.0-45-generic                   3.13.0-45.74                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
pH  linux-image-extra-3.13.0-49-generic                   3.13.0-49.83                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
pH  linux-image-extra-3.13.0-51-generic                   3.13.0-51.84                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
pH  linux-image-extra-3.13.0-52-generic                   3.13.0-52.86                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
pH  linux-image-extra-3.13.0-55-generic                   3.13.0-55.94                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
pH  linux-image-extra-3.13.0-57-generic                   3.13.0-57.95                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
pH  linux-image-extra-3.13.0-61-generic                   3.13.0-61.100                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic                   3.13.0-65.106                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-66-generic                   3.13.0-66.108                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-extra-3.13.0-67-generic                   3.13.0-67.110                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
```

---

### Post by matt_symes on 2015-11-10
Hi

Your image extra packages status' are flagged as being half installed. It looks like the purge operation did not run.

Let's try to force the removal one of the image-extra packages and if it works, we'll force the removal of the rest.

```
sudo dpkg -P --force-remove-reinstreq linux-image-extra-3.13.0-39-generic
```

Please post back all the output of the above command even if you think it completes successfully.

The post the output of this command so we can check the status of the package again after running the above command.

```
dpkg -l linux-image-extra-3.13.0-39-generic
```

Kind Regards

---

### Post by MechaMechanism on 2015-11-11
Now my computer won't post.  Turn on and nothing.  This has happened before.  I will take it to repair shop Thursday morning.  It's a hardware issue and could be the bios.  I will revive this thread when I get the hardware fixed.  The pakage management issue does not have anything to do with the hardware since this has happened before and dpkg was fine.  Thanks for your help.  Expect me to check back in sometime next week.  The weekend is here so the computer shop will get back to me Monday or Tuesday.

---

### Post by matt_symes on 2015-11-11
Hi

> **MechaMechanism said:**
> Now my computer won't post.  Turn on and nothing.  This has happened before.  I will take it to repair shop Thursday morning.  It's a hardware issue and could be the bios.  I will revive this thread when I get the hardware fixed.  The pakage management issue does not have anything to do with the hardware since this has happened before and dpkg was fine.  Thanks for your help.  Expect me to check back in sometime next week.  The weekend is here so the computer shop will get back to me Monday or Tuesday.

Post when you're ready. We'll all be here.

Kind regards

---

### Post by MechaMechanism on 2015-12-13
Well, my computer broke and the bill to repair my 2008 computer was $350.  I said no.  I bought a new computer from System76 instead.  I guess we'll never know what the problem was.  Gonna stick those hard drives in the new computer and back everything up.  I already had a recent backup on an external hard drive too, thank goodness.

Should I mark this thread solved even though it's not or what should I do mods and admins?

---

