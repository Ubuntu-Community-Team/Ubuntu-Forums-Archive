---
title: "Booting stops - newtorking terminates with status 1"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by ddvorak on 2010-04-01
We are running Ubuntu on VMWare EXS Server 3i (32 bit server). We tried upgrading from Version 9.4 to 9.10. 

The server will not boot. 

It throws networking errors then just comes to a blank black screen. Here is most of the screen:
/dev/sda5 was not cleanly unmounted, check forced. (note - this is due to having turned it off at the black screen - that much I get)
/dev/sdd1: recovering journal
/dev/sdb1: recovering journal
/dev/sdc1: recovering journal
/dev/sdb1: clean, 74772/6553600 files, 15793957/26214055 blocks (check in 5 mounts)
/dev/sdd1: clean, 22599/6553600 files, 15036060/26214055 blocks 
/dev/sdc1: clean, 381500/13107200 files, 34291998/52428119 blocks 
Filesystem checks are in progress (ESC to cancel):
***** here is where I think things are going bad ************
init: network-interface (eth0) pre-start process (535) terminated with status 1
init: network-interface (eth0) post-stop process(61 terminated with status 1
init: network-interface (lo) pre-start process (615) terminated with  status 1
init: network-interface (lo) post-stop process(628) terminated with  status 1
/dev/sda5: 105/124496 files (34.3% non-contiguous), 18894/.248976 blocks
mountall: fsck /boot [410] terminated with status 1
fsck from util-linux-ng 2.16
/dev/FileU32-root: clean, 69429/734400 files, 540860/2933760 blocks
init: networking main process (708) terminated with status 1

I know just enough to be really dangerous...and frustrated.

Please help!

---

### Post by alecz20 on 2010-04-04
I have the same problem after messing around with the /etc/networking/interfaces file

I tried to make the IP static for eth0 and then the server would not boot.

Did you do anything similar?

---

### Post by prodigy_ on 2010-04-04
First, there's a known bug that may prevent Ubuntu from booting if something is wrong with /etc/network/interfaces:
[https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/512253](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/512253)

Second, since you also get "fsck /boot terminated with status 1", something might be wrong with the filesystem.

---

### Post by ddvorak on 2010-04-05
We did not change any of the information in /etc/network/interfaces. The interface had a static address before and after the update. The file system seems to be ok. We upgraded the operating system to 10.04 and this took care of the problems.

---

