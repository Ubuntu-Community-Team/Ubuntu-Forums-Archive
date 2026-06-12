---
title: "Failing to boot after 7.10 install."
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by Wrincle on 2008-03-29
Hi,

I just performed a fresh install of 7.10 on an Acer Aspire 7520 (fairly recent so it might not be fully supported..) laptop. After rebooting and attempting to boot into the system for the first time, it initially gives a message and stops at an error. It reads:

"[0.776000] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:02:00.0
Loading, please wait...
usplash: Setting mode 1280x1024 failed
usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768
Check root = bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/(hex code) does not exist. Dropping to a shell!"

I asked for a solution on the IRC channel to which a user told me to regenerate my initramfs. So, I did so by rebooting off the LiveCD and chrooting into the install, then ran "update-initramfs -u". I rebooted into my installation and still it gives the same error.

If anyone can help me solve this I'd really appreciate it (and maybe I can learn something in the meantime :) )

Thank you!

---

### Post by Pumalite on 2008-03-29
This might help:
[http://ubuntuforums.org/showthread.php?t=595979](http://ubuntuforums.org/showthread.php?t=595979)
[http://ubuntuforums.org/showthread.php?t=632151&page=3](http://ubuntuforums.org/showthread.php?t=632151&page=3)

From another thread:

 Re: freezes at boot
I have also an Acer Aspire 5520.

The SOLUTION is very simple:

- just add the option all_generic_ide to the grub boot option

We will never have that problem again.

---

### Post by Wrincle on 2008-03-29
Thanks, it worked :)

---

