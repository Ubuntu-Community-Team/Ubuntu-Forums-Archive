---
title: "RTpatch to kernel"
date: 2016-01-07
forum: Installation &amp; Upgrades
---

### Post by latha2 on 2016-01-07
Dear all,
I have compiled and installed a kernel 4.1.6  for which i want to patch the kernel with " patches-4.1.15-rt17.tar.xz"
How to patch my 4.1.6 linux kernel with this Patches-4.1.15-rt17.tar.xz

I just had a try but it's showing like this 

Hunk #2 succeeded at 1231 (offset -8 lines).
patching file include/linux/work-simple.h
patching file kernel/sched/Makefile
Hunk #1 FAILED at 13.
1 out of 1 hunk FAILED -- saving rejects to file kernel/sched/Makefile.rej
patching file kernel/sched/work-simple.c
patching file kernel/sched/core.c
Hunk #1 succeeded at 1549 (offset 32 lines).
Hunk #2 succeeded at 1808 (offset 15 lines).
Hunk #3 FAILED at 2962.
Hunk #4 succeeded at 2666 with fuzz 2 (offset -342 lines).
Hunk #5 succeeded at 3292 (offset 268 lines).
Hunk #6 succeeded at 3306 (offset 268 lines).
1 out of 6 hunks FAILED -- saving rejects to file kernel/sched/core.c.rej
patching file kernel/workqueue.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #1 succeeded at 805 (offset 1 line).
Hunk #2 succeeded at 851 (offset 1 line).
Hunk #3 succeeded at 871 (offset 1 line).
patching file kernel/workqueue_internal.h
patching file kernel/sched/core.c
Hunk #1 succeeded at 3274 (offset 245 lines).
Hunk #2 succeeded at 3283 (offset 245 lines).
patching file kernel/workqueue.c
Hunk #1 succeeded at 122 (offset -1 lines).
Hunk #2 succeeded at 411 (offset 1 line).
Hunk #3 succeeded at 828 (offset 1 line).
Hunk #4 FAILED at 864.
Hunk #5 FAILED at 881.
Hunk #6 succeeded at 1597 (offset 7 lines).
Hunk #7 succeeded at 1632 (offset 7 lines).
Hunk #8 succeeded at 1802 (offset 7 lines).
2 out of 8 hunks FAILED -- saving rejects to file kernel/workqueue.c.rej
patching file kernel/workqueue.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #2 succeeded at 336 with fuzz 2 (offset 7 lines).
Hunk #3 succeeded at 1103 with fuzz 1 (offset 38 lines).
Hunk #4 succeeded at 1207 (offset 38 lines).
Hunk #5 succeeded at 1270 (offset 37 lines).
Hunk #6 succeeded at 1342 (offset 37 lines).
Hunk #7 succeeded at 1445 (offset 35 lines).
Hunk #8 succeeded at 1519 (offset 35 lines).
Hunk #9 succeeded at 1561 (offset 35 lines).
Hunk #10 succeeded at 2842 (offset 40 lines).
Hunk #11 succeeded at 2897 (offset 40 lines).
Hunk #12 succeeded at 2935 (offset 40 lines).
patching file kernel/workqueue.c
Hunk #1 succeeded at 130 (offset 5 lines).
Hunk #2 succeeded at 183 (offset 5 lines).
Hunk #3 succeeded at 212 (offset 5 lines).
Hunk #4 succeeded at 345 (offset 7 lines).
Hunk #5 succeeded at 364 (offset 7 lines).
Hunk #6 succeeded at 396 (offset 7 lines).
Hunk #7 succeeded at 583 (offset 32 lines).
Hunk #8 succeeded at 687 (offset 32 lines).
Hunk #9 succeeded at 1100 (offset 38 lines).
Hunk #10 succeeded at 1226 (offset 38 lines).
Hunk #11 FAILED at 1227.
Hunk #12 succeeded at 1351 (offset 40 lines).
Hunk #13 succeeded at 1409 (offset 40 lines).
Hunk #14 succeeded at 1426 (offset 40 lines).
Hunk #15 succeeded at 2721 (offset 46 lines).
Hunk #16 succeeded at 2755 (offset 46 lines).
Hunk #17 succeeded at 3197 (offset 46 lines).
Hunk #18 succeeded at 3251 (offset 46 lines).
Hunk #19 succeeded at 3357 (offset 46 lines).
Hunk #20 succeeded at 3970 (offset 46 lines).
Hunk #21 succeeded at 4063 (offset 46 lines).
Hunk #22 succeeded at 4075 (offset 46 lines).
Hunk #23 succeeded at 4102 (offset 46 lines).
Hunk #24 succeeded at 4299 (offset 46 lines).
Hunk #25 succeeded at 4350 (offset 46 lines).
Hunk #26 succeeded at 4700 (offset 46 lines).
Hunk #27 succeeded at 4823 (offset 46 lines).
Hunk #28 succeeded at 4832 (offset 46 lines).
1 out of 28 hunks FAILED -- saving rejects to file kernel/workqueue.c.rej
patching file arch/x86/include/asm/uv/uv_bau.h
patching file arch/x86/include/asm/uv/uv_hub.h
patching file arch/x86/kernel/apic/x2apic_uv_x.c
patching file arch/x86/platform/uv/tlb_uv.c
patching file arch/x86/platform/uv/uv_time.c
patching file arch/x86/crypto/aesni-intel_glue.c
patching file arch/x86/mm/iomap_32.c
patching file arch/x86/kernel/apic/io_apic.c
patching file arch/x86/kvm/x86.c
patching file arch/x86/kernel/cpu/mcheck/mce.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #9 succeeded at 2347 with fuzz 2 (offset 2 lines).
Hunk #10 succeeded at 2374 (offset 3 lines).
Hunk #11 succeeded at 2381 (offset 3 lines).
Hunk #12 succeeded at 2401 (offset 3 lines).
patching file arch/x86/kernel/cpu/mcheck/mce.c
Hunk #1 FAILED at 42.
Hunk #2 succeeded at 1357 (offset 13 lines).
Hunk #3 succeeded at 1414 (offset 13 lines).
Hunk #4 succeeded at 2483 (offset 15 lines).
1 out of 4 hunks FAILED -- saving rejects to file arch/x86/kernel/cpu/mcheck/mce.c.rej
patching file arch/x86/Kconfig
patching file arch/x86/include/asm/thread_info.h
patching file arch/x86/kernel/asm-offsets.c
patching file arch/x86/kernel/entry_32.S
patching file arch/x86/kernel/entry_64.S
patching file arch/x86/include/asm/signal.h
Hunk #1 succeeded at 58 (offset 26 lines).
patching file arch/x86/include/asm/stackprotector.h
patching file arch/x86/Kconfig
Hunk #1 succeeded at 204 (offset 1 line).
patching file fs/xfs/xfs_inode.c
patching file fs/xfs/xfs_inode.h
patch unexpectedly ends in middle of line
patch unexpectedly ends in middle of line
root@jntuh-Veriton-M670:/usr/src/linux-4.1.6# 

What shall I do now in order to make my patch work complete...
Where to correct the hunk failures?? What they mean ?
Thank you

---

