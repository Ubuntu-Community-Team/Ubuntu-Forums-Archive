---
title: "Unable to Mount Root FS  on Uknown Block (0,0)"
date: 2018-01-28
forum: Installation &amp; Upgrades
---

### Post by dustin18 on 2018-01-28
I've been using Ubuntu for a few years but I'm still a novice. I haven't been able to boot into any kernel in about a month. I've always had to use an older linux image (3.13.0-85) to get into the system. Older or newer ones don't work. Now I can't get into any of them. My Ubuntu system is on a 2 TB removable drive (/deb/sdb). The internal drive is a corrupted old Windows drives (sda). (/dev/sdc) is the removable Live USB I used to run the boot script. 

Oddly enough I can get into the system when I boot the removable drive into a laptop and do some CLI tweaks at Grub Rescue. This doesn't work on my desktop anymore. Here is the bootscript results below. Please help!  

[https://paste.ubuntu.com/26481644/](https://paste.ubuntu.com/26481644/)

---

### Post by dustin18 on 2018-01-29
For more info, I'm able to get into Grub at the moment and bring up a  list of all the kernels to choose from. All of the newer ones  immediately restart the computer. The older ones that used to work, such  as 3.13.0-85 bring me to a black screen with the error "unable to mount  root fs on unkown block(0,0)". Let me know if you need more information  in order to offer suggestions. Thank you. 

I've read all of the entries I can regarding this error and others. I've tried boot repair too but it gave me the error "An error occured during the repair. The boot files of Ubuntu 14.04.5 LTS are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (ext4, >200MB, start of disk). This can be performed via tools such as gParted. Then select partition via the [Seperate /boot partition:] option of [Boot Repair.]" I don't exactly understand how to do that.

---

