---
title: "/sbin/init filesystem error"
date: 2013-08-21
forum: Installation &amp; Upgrades
---

### Post by x-david-o on 2013-08-21
I have been trying to fix this by reading some other posts but so far no luck. This is the error message I get:
Target filesystem doesn't have requested /sbin/init.
/bin/sh: 0: can't open ro
[    2.126294] Kernel panic - not syncing: Attemted to kill init!
[    2.126346] Pid: 1, comm: sh Not Tainted 3.2.0-51-generic-pae $77-Ubuntu
[    2.126392] call Trace:
[    2.126440] [<c1594ea6>] ? printk+0x5c/0x161
[    2.126485] [<c1594d74>] panic+0x5c/0x161
[    2.126529] [<c105e604>] forget_original_parent+0x1e4/0x1f0
[    2.126578] [<c10eb9e0>] ?perf_cgroup_attach_task+0x20/0x20
[    2.126624] [<c105e623>] exit_notify+0x13/0x100
[    2.126668] [<c105edbe>] do_exit+0X1AE/0X3C0
[    2.126713] [<c105f128>] do_group_exit+0x38/0xa0
[    2.126757] [<c105f1a8>] sys_exit_group+0x18/0x20
[    2.126803] [<c15b209f>] sysenter_do_call+-x12/0x28

After typing out that error message I booted up a live cd and tried running boot repair with no luck. I restarted my computer and got the same error message but with some different numbers.
Here is the boot [summary]("http://paste.ubuntu.com/6012367")

I have also tried checking the partition on gparted, and I have tried a couple different combos of fsck.

Any help is greatly appreciated.

---

