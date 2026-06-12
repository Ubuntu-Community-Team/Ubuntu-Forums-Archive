---
title: "Update with latest (approx. 42) packages/kernel failed"
date: 2014-07-06
forum: Installation &amp; Upgrades
---

### Post by hansbos-nl on 2014-07-06
Approx. a month ago I installed a clean Ubunt 14.04 LTS installation and left out Samba because of all kinds of problems with it. I did an apt-get update, upgrade latest kernel etc. 
Configured everything and I had a working system. :p 

today, 6 July 2014 I did a apt-get update, upgrade, reboot, etc. because ther wher approx. 42 packages incl. some  that wanted to be upgraded.

Now my 14.04 server doesn't boot anymore? :confused:

After a reboot i get the message:

..... a long list and then:

random: lvm urandom read with 48 bits of entropy available
bio: creat slab <bio-1> at 1
random: nonblocking pool is initialized
Gave up waiting foor root device. common problems:
 - Bootargs (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Chech root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/srv1--vg-root does not exist. Dropping to a shell!
hidraw: rad HID events driver (C) Jiri Kosina
usbcore: registerd new interfacedriver usbhid
usbhid: USB HID core driver

BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)  [   39.927657] bio: create slg <bio-2> at 2

***and now nothing is happening. pressed enter and I get a promt: (initramfs)
I type exit and then enter

Now the system continues with a script and finally I get my 
Ubuntu 14.04 LTS srv1 tty1
svr1 login:
prompt back.

Don't know what's happening but one thing is certain, this is not the right way to start a server??

Any suggestions how to solve this??

Thanks,

Hans.

---

