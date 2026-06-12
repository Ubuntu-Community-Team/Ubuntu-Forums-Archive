---
title: "Failed to install new kernel (linux-ubuntu-modules-2.6.24-22-generic)"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by subject117 on 2008-11-29
I was just running the latest updates on my ubuntu machine and one of the packages failed to install.  It involves the boot sector and the kernel and I am afraid to try rebooting my machine because I don't know if it will come back again.  While my machine is on, what can I do to fix this or reinstall the linux kernel?

Here is the error message I got:

Processing trigger for libc6...
ldconfig deffered processing now taking place
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-22-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Setting up linux-ubuntu-modules-2.6.24-22-generic (2.6.24-22.35) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-22-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-22-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-22-generic; however: Package linux-ubuntu-modules-2.6.24-22-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency probelms - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
linux-generic depends on linux-image-generic (-2.6.24.22.24); however: Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured


Running the package updater again doesn't do anything.  I don't want to reboot my computer unless I am sure this problem is fixed.  I don't have time to fix an unbootable computer.

Thanks!

---

### Post by cariboo on 2008-11-29
Note the error message:

> 
gzip: stdout: No space left on device

Clear up some disk space and reconfigure the kerenl. In a terminal type:

```
sudo apt-get autoremove
```

and

```
sudo apt-get clean
```

then in the same terminal type:

```
sudo dpkg --reconfigure linux-ubuntu-modules-2.6.24-22-generic
```

You may have to download the packages again after cleaning up the hard drive.

Jim

---

### Post by subject117 on 2008-11-29
Thanks for your quick reply.

I tried the first step but it seems to have failed:

$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic oem-config-gtk xserver-xorg-video-amd
  libboost-thread1.34.1 libboost-date-time1.34.1 localechooser-data oem-config
  linux-headers-2.6.24-19
The following packages will be REMOVED:
  libboost-date-time1.34.1 libboost-thread1.34.1 linux-headers-2.6.24-19
  linux-headers-2.6.24-19-generic localechooser-data oem-config oem-config-gtk
  xserver-xorg-video-amd
0 upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 71.0MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 180004 files and directories currently installed.)
Removing libboost-date-time1.34.1 ...
Removing libboost-thread1.34.1 ...
Removing linux-headers-2.6.24-19-generic ...
Removing linux-headers-2.6.24-19 ...
Removing xserver-xorg-video-amd ...
Removing oem-config-gtk ...
Removing oem-config ...
Removing localechooser-data ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Setting up linux-ubuntu-modules-2.6.24-22-generic (2.6.24-22.35) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-22-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-22-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-22-generic; however:
  Package linux-ubuntu-modules-2.6.24-22-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.22.24); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-22-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

I did the next two steps anyway and got this:

$ sudo apt-get clean
$ sudo  dpkg --reconfigure linux-ubuntu-modules-2.6.24-22-generic
dpkg: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

I tried using the configure option and got this:

$ sudo dpkg --configure linux-ubuntu-modules-2.6.24-22-generic
Setting up linux-ubuntu-modules-2.6.24-22-generic (2.6.24-22.35) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-22-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-22-generic (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-22-generic


What is it complaining about?  Is my boot partition too small?

---

### Post by Partyboi2 on 2008-12-01
You can check if your /boot partition is full by typing 
```
df -h
```
in a terminal. If it is full then you can open up synaptic package manager and do a search for linux-image and remove all the old kernels you no longer need, keep the current version as well as one extra as a backup. Once you have made room on your /boot partition then try
```
sudo dpkg --configure -a
```
then
```
sudo apt-get update && sudo apt-get upgrade
```

---

