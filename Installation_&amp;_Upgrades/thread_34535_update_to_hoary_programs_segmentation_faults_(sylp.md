---
title: "update to hoary: programs segmentation faults (sylpheed,xmms,gmplayer)"
date: 2005-05-15
forum: Installation &amp; Upgrades
---

### Post by pinnockio on 2005-05-15
Hello,

I recently updated from warthy to hoary.  Everything works fine, except for some programs that simply exit with a segmentation fault.  These include xmms, gmplayer and sylpheed (email program).  When looking to the forums, it seems that a lot of people have this problem because they own an nvidia-card.

- I'm NOT having an nvidia-card (but a radeon, using the radeon or ati driver).
- I'm running xorg as server
- when I run sylpheed in gdb this is the last line of output of the backtrace:
```
Cannot access memory at address 0xc0000000
```
- I strace sylpheed results in this (snippet of the last lines):
```
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libz.so.1", O_RDONLY)    = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\247\351"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=66480, ...}) = 0
old_mmap(0x49e99000, 68284, PROT_READ|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0x49e99000
old_mmap(0x49ea9000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 3, 0xf000) = 0x49ea9000
close(3)                                = 0
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f51000
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f50000
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++

```

Could somebody help me with these segmentation faults as they started to appear after the upgrade.  Any help is appreceated!

Kind regards,

A Belgian Ubuntu user
(form gentoo user)

---

### Post by pinnockio on 2005-05-22
Hello,

I wanted to install sylpheed manually.  So I went to freshmeat and followed the link for the debian installation package [http://packages.debian.org/stable/mail/sylpheed](http://packages.debian.org/stable/mail/sylpheed) .  There was a list with all the pacakges it depends on.  Well I tried to reinstall them using synaptic.  And guess what?  Now everything works! Gmplayer,xmms,sylpheed,... .

Kind regards

---

