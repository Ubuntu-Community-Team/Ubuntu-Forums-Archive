---
title: "Module missing from latest kernel?"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by skaramanger on 2009-12-06
Greetings all,

I'm running 9.10 on a dual core amd 64 X2 5000.  I recently upgraded the kernel from 2.6.31-15-generic to 2.16.31-16-generic. I been playing around trying to get gkrellm to discover my fans and voltages for my hardware.  No go... So I began looking for kernel modules and discovered that there is no 12c-core module for the latest kernel. Under 2.6.31-15 lists i2c-core.ko, but nothing under 2.6.31-16.  So my nest question is, Has this module been dropped/replaced or just forgotten?

TIA

---

### Post by skaramanger on 2009-12-07
Bump?

---

### Post by slakkie on 2009-12-07
File is present in a different kernel:

apt-file search i2c-core
linux-image-2.6.31-302-ec2: /lib/modules/2.6.31-302-ec2/kernel/drivers/i2c/i2c-core.ko

---

### Post by skaramanger on 2009-12-07
> **slakkie said:**
> File is present in a different kernel:

apt-file search i2c-core
linux-image-2.6.31-302-ec2: /lib/modules/2.6.31-302-ec2/kernel/drivers/i2c/i2c-core.ko
Slakkie,

Your quite right! I don't know what that particular use that kernel is for, but I was hoping to find if it was left out or forgotten in present generic kernel.

Thanks for your reply though, I wasn't aware of the utility of apt-file.

---

