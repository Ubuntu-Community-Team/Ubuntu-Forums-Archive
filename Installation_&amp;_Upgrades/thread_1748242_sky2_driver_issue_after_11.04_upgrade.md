---
title: "sky2 driver issue after 11.04 upgrade"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by davidself1001 on 2011-05-03
I am having problems with sky2 (eth0 driver) periodically disconnecting since in upgraded to 11.04 so i loaded the sk98lin driver (from the Marvell site) and it worked well (sk98lin was the loaded driver in the net config info dialog) until i had to do a reboot and when it came back up i was on sky2 again. I did the install option of the driver installation and it showed sk98lin as the installed driver when i checked the config info prior to the reboot. Now when i try to reinstall it i get the following results and sky2 is listed as the driver rather than sk98lin.


root@david-desktop:/home/david/Desktop/DriverInstall# bash ./install.sh


Installation script for sk98lin driver.
Version 10.87.3.3 (Feb-01-2011)
(C)Copyright 2003-2010 Marvell(R).
================================================== ==
Add to your trouble-report the logfile install.log
which is located in the DriverInstall directory.
================================================== ==


1) installation	 3) generate makefile
2) generate patch 4) exit
Choose your favorite installation method: 1









Please read this carefully!

This script will automatically compile and load the sk98lin
driver on your host system. Before performing both compilation
and loading, it is necessary to shutdown any device using the
sk98lin kernel module and to unload the old sk98lin kernel 
module. This script will do this automatically per default.

Please plug a card into your machine. Without a card we aren't
able to check the full driver functionality.

Do you want proceed? (y/N) y










Create tmp dir (/tmp/Sk98IfkfKllPDBeHAbFmiHkPc) [ OK ]
Check user id (0) [ OK ]
Check kernel version (2.6.38-8-generic) [ OK ]
Check kernel symbol file (/proc/kallsyms) [ OK ]
Check kernel type (SMP) [ OK ]
Check number of CPUs (4) [ OK ]
Check architecture (found) [ OK ]
Set architecture (x86_64) [ OK ]
Check compiler (/usr/bin/gcc) [ OK ]
Check mcmodel flags (kernel) [ OK ]
Check module support (/sbin/insmod) [ OK ]
Check make (/usr/bin/make) [ OK ]
Check kernel gcc version (4.5.2) (Kernel:4.5.2 == gcc:4.5.2) [ OK ]
Check sk98lin driver availability (loaded) [ OK ]
Disconnect devices: (done) [ OK ]
Remove driver (done) [ OK ]
Check kernel header files (/lib/modules/2.6.38-8-generic/build) [ OK ]
Check sources for .config file (/lib/modules/2.6.38-8-generic/build/.[ OK ]
Copy and check .config file (done) [ OK ]
Check the mem address space (lowmem) [ OK ]
Change IOMMU (enabled) [ OK ]
Create new .config file (done) [ OK ]
Execute: make oldconfig (done) [ OK ]
Check modpost availability (available) [ OK ]
Unpack the sources (done) [ OK ]
Check firmware availability (done) [ OK ]
Check kernel header version (not recognized) [ warn ]
Check kernel functions (Changed: nothing) [ OK ]
Compile the kernel (done) [ OK ]
Copy driver man page into /usr/share/man/man4/ (done) [ OK ]
Check the driver (done) [ OK ]
Delete old driver (done) [ OK ]
Copying driver (done) [ OK ]
Make dependency (done) [ OK ]
Delete temp directories (done) [ OK ]
All done. Driver installed and loaded.
To load the module manually, proceed as follows:
Enter "modprobe sk98lin"

Have fun...
root@david-desktop:/home/david/Desktop/DriverInstall# modprobe sk98lin
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
WARNING: All config files need .conf: /etc/modprobe.d/kqemu, it will be ignored in a future release.

Is the "installation" option the correct way to do the driver install or do I have to use the "patch" option for it to be permanent?

Any help would be greatly appreciated.

---

### Post by dino99 on 2011-05-03
actual kernel have sky2 driver builtin (since 2.6.28 or so)
my system run it without issue on: lucid, maverick, natty, oneiric (all 32 bits) without trouble

---

### Post by davidself1001 on 2011-05-03
After i installed the sk98lin driver (before i rebooted) i was no longer having the periodic disconnects.  Now that i am back on sky2 the disconnects are back.  I didn't have any ethernet issues with 10.10.

---

### Post by davidself1001 on 2011-05-07
I have still not been able to figure out how to keep sk98lin after reboot.  I have to do a rmmod sky2 then modprobe sk98lin after each reboot.  Can someone tell me how to make sk98lin a permanent  change?

---

### Post by davidself1001 on 2011-05-07
Do i have the question in the wrong thread?  If so, where would it more likely get a response?

---

### Post by mathia on 2011-05-08
Hi,
you must update the initramfs:
$ sudo rmmod sky2
$ sudo rmmod sk98lin
$ sudo modprobe sk98lin
$ sudo update-initramfs -u -k all
$ reboot
$ sudo lsmod | grep sk
sk98lin ...

please let me know, if it worked for you.

---

### Post by mhergh on 2011-05-29
Hi all,

I had the same problem on trying to replace the sky2 with sk98lin.
Followed the "install" path from sk98lin, everything went smooth - got the same single warning as David, installed fine.

After reboot, again sky2 active. Proceeded with the recommendation rmmod sky2;rmmod sk98lin;update-initram-fs -u -k all;reboot

After reboot BOTH drievers were loaded (lsmod|grep sk) with the sky2 beeing active.

I assume that this is an issue having more kernels on my system. This is nothing special that I need, it's just the ubuntu update process. I am using only the latest kernel 2.6.38-9 generic.

on my system are still present (based on update-initramfs output):
"
root@mhergh-ubuntu:~# update-initramfs -u -k all
update-initramfs: Generating /boot/initrd.img-2.6.38-9-generic
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
update-initramfs: Generating /boot/initrd.img-2.6.35-29-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-28-generic
"

Any idea ?

---

### Post by mhergh on 2011-05-29
An update:

I removed all older kernels and kept only the current one: 2.6.38-9-generic.

Repeated the procedure. Even after the reboot the sky2 is the active driver.

---

### Post by foresto on 2011-10-23
I think you'll have better luck if you add sk98lin to your initrd *and* blacklist the sky2 driver.

But don't bother.  I just finished packaging the latest sk98lin driver (from August 2011) for Ubuntu Natty.  It does all the configuration work for you.  You can find my announcement post here:

[http://ubuntuforums.org/showthread.php?p=11382042#post11382042](http://ubuntuforums.org/showthread.php?p=11382042#post11382042)

---

