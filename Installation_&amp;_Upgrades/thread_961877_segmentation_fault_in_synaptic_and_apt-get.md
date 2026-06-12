---
title: "segmentation fault in synaptic and apt-get"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by it.henrik on 2008-10-28
When I try to run 
```
sudo apt-get upgrade
```
I get segmentation fault after it has finished reading the list of packets.

I cant run synaptic or aptitude or the update applet, they are all giving me the segmentation fault.

Please help, how can I reinstall apt* without apt-get?

heres what my /var/log/messages says
```
henrik@henrik-laptop:~$ tail /var/log/messages
Oct 28 23:09:53 henrik-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
Oct 28 23:10:24 henrik-laptop kernel: [  225.132078] apt-check[5885]: segfault at 53c5950c eip b7cd1ca2 esp bf92f5c0 error 4
Oct 28 23:10:47 henrik-laptop kernel: [  247.575728] aptitude[5918]: segfault at 53a7250c eip b7ed6ca2 esp bffb1040 error 4
Oct 28 23:10:51 henrik-laptop kernel: [  251.770371] apt-cache[5923]: segfault at 66496201 eip b7ef920e esp bf8c9640 error 4
Oct 28 23:11:36 henrik-laptop kernel: [  296.821987] synaptic[5947]: segfault at 52c9650c eip b7f3bca2 esp bffa8f50 error 4
Oct 28 23:17:03 henrik-laptop kernel: [  623.886882] apt-get[6032]: segfault at 53b9750c eip b7e6cca2 esp bfd084f0 error 4
Oct 28 23:17:45 henrik-laptop kernel: [  665.774972] synaptic[6044]: segfault at 52c4d50c eip b7ef2ca2 esp bfcd1c70 error 4
Oct 28 23:22:30 henrik-laptop kernel: [  951.014418] apt-get[6210]: segfault at 53ba950c eip b7e7eca2 esp bfc82fd0 error 4
Oct 28 23:23:09 henrik-laptop kernel: [  989.777122] apt-get[6220]: segfault at 53c2050c eip b7ef5ca2 esp bf906050 error 4
Oct 28 23:23:23 henrik-laptop kernel: [ 1003.601528] apt-get[6224]: segfault at 53ba750c eip b7e7cca2 esp bfe699e0 error 4
henrik@henrik-laptop:~$ 
```

---

### Post by lemming465 on 2008-10-30
I'd be very nervous about disk corruption or other hardware failures with those symptoms.  

First I'd run memtest86+ for a couple hours to rule out bad RAM, then I'd boot a rescue CD and run fsck on all the disk partitions to see if any files were crosslinked, plus *smartctl -H -a* on all the disks to see what the bad block and read error situation was.

Assuming the hardware checks out and you want to upgrade rather than re-install, I'd download the alternate install CD for your version (ubuntu? kubuntu? xubuntu? ...).  It's possible to do off-line upgrades from the alternate install CD's, and I'd trust that more than trying to repair it live.

---

