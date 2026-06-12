---
title: "Error Installing Vexira's Vashield please help.!"
date: 2011-08-04
forum: Installation &amp; Upgrades
---

### Post by MikeBren19 on 2011-08-04
When I try to install Vexira's vashield i am getting an error. Please check below.

ekimnerb@ubuntu:~/vashield$ sudo perl vashield-install.pl
Vexira Shield Configuration
Copyright (c) 1988-2011 Central Command, Inc. All rights reserved.

Loading distribution file...  Ok.
Checking platform...  Linux-i386 - Ok.

In which directory do you want to install the binary files?
[/usr/bin] /usr/bin

In which directory do you want to install the documentation files?
[/usr/share/doc] /usr/share/doc

In which directory do you want to install the manual files?
[/usr/share/man] /usr/share/man

Specify the log directory name
[/var/log] /var/log

What is the directory that contains the init scripts?
[/etc/init.d] /etc/init.d

What is the directory that contains the init directories (rc0.d - rc6.d)?
[/etc] /etc

Specify the log file name
[vashield.log] vashield.log

Enter your registration user name
[] user name

Enter your registration key (example: WESAE-WCRVC-CSNEH)
[] *****-*****-*****

Installing files...  Done.
Installing kernel module... 
No precompiled kernel module was found to match this kernel.
The installer will need to compile a kernel module.
make: Entering directory `/tmp/avshieldfs_src.O3iwT1/avshieldfs'
Makefile:65: *** Unsupported kernel version.  Stop.
make: Leaving directory `/tmp/avshieldfs_src.O3iwT1/avshieldfs'

Failed to install kernel module.
Installation aborted.
Please restart the installer or install manually.
Remove installed files.... Done.
ekimnerb@ubuntu:~/vashield$ 

===============================================

Current kernel is 

Kernel Linux 3.0.0-0300rc7-generic


Any help would be appreciated. thanks.:)

---

### Post by steve11911 on 2011-08-05
Not much out there on this but they do have a support page:

[http://support.vexira.com/KB/a134/vashield-installation.aspx](http://support.vexira.com/KB/a134/vashield-installation.aspx)

and pdf file with a scant few lines about the install:

upd.vexira.com/pub12/docs/vashield_en_vexira.pdf

Requirements:

· GLIBC 2.2.5
· kernel 2.2.x

---

