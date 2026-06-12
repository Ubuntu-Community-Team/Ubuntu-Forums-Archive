---
title: "Upgrade from 20.04 to 22.04 with mdadm raid1 failed - reboot kernel panic error"
date: 2024-02-25
forum: Installation &amp; Upgrades
---

### Post by ingpaolo on 2024-02-25
Hi everybody.
I've just tried to upgrade my Ubuntu 20.04 desktop with mdamd Raid 1 configuration, but the procedure failed to reboot and I had only a "Terminate session" command (not working at all).
So I've rebooted PC with reset button and find out, using recovery mode, an "end kernel panic - not syncing: VFS: unable to mount root fs in unknown-block(0,0)"

Few lines before this error message I can see another error 'VFS: cannot open root device "mapper/ubuntu--vg-root" or unknown-block (0,0): error -6'
Followed by 'Please append a correct "root=" boot option; here are the available partitions:'
'kernel panic ....'
'CPU: 2 PID: 1 Comm: swapper/0 Not tainted 5.4.0-172-generic #190-Ubuntu'
'Hardware name: to be filled by O.E.M. To be filled by O.E.M./SABERTOOTH 990FX R2.0, BIOS 2301 01/06/2014'
'Call trece:'
'dump_stack+0x6d/0x8b'
'panic+0x114/0x2f6'
'mount_block_root+0x23f/0x2e8'
'mount_root+0x38/0x3a'
'prepare_manespace+0x13f/0x194'
kernel_init_freeable+0x265/0x289'
'? rest_init+0xb0/0xb0'
'kernel_init+0xe/0x110'
'ret_from_fork+0x35/0x40'
'Kernel Offset: 0x34e00000 from 0xffffffff81000000 (relocation range: 0xffffffff80000000-0xffffffffbfffffff)'
and than the error mentioned at the beginning.

I've tried to use boot repair, but the error is still there.

Can anyone help me to "repair" my installation without reinstalling Ubuntu desktop?

May thanks to whoever will help me.

---

