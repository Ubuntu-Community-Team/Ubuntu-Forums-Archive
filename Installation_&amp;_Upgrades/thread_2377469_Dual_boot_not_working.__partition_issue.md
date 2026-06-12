---
title: "Dual boot not working.  partition issue?"
date: 2017-11-13
forum: Installation &amp; Upgrades
---

### Post by vrrreddy on 2017-11-13
I had a perfectly working dual boot (windows 10 and Ubuntu 16.04).  I upgraded windows 10 to the latest Fall creators version for which I had to change the partition sizes etc.  After which windows 10 is booting fine.  I am missing my dual boot.  I tried boot-repair.  here is the Pastebin.  I suspect the way I partitioned and the flags for the partition.

[http://paste.ubuntu.com/25956079/](http://paste.ubuntu.com/25956079/)

Thanks
RRR

---

### Post by oldfred on 2017-11-13
I see Acer, is this an Acer system & what model (just for the record).
All Acer so far have needed you to set an UEFI password and enable trust on the Ubuntu .efi files. You give it a name, like "ubuntu" without quotes.

I think these are all the same, but some explain it better or differently so you may understand what to do better.
 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 

You show 13 unknown devices. You probably only need to rename/set trust on one, and then should delete the rest from UEFI's NVRAM.
      
 Check current order & hex number of each entry:
sudo efibootmgr -v 

 The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

You can then check again.

 sudo efibootmgr -v

---

### Post by vrrreddy on 2017-11-14
Thanks for the help.  With the instruction about Acer (UEFI settings) it is working fine.  I remember doing similar steps to install it first time about a year ago and forgot.  

Machine Info:
Acer  R3-471T
Intel® Core&#8482; i7-5500U CPU @ 2.40GHz × 4 
Intel® HD Graphics 5500 (Broadwell GT2)

---

