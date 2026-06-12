---
title: "Installation error."
date: 2011-12-11
forum: Installation &amp; Upgrades
---

### Post by nandomo on 2011-12-11
I installed ubuntu 11.10 last night on PC, ran all the updates, rebooted. Everything worked fine. I installed the lamp server and everything seemed fine. I restarted my computer and I got a screen where it wants me to boot linux 3.0 generic... When I try to reinstall ubuntu it gives me the following error.

```

Kernel panic - not syncing: Attempted to kill init!
Pid; l: comm: init Tainted: G W 3.0.0-12-generic #20-Ubuntu
Call Trace:
? printK+0x2d/0x02f
panic+0x5c/0x151
forget_original_parent+0x1e4/0x1f0
? _raw_spin_lock_irqsave+0x2d/0x40
exit_notify+0x13/0x140
? remove_vma+0x44/0x60
do_group_exit+0x38/0xa0
sys_exit_group+0x18/0x20
syscall_call+0x7/0xb
panic occurred switching back to text console
GPU lockup - switching to software fbcon
GPU lockup - switching to software fbcon 
```

Any help?

---

