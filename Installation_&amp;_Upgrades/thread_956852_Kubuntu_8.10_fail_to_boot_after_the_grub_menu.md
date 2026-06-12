---
title: "Kubuntu 8.10 fail to boot after the grub menu"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by chylee on 2008-10-23
I am using Kubuntu 8.10 with kde4

I've Install Kubuntu using the LiveCD but can not get to boot in to the os. When I start the PC, get to the grub menu and select the option to boot. The screen change to kubuntu screen then go's to text mode showing the following:
> Starting up ...
Loading, Please Wait...
Gave up waiting for root device.       Common problem
 - Boot args (cat /prog/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for right device)
 - Missing module (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/3328a24e-ca23-4ce9-88cb-1c90e1588e5b does not exist. Dropping to shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


So I type in the commands and this is what I got

(initramfs) cat /proc/cmdline
root=UUID=3328a24e-ca23-4ce9-88cb-1c90e1588e5b ro quiet splash

(initramfs) cat /proc/modules; ls /dev
[see attached files]

I also check the /dev/disk/id-uuid directory in to see if the uuid was present and it was.

I have started a post at:
[http://kubuntuforums.net/forums/index.php?topic=3098319.0](http://kubuntuforums.net/forums/index.php?topic=3098319.0)

and bug report at:
[https://bugs.launchpad.net/ubuntu/+bug/284774](https://bugs.launchpad.net/ubuntu/+bug/284774)

---

### Post by chylee on 2008-10-25
I tried Kubuntu-8.10-RC and still have the same problem

---

