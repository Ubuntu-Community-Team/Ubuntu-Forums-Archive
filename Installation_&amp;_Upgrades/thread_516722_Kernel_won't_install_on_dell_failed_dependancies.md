---
title: "Kernel won't install on dell: failed dependancies"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by inflamous on 2007-08-03
Hi, I've been trying to install Kubuntu 7.04 on my Dell Inspiron 1501 for the past couple of days. I have an AMD mobile Sempron 3500+ (64-bit) so I've tried both the x86 and amd64 alternate install cds, but I always get the same error. I'm putting the Linux and the boot loader on a logical drive, 15gb for Ubuntu, 1gb swap and 8mb for GRUB.

However, everything goes all and good (except the wireless, which I'll have to fix after the installation) until I reach the base installation. At about 83% when it says I get a "kernel failed to install" message and it tells me to check virtual console 4. When I check that, it tells me that linux-generic depends on linux-image-generic which is not configured yet.

I decided to change the debconf to a low priority so that I could change the kernel, however all of them fail except when I choose not to install any kernel.

Does anybody know how this problem can be fixed?

---

### Post by eggdeng on 2007-08-03
> I'm putting the Linux and the boot loader on a logical drive Is that a bootable (primary) partition?

---

### Post by az on 2007-08-03
> **inflamous said:**
> and 8mb for GRUB.


Do you mean a boot partition?  You should leave a lot more for your boot partition.  You will need room for two kernels or more.  Make it 100 megs to be safe.

---

### Post by inflamous on 2007-08-03
I've put linux on a logical drive on my desktop and it worked...

---

### Post by inflamous on 2007-08-04
thanks az, I don't know where I read that you don't need much space for the boot partition :S
So I got through the kernel installation...but now my computer just stops when it reaches the GRUB installation...I'll check the forums for a solution to that problem, thanks again though.

---

