---
title: "&quot;no kernel module were found&quot; error when installing xubuntu from hd"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sylecn on 2008-10-21
I'm trying to install xubuntu intrepid beta on a desktop.

I put downloaded xubuntu-8.10-beta-alternate-amd64.iso on C:\

Then download the hd-media kernel and initrd files from here:
[http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-amd64/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-amd64/current/images/hd-media/)
and set up grub4dos to start the installer.

The installer started successfully. I did the trick(*) when installer claim not finding the iso image. After that, the installer found and mount the iso automically.

Everything worked fine, but in the following step, I got a 
"[!!]load installer components from an installer ISO."
"No Kernel modules were found." 

Skip to load modules fails the installer.

I have found the running is 2.6.27-7-generic by using uname -a  and the modules in ISO image is *-2.6.27-4-generic-*.

Does that make the install fail to load kernel modules?
What should I do if I want to use the hd install approach?


--*trick--
switch to console 2 and execute:
mkdir /dev/loop 
ln /dev/loop0 /dev/loop/0
then back to console 1

---

