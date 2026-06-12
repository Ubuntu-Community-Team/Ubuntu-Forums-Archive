---
title: "Install Ubuntu, dmraid/no internet"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by boebi on 2008-03-20
Hey,

I'm having a problem with installing Ubuntu.
If I say something wrong here, please correct me.

I am running a RAID system over my HDD's, so I need dmraid installed for Ubuntu to recognize my partitions. To get dmraid I need internet acces. My network adapter (Belkin USB F5D7050) is not compatible with Ubuntu, so I can't acces the internet.


Is there any way to get my network adapter working, WITHOUT ubuntu already installed?

Please include step by step help, I know much about computers, but nothing about Linux ^^


Thanks in advance,
boebi

---

### Post by dstew on 2008-03-20
Apparently, you can compile a driver that will work with that adapter. See [this blog]("http://blog.mcnicholl.com/2008/03/11/ubuntu-710-gutsy-and-belkin-usb-wireless-networking/"). If you can boot a live CD, you can install the adapter driver onto the live CD system. It looks a bit tough though.

The other way to proceed is to download the [dmraid package from the Ubuntu packages site]("http://packages.ubuntu.com/gutsy/dmraid"), and install it using ```
sudo dpkg -i dmraid_1.0.0.rc13-2ubuntu5_i386.deb
```This is for gutsy.

---

### Post by boebi on 2008-03-21
> **dstew said:**
> Apparently, you can compile a driver that will work with that adapter. See [this blog]("http://blog.mcnicholl.com/2008/03/11/ubuntu-710-gutsy-and-belkin-usb-wireless-networking/"). If you can boot a live CD, you can install the adapter driver onto the live CD system. It looks a bit tough though.

The other way to proceed is to download the [dmraid package from the Ubuntu packages site]("http://packages.ubuntu.com/gutsy/dmraid"), and install it using ```
sudo dpkg -i dmraid_1.0.0.rc13-2ubuntu5_i386.deb
```This is for gutsy.

Thanks for the reply.
I have ubuntu version 7.04, I guess that's Gutsy.
I'll try install dmraid, after that my internet. I really hope this is gonna work...

---

### Post by boebi on 2008-03-21
Hmm.. It didn't work.
This is what Terminal gave me:

> 


To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.


ubuntu@ubuntu:~$ cd Desktop

ubuntu@ubuntu:~/Desktop$ sudo dpkg -i dmraid_1.0.0.rc13-2ubuntu5_i386.deb

Selecting previously deselected package dmraid.
(Reading database ... 91545 files and directories currently installed.)

Unpacking dmraid (from dmraid_1.0.0.rc13-2ubuntu5_i386.deb) ...
dpkg: dependency problems prevent configuration of dmraid:

dmraid depends on libc6 (>= 2.5-5); however:
  Version of libc6 on system is 2.5-0
ubuntu14.
 dmraid depends on libdevmapper1.02.1; however:
  Package libdevmapper1.02.1 is not installed.

dmraid depends on libselinux1 (>= 2.0.15); however:
  Version of libselinux1 on system is 1.32-3
ubuntu1.
 dmraid depends on libsepol1 (>= 2.0.3); however:
  Version of libsepol1 on system is 1.14-2build1.
dpkg: 
error processing dmraid (--install):
 dependency problems - leaving unconfigured

Errors were encountered while processing:
 dmraid

ubuntu@ubuntu:~/Desktop$ 




EDIT: humz, seems I have an old version huh... I'll get 7.10

---

### Post by boebi on 2008-03-21
Mount Points....

I got dmraid working, but it keeps saying there are 2 file systems with the same mount point.
All my partitions have the same mount point, but my ext3 and Linux swap.

I'm afraid to damage my other partitions, or windows if I change their mount points.
Please help

---

### Post by dstew on 2008-03-21
> I got dmraid working, but it keeps saying there are 2 file systems with the same mount point.What command did you give? Post the command and the error output.

---

### Post by boebi on 2008-03-22
I didn't give any command.
It was in the installation progress.

BTW, I got the mount points fixed.

But when I click forward, I get a comfirmation screen, my ext3 and Linux swap are listed there, I click forward and I get an error.
>  The installation on file system ... failed 
Where '...' is the full path of my partition.

---

### Post by dstew on 2008-03-22
Did you designate a partition for the root file system? To do that, you need to give your ext3 partition the mount point '/' (without the single quotes). However, I do not have experience installing directly to a RAID, so I am probably missing something...

---

