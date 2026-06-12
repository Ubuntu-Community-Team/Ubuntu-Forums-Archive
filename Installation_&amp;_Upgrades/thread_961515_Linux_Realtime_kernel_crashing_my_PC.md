---
title: "Linux Realtime kernel crashing my PC"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by Boneless on 2008-10-28
Hi,

I have a HP Compaq nx8220 with Ubuntu 7.10, I tried instaling the realtime kernel:

> Package: linux-rt
Priority: optional
Section: multiverse/metapackages
Installed-Size: 52
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta
Version: 2.6.22.14.21
Depends: linux-image-rt (= 2.6.22.14.21), linux-restricted-modules-rt (= 2.6.22.14.21)
Filename: pool/multiverse/l/linux-meta/linux-rt_2.6.22.14.21_i386.deb

but it crashes my PC at start-up, it doesn't even access to the disk, it simply locks before (requiring a hard reset).
I don't have a clue about what to do... :(

---

### Post by dstew on 2008-10-28
Do you get any kernel error messages before it locks up? You might need to remove **quiet splash** from the kernel line in your grub menu to see the errors.

---

### Post by Boneless on 2008-10-28
I read the messages, can't really remember what's written (couldn't be bothered to write down by hand all those messages :D ) but no error messages... last lines were something like "linux-kernel-thread-helper blah blah", then "=====================" and that's it. It just locks there.

---

### Post by dstew on 2008-10-28
I have read somewhere that the esd process causes the realtime kernel to freeze in some systems. If you can get a command line, try```
sudo killall esd
```
That's just a guess. It would be nice to know what messages you see before it locks up. Maybe the realtime kernel will not work for you, I don't know. You might have to check on a site about the realtime kernel.

---

### Post by Boneless on 2008-10-29
I don't think that's the case, I can't even login... it just freezes seconds after GRUB loads the kernel...

---

### Post by dstew on 2008-10-29
I really don't know much about the realtime kernel, but in general when you have a kernel crash like you are having, you should be able to see some errors output by the kernel or the intial RAM file system. Often you will get a "kernel panic" message. Do you remember seeing a "kernel panic message"?

Sometimes you can get a balky kernel to load by using certain parameters on the kernel line to bypass problem hardware drivers. You can try these. Add them to the end of the kernel line in the /boot/grub/menu.lst file:```
noapic nolapic acpi=off
```But without knowing the error messages, I am just guessing...

---

### Post by Boneless on 2008-10-29
No "kernel panic" message, anyway I'll try doing as you suggested.

---

### Post by Boneless on 2008-10-31
OK, here are the last 8 lines of kernel messages (which I had to copy by hand on a piece of paper, since the system just freezes, forgive me so if I didn't copy out everything):

```

[9.00whatever] kernel_init+0x141/0x360
[9.00whatever] _switch_to+0xaa/0x1d0
[9.00whatever] schedule_tail+0x53/0x120
[9.00whatever] ret_from_fork+0x6/0x20
[9.00whatever] kernel_init+0x0/0x3b0
[9.00whatever] kernel_init+0x0/0x3b0
[9.00whatever] kernel_thread_helper+0x7/0x10
[9.00whatever] =============================

```

---

### Post by Boneless on 2008-11-01
bump

---

### Post by Boneless on 2008-11-01
bump again

---

### Post by Boneless on 2008-11-06
sblomp.

---

