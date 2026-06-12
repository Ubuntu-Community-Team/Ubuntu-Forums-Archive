---
title: "Kernel Patching doesn't seem to work for me."
date: 2016-12-31
forum: Installation &amp; Upgrades
---

### Post by forkenbrock on 2016-12-31
Hello, I'm trying to patch the "linux-4.4" kernel with "patches-4.4.38-rt49.tar.xz".  I used the following command to unzip and apply the patch:

xzcat ../patches-4.4.38-rt49.tar.xz | patch -p1

But I get about 500 of these messages.  I was under the impression that  4.4 means it's unpatched, but I keep seeing these messages about a  previous patch detected.

Edit: I also attempted to download 4.4.39 kernel and the patch.  I was able to reverse the patch, but when trying to apply the rt patch, the result is the same.

```

jaguar@jaguaraudiodesigncom:~/Documents/linux-4.4$ xzcat ../patches-4.4.38-rt49.tar.xz | patch -p1
patching file arch/x86/kernel/nmi.c
patching file arch/x86/kernel/reboot.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #1 succeeded at 718 (offset -8 lines).
Hunk #2 succeeded at 780 (offset -8 lines).
Hunk #3 succeeded at 788 (offset -8 lines).
patching file include/linux/kernel.h
Hunk #1 FAILED at 259.
Hunk #2 succeeded at 479 (offset 18 lines).
1 out of 2 hunks FAILED -- saving rejects to file include/linux/kernel.h.rej
patching file kernel/panic.c
Hunk #1 succeeded at 119 with fuzz 2 (offset 58 lines).
patching file kernel/watchdog.c
patching file kernel/stop_machine.c
Hunk #4 FAILED at 88.
Hunk #5 succeeded at 143 (offset 16 lines).
Hunk #6 FAILED at 226.
Hunk #7 FAILED at 237.
Hunk #8 succeeded at 302 with fuzz 2 (offset 16 lines).
Hunk #9 FAILED at 345.
Hunk #10 FAILED at 424.
Hunk #11 FAILED at 438.
Hunk #12 succeeded at 495 (offset 19 lines).
Hunk #13 FAILED at 538.
Hunk #14 succeeded at 663 (offset 21 lines).
7 out of 14 hunks FAILED -- saving rejects to file kernel/stop_machine.c.rej
patching file block/blk-mq.c
Hunk #1 succeeded at 1405 (offset -2 lines).
Hunk #2 succeeded at 1607 (offset -2 lines).
Hunk #3 succeeded at 1800 (offset -2 lines).
patching file block/blk-mq.h
patching file net/core/dev.c
Reversed (or previously applied) patch detected!  Assume -R? [n] 

```

---

### Post by forkenbrock on 2016-12-31
The problem was caused by the confusion created by having a patch file named "patches-4.4.38-rt49.tar.xz" and another named "patch-4.4.38-rt49.patch.xz" in the same folder.  The second file was the correct one and I patched the unpacked folder "linux-4.4.38" (not 4.4) without an issue.

---

