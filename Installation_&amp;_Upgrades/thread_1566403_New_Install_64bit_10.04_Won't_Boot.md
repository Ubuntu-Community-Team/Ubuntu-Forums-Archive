---
title: "New Install 64bit 10.04 Won't Boot"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by bper on 2010-09-02
Hello,

I created a boot flash drive, which booted fine and seemingly installed a fresh 64-bit 10.04 OS on my new 1TB drive successfully. After rebooting and removing the flash drive, the system goes through its normal startup but stalls before grub seems to load.

The system just hangs at that point. I tried re-installing the OS thinking that maybe something went wrong, but the same results.

Can you please offer some suggestions as to how I can proceed?

Thank you in advance.

---

### Post by bper on 2010-09-05
I forgot to post my own reply. It turns out that the default install/disk partition does not work for me. I have to manually partition the disk and make sure that I specify a /boot partition. Doing so enables my install to boot fine every time.

Thank you anyway.

---

