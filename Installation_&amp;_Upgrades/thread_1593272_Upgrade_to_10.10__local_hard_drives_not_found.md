---
title: "Upgrade to 10.10 : local hard drives not found"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by Oygron on 2010-10-11
Hi all, 

I made an upgrade from Ubuntu 10.04 to Ubuntu 10.10. The upgrade went well, no error or such, but when time went to reboot, it stucks just after Grub. 
I can still boot with the older kernels (2.6.32-25).

The error message with the recent kernel (2.6.35-22) is:
> 
udevd-work[173]: `/sbin/modprobe -bv pci:<lots of letters and digits>` unespected exit with status 0x0009
Gave up waiting for root device. Common problem:
-Boot args (cat /proc/cmdline)
-Check root delay
-Check root
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/<disk ID> does not exist.


According to Google, this kind of error seems to come from a disk changing name (sda -> sdb for ex), but this shouldn't be my case since I use uuid both for grub and fstab. I checked the ID, it's still the right one. In /dev (with the newest kernel) I cannot see any sda or sdb, and the "by-uuid" folder is empty. 

The result from "cat /proc/cmdline" seems OK (it corresponds to the one with the older kernel)


The result from "cat /proc/modules" seems trange to me: only 6 lines or so are listed, whereas there are almost 50 for the older one. Perhaps it is just due to the fact the kernel isn't loaded (since it cannot find it).

 
I tried to reinstall the new kernel from Synaptic, but no result.

Can someone help me ?

Thank you very much

Oygron


p.s: English is not my native language, so I may have done big mistakes in my message... Sorry.

---

### Post by Oygron on 2010-10-12
Update : 
I tried to boot with the live USB and hadn't enough time to decide if it will boot or not. In fact, I reached the selection screen in less than a minute, but after clicking on "Test without change", I waited 40 minutes without result. The system was reading on my key, so it was doing something, but after all this time, I had to return to work (it is my workstation) and stop the test. 

Maybe that will help to ID the source of the problem. 

Thank you

Trigger

p.s: I tested the USB key on another computer and it booted, so the key is valid.

Edit: It seems that it is a known bug from kernel 2.6.35 ([http://lkml.org/lkml/2010/6/16/323](http://lkml.org/lkml/2010/6/16/323)). A (temporary) solution is to add pci=nocrs in the kernel line in grub. 
Bug report opened on launchpad.

Edit2: Bug reports : 
[https://bugs.launchpad.net/ubuntu/+bug/659149](https://bugs.launchpad.net/ubuntu/+bug/659149)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/653238](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/653238)
Seems to affect all Dell Precision T3500

---

