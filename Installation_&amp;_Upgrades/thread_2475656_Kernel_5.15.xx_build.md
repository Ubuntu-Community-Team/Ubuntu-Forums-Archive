---
title: "Kernel 5.15.xx build"
date: 2022-06-03
forum: Installation &amp; Upgrades
---

### Post by snarf772 on 2022-06-03
Hi all,
I'm new to this forum so first hi everybody.
I'm using ubuntu for long now and just tested 22.04 version yesterday (server base + openbox) and I would like to rebuild my kernel to patch it with preempt rt patch.
I downloaded kernel 5.15.43 source and related rt patch 5.15.43-rt45 and patch went smoothly
kernel build was also fine and modules build and install all good.
After a grub update correct I rebooted into this new kernel and unfrotunately am not able to boot. Resulting error is :
    out of memory
    [...]   
    Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
I thought it come from my build, so I download the officiel ubuntu  22.04 kernel with running config and rebuild it. reloading grub and reboot pc bring me to the same error. So I tend to think my build is correct but something else in the environment is not correct.

Looking a various thread on the subject, I double check the /root= parameter which is fine and similar to my initial running install
All lib/modules for existing and new kernel are similar and the same for everthing related to my file system (lvm)
grub module that are used in grub.cfg are existing

I'm now a bit lost and don't where to head in order to solve this.

Hope you'll be able to help me 
Snarf

Ps: feel free to move this post where it best suits as I don't know this forum very much

---

