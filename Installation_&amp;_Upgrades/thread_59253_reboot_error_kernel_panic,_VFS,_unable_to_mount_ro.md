---
title: "reboot error: kernel panic, VFS, unable to mount root fs on unknown-block(0,0)"
date: 2005-08-23
forum: Installation &amp; Upgrades
---

### Post by adele on 2005-08-23
I downloaded kernel-source-2.6.8, made no change of the code, just reconfig it, mainly enable all the kernel-hacking options,  and then compile it with make-kpkg, install it with dpkg, no error messgers were given.

but then when I reboot the system, it says:  kernel panic, not syncing: VFS, unable to mount root fs on unknown-block(0,0). 

I can still boot from my original version of ubuntu, they are installed on the same disk, same partition hda3.
this is the file menu.lst:  the first kernel works, while the second gives the above error.
------------------------------------------------
title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.8.2308 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.8.2308 root=/dev/hda3 ro quiet splash
savedefault
boot 
------------------------------

---

