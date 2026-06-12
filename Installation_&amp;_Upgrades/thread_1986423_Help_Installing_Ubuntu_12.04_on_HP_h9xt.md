---
title: "Help Installing Ubuntu 12.04 on HP h9xt"
date: 2012-05-24
forum: Installation &amp; Upgrades
---

### Post by aselder on 2012-05-24
Hi all,

I just got a brand new HP Phoenix h9xt and I'm trying to install Ubuntu 12.04 on it.

It came with a 2 TB HD and I plopped in second 1 TB HD. It also has an AMD Radeon HD 7770. I'm trying to install Ubuntu to the 2nd HD leaving the original HD untouched, other than the MBR which I'd like alter so I can choose the OS to boot.

I downloaded the 64 bit install CD, and after booting with the radeon.modeset=0 added to the boot line,  I set the install to create swap and ext4 partitions on /dev/sdb and told it to install the boot loader to /dev/sda. The install chugs away and completes fine.

I then reboot and I just get a blank screen with and single blinking underscore. No keypresses are processed and I'm just force to hard shutdown..

I'm guessing that the install of Ubuntu succeeded, but something happened with installing the boot loader.

Does anybody have any ideas how to get things working?

Thanks,

Andrew

---

### Post by jadtech on 2012-05-24
chances are since you had to use nomodeset to boot the cd you will need it to boot in on the system to install the additional drivers

---

### Post by aselder on 2012-05-24
Yeah, I know I'll have to change the boot line in the loader, but I can't even get the boot loader to appear.

Andrew

---

### Post by jadtech on 2012-05-25
> **aselder said:**
> Yeah, I know I'll have to change the boot line in the loader, but I can't even get the boot loader to appear.

Andrew

try booting tapping pressing the **** key  see if you can get to a menu  choose recovery this might  work for you ..

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

