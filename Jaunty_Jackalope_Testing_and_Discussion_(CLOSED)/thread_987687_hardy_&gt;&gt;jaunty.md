---
title: "hardy &gt;&gt;jaunty"
date: 2008-11-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Sponzenbroekske on 2008-11-19
Can I upgrade directly to Jaunty (alpha) from Hardy, or do I gotta upgrade to intrepid first?

---

### Post by Pumalite on 2008-11-19
Intrepid first

---

### Post by Partyboi2 on 2008-11-19
Jaunty Is still real early in its development and is not recommend as a stable system. There is further discussion [[COLOR=Blue]here[/COLOR]]("http://ubuntuforums.org/forumdisplay.php?f=352") about it. But to answer your question you would need to upgrade to intrepid first.

---

### Post by Sponzenbroekske on 2008-11-19
I know that it aint stable yet, but i got hardy, vista and intrepid on one HD, hardy 32bit so experimental, my intrepid is a stable 64bit :)

---

### Post by catdriver on 2008-11-19
I want am thinking about upgrading, simply because I can, and this machine isn't mission critical.  BUT.... When I run update manager, I get a message that my software index is broken, and I need to run sudo apt-get install -f.
I do so and get this out put.....
[INDENT]chris@chris:~$ sudo apt-get install -f
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
chris@chris:~$[/INDENT] 

Oviousely these two packages are bustipated. Worse I check /lib/linux-restricted, and they are simply not there, not is there any entry in 'lib/modules... The system.map files reported missing from /boot are definitely missing as well.  I have no reference to those releases in my GRUB set up and the machine appears to run normally, except update manager and synaptic both crash....

This is an Hardy installation. 8.04LTS.  Any thoughts?

---

### Post by ravindran.k on 2009-01-24
> **catdriver said:**
> I want am thinking about upgrading, simply because I can, and this machine isn't mission critical.  BUT.... When I run update manager, I get a message that my software index is broken, and I need to run sudo apt-get install -f.
I do so and get this out put.....
This is an Hardy installation. 8.04LTS.  Any thoughts?

I will try upgrading my backup m/c today from 8.04 to jaunty alpha 3.. and keep you posted  :)

---

### Post by ravindran.k on 2009-01-24
> **ravindran.k said:**
> I will try upgrading my backup m/c today from 8.04 to jaunty alpha 3.. and keep you posted  :)
My Old P3 450 Mhz..80 GB HDD has a physical crash.. Trying to recover.. But I dont have much hopes :( 

So I wont be able to test this I guess.. :((

---

### Post by Pumalite on 2009-01-24
pumalite@pumalite-desktop:~$ uname -a
Linux pumalite-desktop 2.6.28-5-generic #15-Ubuntu SMP Fri Jan 23 01:16:33 UTC 2009 x86_64 GNU/Linux
pumalite@pumalite-desktop:~$

---

