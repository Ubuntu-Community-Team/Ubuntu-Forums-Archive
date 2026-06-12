---
title: "GRUB2 Blank Screen"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by liquidfalcon on 2010-11-20
Hello,

I have a machine with RAID 1 (Software) and GRUB2. After my first kernel compile I tried to install it, and then ran grub-install on /dev/mdo (My raid device) to update the list (I didnt realize at the time there was a grub-update). Now when my machine starts I get no prompt from GRUB, just an underscore, then a blank screen (After BIOS setup screen). There are only two hard drives in the array and they are the only drives in the system. Reinstalling GRUB2 didn't help either. Would someone have any idea why GRUB is doing this? If I attempt to hold shift at startup to see the output from the kernel nothing happens, so I assume that GRUB isnt even booting the kernel.

Any ideas?

Thanks in advance.

---

### Post by ronparent on 2010-11-21
Not an expert on software raid setup, but I believe that on a software raid the boot loader has to be installed on a non-raid device (ie /dev/sda). This is opposed to a fakeraid where the boot loader has to be installed to a raid device.

---

