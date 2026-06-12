---
title: "New Kernel boots in initramfs"
date: 2012-03-08
forum: Installation &amp; Upgrades
---

### Post by Tos_Phoenix on 2012-03-08
Hi folks!

This Problem is related to XBMCbuntu, but since it seems to be a general problem, i'll post it here.

I was using ubuntu server + xbmc for a long time, but since my harddisk died today i tried out installing xbmcbuntu Eden RC2 on a sdcard!

Everything was working fine, until i did an apt-get dist-upgrade and installed a new kernel 3.0.0-16. 
I can't geht the system working with this kernel. 3.0.0-15 just works fine, but when i want to boot with the newer kernel, it goes straight to busybox initramfs.

Now, normally there are some error messages, like "cant find device xyz" but i don't get anything, dmesg looks fine, etc
I tried 
- reinstalling the kernel
- update-initramfs
- update-grub and so on, but nothing helps

I also installed newer nvidia-drivers, because this was a problem in a bug report i found, but then i couldn't boot with any kernel at all..(luckily i had made a backup) so it seems it has something to do with dkms, but since there are no error messages, i'm out of ideas..

well..any help or hint would be appreciated..

---

### Post by Tos_Phoenix on 2012-04-19
this problem still haunts me after an upgrade to 12.04

now i can't boot any kernel, but when i mount the root device in the initramfs, i can boot normally..

Does really noone can help me with this?

---

### Post by dzponce11 on 2012-04-19
why did you upgrade the kernel in the first place?

---

### Post by dzponce11 on 2012-04-19
I'm guessing your best bet would be to try to back up all the files you can, then wipe and reinstall.

---

### Post by Tos_Phoenix on 2012-04-20
Well..i thougt updates wouldn't hurt that much and i never had a problem with a kernel upgrade in the last 4-5 years..

Yes, I could reinstall the whole thing, but it's a lot of work and i'd also like to understand WHY this is happening...

Since it only happens when the initrd image is newly generated, it has (or should) be a bug with the initramfs-tool, and there should be a way to debug this?

---

