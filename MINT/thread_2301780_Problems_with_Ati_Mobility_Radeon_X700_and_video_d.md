---
title: "Problems with Ati Mobility Radeon X700 and video driver"
date: 2015-11-05
forum: MINT
---

### Post by hardhu on 2015-11-05
Hello everybody,
I have a quite old notebook (2005) that has an Ati Mobility Radeon X700 as video card. I have a lot of problems with recent versions of Ubuntu/Mint, at the present time I am trying Linux Mint 17.2 Xfce, but since I go no support on Mint forums, I try to describe here my problem to see if anybody can help.
What is happening, is that, after a random period of time of usage, desktop becomes irresponsive, I can only move the mouse pointer, but I cannot click or use the keyboard anymore. Sometimes the screen goes blank several times before this happens. Sometimes I can ssh from another pc to reboot the laptop, sometimes even this fails.
What I get from the logs is the following:

- from /var/log/Xorg.0.log (only the relevant error messages)

```

(EE) [mi] EQ overflowing.  Additional events will be discarded until existing events are processed.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x48) [0x55ab6bd0d848]
(EE) 1: /usr/bin/X (mieqEnqueue+0x22b) [0x55ab6bcef83b]
(EE) 2: /usr/bin/X (QueuePointerEvents+0x52) [0x55ab6bbd0f72]
(EE) 3: /usr/bin/X (xf86PostMotionEvent+0xd6) [0x55ab6bc07046]
(EE) 4: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f568188d000+0x4e39) [0x7f5681891e39]
(EE) 5: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f568188d000+0x68e2) [0x7f56818938e2]
(EE) 6: /usr/bin/X (0x55ab6bb64000+0x93518) [0x55ab6bbf7518]
(EE) 7: /usr/bin/X (0x55ab6bb64000+0xbbc90) [0x55ab6bc1fc90]
(EE) 8: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f568aec2000+0x10340) [0x7f568aed2340]
(EE) 9: /lib/x86_64-linux-gnu/libc.so.6 (ioctl+0x7) [0x7f56899d2337]
(EE) 10: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmIoctl+0x34) [0x7f568acb9804]
(EE) 11: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmCommandWrite+0x1e) [0x7f568acbbe0e]
(EE) 12: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f5685619000+0x1bb9) [0x7f568561abb9]
(EE) 13: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f5685619000+0x1dbc) [0x7f568561adbc]
(EE) 14: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x7f5685826000+0x24d77) [0x7f568584ad77]
(EE) 15: /usr/lib/xorg/modules/libexa.so (0x7f56849a7000+0xacb0) [0x7f56849b1cb0]
(EE) 16: /usr/bin/X (0x55ab6bb64000+0x19a6d3) [0x55ab6bcfe6d3]
(EE) 17: /usr/bin/X (0x55ab6bb64000+0xe0cd5) [0x55ab6bc44cd5]
(EE) 18: /usr/bin/X (0x55ab6bb64000+0x533b6) [0x55ab6bbb73b6]
(EE) 19: /usr/bin/X (0x55ab6bb64000+0x55f0e) [0x55ab6bbb9f0e]
(EE) 20: /usr/bin/X (0x55ab6bb64000+0x59d9a) [0x55ab6bbbdd9a]
(EE) 21: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7f5689902ec5]
(EE) 22: /usr/bin/X (0x55ab6bb64000+0x451ee) [0x55ab6bba91ee]
(EE) 
(EE) [mi] These backtraces from mieqEnqueue may point to a culprit higher up the stack.
(EE) [mi] mieq is *NOT* the cause.  It is a victim.
(EE) [mi] EQ overflow continuing.  100 events have been dropped.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x48) [0x55ab6bd0d848]
(EE) 1: /usr/bin/X (QueuePointerEvents+0x52) [0x55ab6bbd0f72]
(EE) 2: /usr/bin/X (xf86PostMotionEvent+0xd6) [0x55ab6bc07046]
(EE) 3: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f568188d000+0x4e39) [0x7f5681891e39]
(EE) 4: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f568188d000+0x68e2) [0x7f56818938e2]
(EE) 5: /usr/bin/X (0x55ab6bb64000+0x93518) [0x55ab6bbf7518]
(EE) 6: /usr/bin/X (0x55ab6bb64000+0xbbc90) [0x55ab6bc1fc90]
(EE) 7: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f568aec2000+0x10340) [0x7f568aed2340]
(EE) 8: /lib/x86_64-linux-gnu/libc.so.6 (ioctl+0x7) [0x7f56899d2337]
(EE) 9: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmIoctl+0x34) [0x7f568acb9804]
(EE) 10: /usr/lib/x86_64-linux-gnu/libdrm.so.2 (drmCommandWrite+0x1e) [0x7f568acbbe0e]
(EE) 11: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f5685619000+0x1bb9) [0x7f568561abb9]
(EE) 12: /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1 (0x7f5685619000+0x1dbc) [0x7f568561adbc]
(EE) 13: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x7f5685826000+0x24d77) [0x7f568584ad77]
(EE) 14: /usr/lib/xorg/modules/libexa.so (0x7f56849a7000+0xacb0) [0x7f56849b1cb0]
(EE) 15: /usr/bin/X (0x55ab6bb64000+0x19a6d3) [0x55ab6bcfe6d3]
(EE) 16: /usr/bin/X (0x55ab6bb64000+0xe0cd5) [0x55ab6bc44cd5]
(EE) 17: /usr/bin/X (0x55ab6bb64000+0x533b6) [0x55ab6bbb73b6]
(EE) 18: /usr/bin/X (0x55ab6bb64000+0x55f0e) [0x55ab6bbb9f0e]
(EE) 19: /usr/bin/X (0x55ab6bb64000+0x59d9a) [0x55ab6bbbdd9a]
(EE) 20: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7f5689902ec5]
(EE) 21: /usr/bin/X (0x55ab6bb64000+0x451ee) [0x55ab6bba91ee]
(EE) 

```

- from /var/log/syslog (only the relevant parts):

```
Nov  4 20:43:27 eaglinux kernel: [34670.156082] radeon 0000:01:00.0: ring 0 stalled for more than 10236msec
Nov  4 20:43:27 eaglinux kernel: [34670.156098] radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000044cba last fence id 0x0000000000044d9a on ring 0)
Nov  4 20:43:27 eaglinux kernel: [34670.156124] radeon 0000:01:00.0: failed to get a new IB (-35)
Nov  4 20:43:27 eaglinux kernel: [34670.156216] [drm:radeon_cs_ioctl [radeon]] *ERROR* Failed to get ib !
Nov  4 20:43:27 eaglinux kernel: [34670.345523] Failed to wait GUI idle while programming pipes. Bad things might happen.
Nov  4 20:43:28 eaglinux kernel: [34670.347334] radeon 0000:01:00.0: Saved 7211 dwords of commands on ring 0.
Nov  4 20:43:28 eaglinux kernel: [34670.347352] radeon 0000:01:00.0: (r300_asic_reset:425) RBBM_STATUS=0x80010140
Nov  4 20:43:28 eaglinux kernel: [34670.848480] radeon 0000:01:00.0: (r300_asic_reset:444) RBBM_STATUS=0x80010140
Nov  4 20:43:28 eaglinux kernel: [34671.345597] radeon 0000:01:00.0: (r300_asic_reset:456) RBBM_STATUS=0x00000140
Nov  4 20:43:28 eaglinux kernel: [34671.345635] radeon 0000:01:00.0: GPU reset succeed
Nov  4 20:43:28 eaglinux kernel: [34671.345642] radeon 0000:01:00.0: GPU reset succeeded, trying to resume
Nov  4 20:43:28 eaglinux kernel: [34671.349719] radeon 0000:01:00.0: ffff880035e3b400 unpin not necessary
Nov  4 20:43:28 eaglinux kernel: [34671.361408] [drm] PCIE GART of 512M enabled (table at 0x00000000C8040000).
Nov  4 20:43:28 eaglinux kernel: [34671.361425] [drm] radeon: 2 quad pipes, 1 z pipes initialized.
Nov  4 20:43:28 eaglinux kernel: [34671.361434] radeon 0000:01:00.0: WB enabled
Nov  4 20:43:28 eaglinux kernel: [34671.361439] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x00000000a8000000 and cpu addr 0xffff8800359d4000
Nov  4 20:43:28 eaglinux kernel: [34671.361482] [drm] radeon: ring at 0x00000000A8001000
Nov  4 20:43:28 eaglinux kernel: [34671.361506] [drm] ring test succeeded in 2 usecs
Nov  4 20:43:29 eaglinux kernel: [34672.576037] [drm] ib test succeeded in 0 usecs
Nov  4 20:43:47 eaglinux kernel: [34690.436055] radeon 0000:01:00.0: ring 0 stalled for more than 10272msec
Nov  4 20:43:47 eaglinux kernel: [34690.436071] radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000044eac last fence id 0x0000000000044ead on ring 0)
Nov  4 20:43:47 eaglinux kernel: [34690.626920] Failed to wait GUI idle while programming pipes. Bad things might happen.
Nov  4 20:43:48 eaglinux kernel: [34690.628727] radeon 0000:01:00.0: Saved 75 dwords of commands on ring 0.
Nov  4 20:43:48 eaglinux kernel: [34690.628745] radeon 0000:01:00.0: (r300_asic_reset:425) RBBM_STATUS=0x80010140
Nov  4 20:43:48 eaglinux kernel: [34691.129880] radeon 0000:01:00.0: (r300_asic_reset:444) RBBM_STATUS=0x80010140
Nov  4 20:43:48 eaglinux kernel: [34691.626996] radeon 0000:01:00.0: (r300_asic_reset:456) RBBM_STATUS=0x00000140
Nov  4 20:43:48 eaglinux kernel: [34691.627035] radeon 0000:01:00.0: GPU reset succeed
Nov  4 20:43:48 eaglinux kernel: [34691.627041] radeon 0000:01:00.0: GPU reset succeeded, trying to resume
Nov  4 20:43:48 eaglinux kernel: [34691.632528] radeon 0000:01:00.0: ffff880035e3b400 unpin not necessary
Nov  4 20:43:49 eaglinux kernel: [34691.641399] [drm] PCIE GART of 512M enabled (table at 0x00000000C8040000).
Nov  4 20:43:49 eaglinux kernel: [34691.641417] [drm] radeon: 2 quad pipes, 1 z pipes initialized.
Nov  4 20:43:49 eaglinux kernel: [34691.641426] radeon 0000:01:00.0: WB enabled
Nov  4 20:43:49 eaglinux kernel: [34691.641431] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x00000000a8000000 and cpu addr 0xffff8800359d4000
Nov  4 20:43:49 eaglinux kernel: [34691.641449] [drm] radeon: ring at 0x00000000A8001000
Nov  4 20:43:49 eaglinux kernel: [34691.641471] [drm] ring test succeeded in 1 usecs
Nov  4 20:43:49 eaglinux kernel: [34692.857806] [drm] ib test succeeded in 0 usecs
Nov  4 20:44:01 eaglinux kernel: [34704.452093] radeon 0000:01:00.0: ring 0 stalled for more than 10236msec
Nov  4 20:44:01 eaglinux kernel: [34704.452108] radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000044f1d last fence id 0x0000000000044f38 on ring 0)
Nov  4 20:44:01 eaglinux kernel: [34704.642696] Failed to wait GUI idle while programming pipes. Bad things might happen.
Nov  4 20:44:02 eaglinux kernel: [34704.644823] radeon 0000:01:00.0: Saved 907 dwords of commands on ring 0.
Nov  4 20:44:02 eaglinux kernel: [34704.644842] radeon 0000:01:00.0: (r300_asic_reset:425) RBBM_STATUS=0x80010140
Nov  4 20:44:02 eaglinux kernel: [34705.145972] radeon 0000:01:00.0: (r300_asic_reset:444) RBBM_STATUS=0x80010140
Nov  4 20:44:02 eaglinux kernel: [34705.643079] radeon 0000:01:00.0: (r300_asic_reset:456) RBBM_STATUS=0x00000140
Nov  4 20:44:02 eaglinux kernel: [34705.643117] radeon 0000:01:00.0: GPU reset succeed
Nov  4 20:44:02 eaglinux kernel: [34705.643124] radeon 0000:01:00.0: GPU reset succeeded, trying to resume
Nov  4 20:44:02 eaglinux kernel: [34705.648917] radeon 0000:01:00.0: ffff880035e3b400 unpin not necessary
Nov  4 20:44:03 eaglinux kernel: [34705.657401] [drm] PCIE GART of 512M enabled (table at 0x00000000C8040000).
Nov  4 20:44:03 eaglinux kernel: [34705.657418] [drm] radeon: 2 quad pipes, 1 z pipes initialized.
Nov  4 20:44:03 eaglinux kernel: [34705.657428] radeon 0000:01:00.0: WB enabled
Nov  4 20:44:03 eaglinux kernel: [34705.657433] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x00000000a8000000 and cpu addr 0xffff8800359d4000
Nov  4 20:44:03 eaglinux kernel: [34705.657451] [drm] radeon: ring at 0x00000000A8001000
Nov  4 20:44:03 eaglinux kernel: [34705.657476] [drm] ring test succeeded in 2 usecs
Nov  4 20:44:03 eaglinux kernel: [34706.871087] [drm] ib test succeeded in 0 usecs
Nov  4 20:46:04 eaglinux kernel: [34827.568055] radeon 0000:01:00.0: ring 0 stalled for more than 10000msec
Nov  4 20:46:04 eaglinux kernel: [34827.568071] radeon 0000:01:00.0: GPU lockup (current fence id 0x0000000000045a76 last fence id 0x0000000000045aa0 on ring 0)
Nov  4 20:46:04 eaglinux kernel: [34827.755981] Failed to wait GUI idle while programming pipes. Bad things might happen.
Nov  4 20:46:05 eaglinux kernel: [34827.761696] radeon 0000:01:00.0: Saved 1291 dwords of commands on ring 0.
Nov  4 20:46:05 eaglinux kernel: [34827.761711] radeon 0000:01:00.0: (r300_asic_reset:425) RBBM_STATUS=0x80010140
Nov  4 20:46:05 eaglinux kernel: [34828.263147] radeon 0000:01:00.0: (r300_asic_reset:444) RBBM_STATUS=0x80010140
Nov  4 20:46:05 eaglinux kernel: [34828.760202] radeon 0000:01:00.0: (r300_asic_reset:456) RBBM_STATUS=0x00000140
Nov  4 20:46:05 eaglinux kernel: [34828.760229] radeon 0000:01:00.0: GPU reset succeed
Nov  4 20:46:05 eaglinux kernel: [34828.760233] radeon 0000:01:00.0: GPU reset succeeded, trying to resume
Nov  4 20:46:05 eaglinux kernel: [34828.762965] radeon 0000:01:00.0: ffff880035e3b400 unpin not necessary
Nov  4 20:46:06 eaglinux kernel: [34828.773504] [drm] PCIE GART of 512M enabled (table at 0x00000000C8040000).
Nov  4 20:46:06 eaglinux kernel: [34828.773522] [drm] radeon: 2 quad pipes, 1 z pipes initialized.
Nov  4 20:46:06 eaglinux kernel: [34828.773532] radeon 0000:01:00.0: WB enabled
Nov  4 20:46:06 eaglinux kernel: [34828.773538] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x00000000a8000000 and cpu addr 0xffff8800359d4000
Nov  4 20:46:06 eaglinux kernel: [34828.773557] [drm] radeon: ring at 0x00000000A8001000
Nov  4 20:46:06 eaglinux kernel: [34828.773583] [drm] ring test succeeded in 2 usecs
Nov  4 20:49:36 eaglinux kernel: [35040.096125] INFO: task Xorg:1151 blocked for more than 120 seconds.
Nov  4 20:49:36 eaglinux kernel: [35040.096140]       Not tainted 4.2.0-16-generic #19~14.04.1-Ubuntu
Nov  4 20:49:36 eaglinux kernel: [35040.096144] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov  4 20:49:36 eaglinux kernel: [35040.096150] Xorg            D ffff88007fc16640     0  1151   1128 0x00400004
Nov  4 20:49:36 eaglinux kernel: [35040.096161]  ffff8800792e3958 0000000000000086 ffffffff81c14500 ffff880078aacb00
Nov  4 20:49:36 eaglinux kernel: [35040.096169]  ffff880035883aa8 ffff8800792e4000 ffff8800792e3ad8 ffff88003590c000
Nov  4 20:49:36 eaglinux kernel: [35040.096176]  ffff8800792e3a70 ffff88003590d490 ffff8800792e3978 ffffffff817b6a77
Nov  4 20:49:36 eaglinux kernel: [35040.096183] Call Trace:
Nov  4 20:49:36 eaglinux kernel: [35040.096201]  [<ffffffff817b6a77>] schedule+0x37/0x80
Nov  4 20:49:36 eaglinux kernel: [35040.096211]  [<ffffffff817b9431>] schedule_timeout+0x201/0x2a0
Nov  4 20:49:36 eaglinux kernel: [35040.096220]  [<ffffffff810de79e>] ? internal_add_timer+0x7e/0x90
Nov  4 20:49:36 eaglinux kernel: [35040.096302]  [<ffffffffc01de886>] ? radeon_fence_process+0x16/0x40 [radeon]
Nov  4 20:49:36 eaglinux kernel: [35040.096358]  [<ffffffffc01deb1f>] radeon_fence_wait_seq_timeout.constprop.7+0x1ef/0x2c0 [radeon]
Nov  4 20:49:36 eaglinux kernel: [35040.096413]  [<ffffffffc01de782>] ? radeon_fence_emit+0x62/0x150 [radeon]
Nov  4 20:49:36 eaglinux kernel: [35040.096421]  [<ffffffff810b7340>] ? prepare_to_wait_event+0xf0/0xf0
Nov  4 20:49:36 eaglinux kernel: [35040.096476]  [<ffffffffc01deeab>] radeon_fence_wait+0x7b/0xb0 [radeon]
Nov  4 20:49:36 eaglinux kernel: [35040.096543]  [<ffffffffc0201c56>] r100_ib_test+0x186/0x270 [radeon]
Nov  4 20:49:36 eaglinux kernel: [35040.096617]  [<ffffffffc029d0b8>] radeon_ib_ring_tests+0x58/0xc0 [radeon]
Nov  4 20:49:36 eaglinux kernel: [35040.096667]  [<ffffffffc01c5ea3>] radeon_gpu_reset+0x223/0x310 [radeon]
Nov  4 20:49:36 eaglinux kernel: [35040.096721]  [<ffffffffc01de060>] ? radeon_fence_default_wait+0x130/0x130 [radeon]
Nov  4 20:49:36 eaglinux kernel: [35040.096784]  [<ffffffffc01f47be>] radeon_gem_handle_lockup.part.5+0xe/0x20 [radeon]
Nov  4 20:49:36 eaglinux kernel: [35040.096846]  [<ffffffffc01f56da>] radeon_gem_wait_idle_ioctl+0xca/0x130 [radeon]
Nov  4 20:49:36 eaglinux kernel: [35040.096895]  [<ffffffffc001e6c3>] drm_ioctl+0x363/0x680 [drm]
Nov  4 20:49:36 eaglinux kernel: [35040.096958]  [<ffffffffc01f5610>] ? radeon_gem_busy_ioctl+0xe0/0xe0 [radeon]
Nov  4 20:49:36 eaglinux kernel: [35040.096969]  [<ffffffff81085be6>] ? __set_current_blocked+0x36/0x60
Nov  4 20:49:36 eaglinux kernel: [35040.096979]  [<ffffffff8101f8ec>] ? fpu__activate_curr+0x3c/0x80
Nov  4 20:49:36 eaglinux kernel: [35040.096987]  [<ffffffff81085c95>] ? signal_setup_done+0x65/0xa0
Nov  4 20:49:36 eaglinux kernel: [35040.097036]  [<ffffffffc01c304b>] radeon_drm_ioctl+0x4b/0x80 [radeon]
Nov  4 20:49:36 eaglinux kernel: [35040.097045]  [<ffffffff811fd90d>] do_vfs_ioctl+0x2cd/0x4b0
Nov  4 20:49:36 eaglinux kernel: [35040.097054]  [<ffffffff81082b8f>] ? recalc_sigpending+0x1f/0x60
Nov  4 20:49:36 eaglinux kernel: [35040.097060]  [<ffffffff8102102d>] ? fpu__restore_sig+0x4d/0x60
Nov  4 20:49:36 eaglinux kernel: [35040.097069]  [<ffffffff811fdb69>] SyS_ioctl+0x79/0x90
Nov  4 20:49:36 eaglinux kernel: [35040.097078]  [<ffffffff81014fb6>] ? sys_rt_sigreturn+0xa6/0xc0
Nov  4 20:49:36 eaglinux kernel: [35040.097086]  [<ffffffff817ba2f2>] entry_SYSCALL_64_fastpath+0x16/0x75
Nov  4 20:51:36 eaglinux kernel: [35160.096112] INFO: task Xorg:1151 blocked for more than 120 seconds.
Nov  4 20:51:36 eaglinux kernel: [35160.096126]       Not tainted 4.2.0-16-generic #19~14.04.1-Ubuntu
Nov  4 20:51:36 eaglinux kernel: [35160.096130] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov  4 20:51:36 eaglinux kernel: [35160.096136] Xorg            D ffff88007fc16640     0  1151   1128 0x00400004
Nov  4 20:51:36 eaglinux kernel: [35160.096147]  ffff8800792e3958 0000000000000086 ffffffff81c14500 ffff880078aacb00
Nov  4 20:51:36 eaglinux kernel: [35160.096155]  ffff880035883aa8 ffff8800792e4000 ffff8800792e3ad8 ffff88003590c000
Nov  4 20:51:36 eaglinux kernel: [35160.096162]  ffff8800792e3a70 ffff88003590d490 ffff8800792e3978 ffffffff817b6a77
Nov  4 20:51:36 eaglinux kernel: [35160.096169] Call Trace:
Nov  4 20:51:36 eaglinux kernel: [35160.096187]  [<ffffffff817b6a77>] schedule+0x37/0x80
Nov  4 20:51:36 eaglinux kernel: [35160.096196]  [<ffffffff817b9431>] schedule_timeout+0x201/0x2a0
Nov  4 20:51:36 eaglinux kernel: [35160.096205]  [<ffffffff810de79e>] ? internal_add_timer+0x7e/0x90
Nov  4 20:51:36 eaglinux kernel: [35160.096286]  [<ffffffffc01de886>] ? radeon_fence_process+0x16/0x40 [radeon]
Nov  4 20:51:36 eaglinux kernel: [35160.096342]  [<ffffffffc01deb1f>] radeon_fence_wait_seq_timeout.constprop.7+0x1ef/0x2c0 [radeon]
Nov  4 20:51:36 eaglinux kernel: [35160.096397]  [<ffffffffc01de782>] ? radeon_fence_emit+0x62/0x150 [radeon]
Nov  4 20:51:36 eaglinux kernel: [35160.096405]  [<ffffffff810b7340>] ? prepare_to_wait_event+0xf0/0xf0
Nov  4 20:51:36 eaglinux kernel: [35160.096460]  [<ffffffffc01deeab>] radeon_fence_wait+0x7b/0xb0 [radeon]
Nov  4 20:51:36 eaglinux kernel: [35160.096527]  [<ffffffffc0201c56>] r100_ib_test+0x186/0x270 [radeon]
Nov  4 20:51:36 eaglinux kernel: [35160.096601]  [<ffffffffc029d0b8>] radeon_ib_ring_tests+0x58/0xc0 [radeon]
Nov  4 20:51:36 eaglinux kernel: [35160.096650]  [<ffffffffc01c5ea3>] radeon_gpu_reset+0x223/0x310 [radeon]
Nov  4 20:51:36 eaglinux kernel: [35160.096704]  [<ffffffffc01de060>] ? radeon_fence_default_wait+0x130/0x130 [radeon]
Nov  4 20:51:36 eaglinux kernel: [35160.096767]  [<ffffffffc01f47be>] radeon_gem_handle_lockup.part.5+0xe/0x20 [radeon]
Nov  4 20:51:36 eaglinux kernel: [35160.096830]  [<ffffffffc01f56da>] radeon_gem_wait_idle_ioctl+0xca/0x130 [radeon]
Nov  4 20:51:36 eaglinux kernel: [35160.096879]  [<ffffffffc001e6c3>] drm_ioctl+0x363/0x680 [drm]
Nov  4 20:51:36 eaglinux kernel: [35160.096942]  [<ffffffffc01f5610>] ? radeon_gem_busy_ioctl+0xe0/0xe0 [radeon]
Nov  4 20:51:36 eaglinux kernel: [35160.096953]  [<ffffffff81085be6>] ? __set_current_blocked+0x36/0x60
Nov  4 20:51:36 eaglinux kernel: [35160.096963]  [<ffffffff8101f8ec>] ? fpu__activate_curr+0x3c/0x80
Nov  4 20:51:36 eaglinux kernel: [35160.096971]  [<ffffffff81085c95>] ? signal_setup_done+0x65/0xa0
Nov  4 20:51:36 eaglinux kernel: [35160.097020]  [<ffffffffc01c304b>] radeon_drm_ioctl+0x4b/0x80 [radeon]
Nov  4 20:51:36 eaglinux kernel: [35160.097029]  [<ffffffff811fd90d>] do_vfs_ioctl+0x2cd/0x4b0
Nov  4 20:51:36 eaglinux kernel: [35160.097037]  [<ffffffff81082b8f>] ? recalc_sigpending+0x1f/0x60
Nov  4 20:51:36 eaglinux kernel: [35160.097044]  [<ffffffff8102102d>] ? fpu__restore_sig+0x4d/0x60
Nov  4 20:51:36 eaglinux kernel: [35160.097052]  [<ffffffff811fdb69>] SyS_ioctl+0x79/0x90
Nov  4 20:51:36 eaglinux kernel: [35160.097062]  [<ffffffff81014fb6>] ? sys_rt_sigreturn+0xa6/0xc0
Nov  4 20:51:36 eaglinux kernel: [35160.097070]  [<ffffffff817ba2f2>] entry_SYSCALL_64_fastpath+0x16/0x75
Nov  4 20:53:36 eaglinux kernel: [35280.096111] INFO: task Xorg:1151 blocked for more than 120 seconds.
Nov  4 20:53:36 eaglinux kernel: [35280.096125]       Not tainted 4.2.0-16-generic #19~14.04.1-Ubuntu
Nov  4 20:53:36 eaglinux kernel: [35280.096130] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov  4 20:53:36 eaglinux kernel: [35280.096135] Xorg            D ffff88007fc16640     0  1151   1128 0x00400004
Nov  4 20:53:36 eaglinux kernel: [35280.096147]  ffff8800792e3958 0000000000000086 ffffffff81c14500 ffff880078aacb00
Nov  4 20:53:36 eaglinux kernel: [35280.096155]  ffff880035883aa8 ffff8800792e4000 ffff8800792e3ad8 ffff88003590c000
Nov  4 20:53:36 eaglinux kernel: [35280.096162]  ffff8800792e3a70 ffff88003590d490 ffff8800792e3978 ffffffff817b6a77
Nov  4 20:53:36 eaglinux kernel: [35280.096169] Call Trace:
Nov  4 20:53:36 eaglinux kernel: [35280.096187]  [<ffffffff817b6a77>] schedule+0x37/0x80
Nov  4 20:53:36 eaglinux kernel: [35280.096197]  [<ffffffff817b9431>] schedule_timeout+0x201/0x2a0
Nov  4 20:53:36 eaglinux kernel: [35280.096205]  [<ffffffff810de79e>] ? internal_add_timer+0x7e/0x90
Nov  4 20:53:36 eaglinux kernel: [35280.096287]  [<ffffffffc01de886>] ? radeon_fence_process+0x16/0x40 [radeon]
Nov  4 20:53:36 eaglinux kernel: [35280.096354]  [<ffffffffc01deb1f>] radeon_fence_wait_seq_timeout.constprop.7+0x1ef/0x2c0 [radeon]
Nov  4 20:53:36 eaglinux kernel: [35280.096409]  [<ffffffffc01de782>] ? radeon_fence_emit+0x62/0x150 [radeon]
Nov  4 20:53:36 eaglinux kernel: [35280.096417]  [<ffffffff810b7340>] ? prepare_to_wait_event+0xf0/0xf0
Nov  4 20:53:36 eaglinux kernel: [35280.096472]  [<ffffffffc01deeab>] radeon_fence_wait+0x7b/0xb0 [radeon]
Nov  4 20:53:36 eaglinux kernel: [35280.096539]  [<ffffffffc0201c56>] r100_ib_test+0x186/0x270 [radeon]
Nov  4 20:53:36 eaglinux kernel: [35280.096613]  [<ffffffffc029d0b8>] radeon_ib_ring_tests+0x58/0xc0 [radeon]
Nov  4 20:53:36 eaglinux kernel: [35280.096663]  [<ffffffffc01c5ea3>] radeon_gpu_reset+0x223/0x310 [radeon]
Nov  4 20:53:36 eaglinux kernel: [35280.096717]  [<ffffffffc01de060>] ? radeon_fence_default_wait+0x130/0x130 [radeon]
Nov  4 20:53:36 eaglinux kernel: [35280.096780]  [<ffffffffc01f47be>] radeon_gem_handle_lockup.part.5+0xe/0x20 [radeon]
Nov  4 20:53:36 eaglinux kernel: [35280.096842]  [<ffffffffc01f56da>] radeon_gem_wait_idle_ioctl+0xca/0x130 [radeon]
Nov  4 20:53:36 eaglinux kernel: [35280.096891]  [<ffffffffc001e6c3>] drm_ioctl+0x363/0x680 [drm]
Nov  4 20:53:36 eaglinux kernel: [35280.096954]  [<ffffffffc01f5610>] ? radeon_gem_busy_ioctl+0xe0/0xe0 [radeon]
Nov  4 20:53:36 eaglinux kernel: [35280.096965]  [<ffffffff81085be6>] ? __set_current_blocked+0x36/0x60
Nov  4 20:53:36 eaglinux kernel: [35280.096975]  [<ffffffff8101f8ec>] ? fpu__activate_curr+0x3c/0x80
Nov  4 20:53:36 eaglinux kernel: [35280.096983]  [<ffffffff81085c95>] ? signal_setup_done+0x65/0xa0
Nov  4 20:53:36 eaglinux kernel: [35280.097032]  [<ffffffffc01c304b>] radeon_drm_ioctl+0x4b/0x80 [radeon]
Nov  4 20:53:36 eaglinux kernel: [35280.097041]  [<ffffffff811fd90d>] do_vfs_ioctl+0x2cd/0x4b0
Nov  4 20:53:36 eaglinux kernel: [35280.097050]  [<ffffffff81082b8f>] ? recalc_sigpending+0x1f/0x60
Nov  4 20:53:36 eaglinux kernel: [35280.097056]  [<ffffffff8102102d>] ? fpu__restore_sig+0x4d/0x60
Nov  4 20:53:36 eaglinux kernel: [35280.097064]  [<ffffffff811fdb69>] SyS_ioctl+0x79/0x90
Nov  4 20:53:36 eaglinux kernel: [35280.097074]  [<ffffffff81014fb6>] ? sys_rt_sigreturn+0xa6/0xc0
Nov  4 20:53:36 eaglinux kernel: [35280.097082]  [<ffffffff817ba2f2>] entry_SYSCALL_64_fastpath+0x16/0x75
Nov  4 20:55:36 eaglinux kernel: [35400.096110] INFO: task Xorg:1151 blocked for more than 120 seconds.
Nov  4 20:55:36 eaglinux kernel: [35400.096124]       Not tainted 4.2.0-16-generic #19~14.04.1-Ubuntu
Nov  4 20:55:36 eaglinux kernel: [35400.096128] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov  4 20:55:36 eaglinux kernel: [35400.096134] Xorg            D ffff88007fc16640     0  1151   1128 0x00400004
Nov  4 20:55:36 eaglinux kernel: [35400.096145]  ffff8800792e3958 0000000000000086 ffffffff81c14500 ffff880078aacb00
Nov  4 20:55:36 eaglinux kernel: [35400.096153]  ffff880035883aa8 ffff8800792e4000 ffff8800792e3ad8 ffff88003590c000
Nov  4 20:55:36 eaglinux kernel: [35400.096161]  ffff8800792e3a70 ffff88003590d490 ffff8800792e3978 ffffffff817b6a77
Nov  4 20:55:36 eaglinux kernel: [35400.096167] Call Trace:
Nov  4 20:55:36 eaglinux kernel: [35400.096185]  [<ffffffff817b6a77>] schedule+0x37/0x80
Nov  4 20:55:36 eaglinux kernel: [35400.096195]  [<ffffffff817b9431>] schedule_timeout+0x201/0x2a0
Nov  4 20:55:36 eaglinux kernel: [35400.096204]  [<ffffffff810de79e>] ? internal_add_timer+0x7e/0x90
Nov  4 20:55:36 eaglinux kernel: [35400.096285]  [<ffffffffc01de886>] ? radeon_fence_process+0x16/0x40 [radeon]
Nov  4 20:55:36 eaglinux kernel: [35400.096341]  [<ffffffffc01deb1f>] radeon_fence_wait_seq_timeout.constprop.7+0x1ef/0x2c0 [radeon]
Nov  4 20:55:36 eaglinux kernel: [35400.096396]  [<ffffffffc01de782>] ? radeon_fence_emit+0x62/0x150 [radeon]
Nov  4 20:55:36 eaglinux kernel: [35400.096404]  [<ffffffff810b7340>] ? prepare_to_wait_event+0xf0/0xf0
Nov  4 20:55:36 eaglinux kernel: [35400.096459]  [<ffffffffc01deeab>] radeon_fence_wait+0x7b/0xb0 [radeon]
Nov  4 20:55:36 eaglinux kernel: [35400.096526]  [<ffffffffc0201c56>] r100_ib_test+0x186/0x270 [radeon]
Nov  4 20:55:36 eaglinux kernel: [35400.096600]  [<ffffffffc029d0b8>] radeon_ib_ring_tests+0x58/0xc0 [radeon]
Nov  4 20:55:36 eaglinux kernel: [35400.096650]  [<ffffffffc01c5ea3>] radeon_gpu_reset+0x223/0x310 [radeon]
Nov  4 20:55:36 eaglinux kernel: [35400.096704]  [<ffffffffc01de060>] ? radeon_fence_default_wait+0x130/0x130 [radeon]
Nov  4 20:55:36 eaglinux kernel: [35400.096767]  [<ffffffffc01f47be>] radeon_gem_handle_lockup.part.5+0xe/0x20 [radeon]
Nov  4 20:55:36 eaglinux kernel: [35400.096829]  [<ffffffffc01f56da>] radeon_gem_wait_idle_ioctl+0xca/0x130 [radeon]
Nov  4 20:55:36 eaglinux kernel: [35400.096878]  [<ffffffffc001e6c3>] drm_ioctl+0x363/0x680 [drm]
Nov  4 20:55:36 eaglinux kernel: [35400.096941]  [<ffffffffc01f5610>] ? radeon_gem_busy_ioctl+0xe0/0xe0 [radeon]
Nov  4 20:55:36 eaglinux kernel: [35400.096952]  [<ffffffff81085be6>] ? __set_current_blocked+0x36/0x60
Nov  4 20:55:36 eaglinux kernel: [35400.096962]  [<ffffffff8101f8ec>] ? fpu__activate_curr+0x3c/0x80
Nov  4 20:55:36 eaglinux kernel: [35400.096970]  [<ffffffff81085c95>] ? signal_setup_done+0x65/0xa0
Nov  4 20:55:36 eaglinux kernel: [35400.097019]  [<ffffffffc01c304b>] radeon_drm_ioctl+0x4b/0x80 [radeon]
Nov  4 20:55:36 eaglinux kernel: [35400.097029]  [<ffffffff811fd90d>] do_vfs_ioctl+0x2cd/0x4b0
Nov  4 20:55:36 eaglinux kernel: [35400.097037]  [<ffffffff81082b8f>] ? recalc_sigpending+0x1f/0x60
Nov  4 20:55:36 eaglinux kernel: [35400.097044]  [<ffffffff8102102d>] ? fpu__restore_sig+0x4d/0x60
Nov  4 20:55:36 eaglinux kernel: [35400.097052]  [<ffffffff811fdb69>] SyS_ioctl+0x79/0x90
Nov  4 20:55:36 eaglinux kernel: [35400.097061]  [<ffffffff81014fb6>] ? sys_rt_sigreturn+0xa6/0xc0
Nov  4 20:55:36 eaglinux kernel: [35400.097069]  [<ffffffff817ba2f2>] entry_SYSCALL_64_fastpath+0x16/0x75
Nov  4 20:57:36 eaglinux kernel: [35520.096112] INFO: task Xorg:1151 blocked for more than 120 seconds.
Nov  4 20:57:36 eaglinux kernel: [35520.096126]       Not tainted 4.2.0-16-generic #19~14.04.1-Ubuntu
Nov  4 20:57:36 eaglinux kernel: [35520.096130] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov  4 20:57:36 eaglinux kernel: [35520.096135] Xorg            D ffff88007fc16640     0  1151   1128 0x00400004
Nov  4 20:57:36 eaglinux kernel: [35520.096147]  ffff8800792e3958 0000000000000086 ffffffff81c14500 ffff880078aacb00
Nov  4 20:57:36 eaglinux kernel: [35520.096155]  ffff880035883aa8 ffff8800792e4000 ffff8800792e3ad8 ffff88003590c000
Nov  4 20:57:36 eaglinux kernel: [35520.096162]  ffff8800792e3a70 ffff88003590d490 ffff8800792e3978 ffffffff817b6a77
Nov  4 20:57:36 eaglinux kernel: [35520.096169] Call Trace:
Nov  4 20:57:36 eaglinux kernel: [35520.096188]  [<ffffffff817b6a77>] schedule+0x37/0x80
Nov  4 20:57:36 eaglinux kernel: [35520.096198]  [<ffffffff817b9431>] schedule_timeout+0x201/0x2a0
Nov  4 20:57:36 eaglinux kernel: [35520.096206]  [<ffffffff810de79e>] ? internal_add_timer+0x7e/0x90
Nov  4 20:57:36 eaglinux kernel: [35520.096289]  [<ffffffffc01de886>] ? radeon_fence_process+0x16/0x40 [radeon]
Nov  4 20:57:36 eaglinux kernel: [35520.096345]  [<ffffffffc01deb1f>] radeon_fence_wait_seq_timeout.constprop.7+0x1ef/0x2c0 [radeon]
Nov  4 20:57:36 eaglinux kernel: [35520.096399]  [<ffffffffc01de782>] ? radeon_fence_emit+0x62/0x150 [radeon]
Nov  4 20:57:36 eaglinux kernel: [35520.096407]  [<ffffffff810b7340>] ? prepare_to_wait_event+0xf0/0xf0
Nov  4 20:57:36 eaglinux kernel: [35520.096462]  [<ffffffffc01deeab>] radeon_fence_wait+0x7b/0xb0 [radeon]
Nov  4 20:57:36 eaglinux kernel: [35520.096530]  [<ffffffffc0201c56>] r100_ib_test+0x186/0x270 [radeon]
Nov  4 20:57:36 eaglinux kernel: [35520.096603]  [<ffffffffc029d0b8>] radeon_ib_ring_tests+0x58/0xc0 [radeon]
Nov  4 20:57:36 eaglinux kernel: [35520.096653]  [<ffffffffc01c5ea3>] radeon_gpu_reset+0x223/0x310 [radeon]
Nov  4 20:57:36 eaglinux kernel: [35520.096707]  [<ffffffffc01de060>] ? radeon_fence_default_wait+0x130/0x130 [radeon]
Nov  4 20:57:36 eaglinux kernel: [35520.096770]  [<ffffffffc01f47be>] radeon_gem_handle_lockup.part.5+0xe/0x20 [radeon]
Nov  4 20:57:36 eaglinux kernel: [35520.096832]  [<ffffffffc01f56da>] radeon_gem_wait_idle_ioctl+0xca/0x130 [radeon]
Nov  4 20:57:36 eaglinux kernel: [35520.096881]  [<ffffffffc001e6c3>] drm_ioctl+0x363/0x680 [drm]
Nov  4 20:57:36 eaglinux kernel: [35520.096944]  [<ffffffffc01f5610>] ? radeon_gem_busy_ioctl+0xe0/0xe0 [radeon]
Nov  4 20:57:36 eaglinux kernel: [35520.096956]  [<ffffffff81085be6>] ? __set_current_blocked+0x36/0x60
Nov  4 20:57:36 eaglinux kernel: [35520.096966]  [<ffffffff8101f8ec>] ? fpu__activate_curr+0x3c/0x80
Nov  4 20:57:36 eaglinux kernel: [35520.096974]  [<ffffffff81085c95>] ? signal_setup_done+0x65/0xa0
Nov  4 20:57:36 eaglinux kernel: [35520.097022]  [<ffffffffc01c304b>] radeon_drm_ioctl+0x4b/0x80 [radeon]
Nov  4 20:57:36 eaglinux kernel: [35520.097032]  [<ffffffff811fd90d>] do_vfs_ioctl+0x2cd/0x4b0
Nov  4 20:57:36 eaglinux kernel: [35520.097040]  [<ffffffff81082b8f>] ? recalc_sigpending+0x1f/0x60
Nov  4 20:57:36 eaglinux kernel: [35520.097047]  [<ffffffff8102102d>] ? fpu__restore_sig+0x4d/0x60
Nov  4 20:57:36 eaglinux kernel: [35520.097055]  [<ffffffff811fdb69>] SyS_ioctl+0x79/0x90
Nov  4 20:57:36 eaglinux kernel: [35520.097065]  [<ffffffff81014fb6>] ? sys_rt_sigreturn+0xa6/0xc0
Nov  4 20:57:36 eaglinux kernel: [35520.097072]  [<ffffffff817ba2f2>] entry_SYSCALL_64_fastpath+0x16/0x75
Nov  4 20:59:36 eaglinux kernel: [35640.096114] INFO: task Xorg:1151 blocked for more than 120 seconds.
Nov  4 20:59:36 eaglinux kernel: [35640.096127]       Not tainted 4.2.0-16-generic #19~14.04.1-Ubuntu
Nov  4 20:59:36 eaglinux kernel: [35640.096132] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov  4 20:59:36 eaglinux kernel: [35640.096137] Xorg            D ffff88007fc16640     0  1151   1128 0x00400004
Nov  4 20:59:36 eaglinux kernel: [35640.096149]  ffff8800792e3958 0000000000000086 ffffffff81c14500 ffff880078aacb00
Nov  4 20:59:36 eaglinux kernel: [35640.096157]  ffff880035883aa8 ffff8800792e4000 ffff8800792e3ad8 ffff88003590c000
Nov  4 20:59:36 eaglinux kernel: [35640.096164]  ffff8800792e3a70 ffff88003590d490 ffff8800792e3978 ffffffff817b6a77
Nov  4 20:59:36 eaglinux kernel: [35640.096171] Call Trace:
Nov  4 20:59:36 eaglinux kernel: [35640.096189]  [<ffffffff817b6a77>] schedule+0x37/0x80
Nov  4 20:59:36 eaglinux kernel: [35640.096199]  [<ffffffff817b9431>] schedule_timeout+0x201/0x2a0
Nov  4 20:59:36 eaglinux kernel: [35640.096207]  [<ffffffff810de79e>] ? internal_add_timer+0x7e/0x90
Nov  4 20:59:36 eaglinux kernel: [35640.096289]  [<ffffffffc01de886>] ? radeon_fence_process+0x16/0x40 [radeon]
Nov  4 20:59:36 eaglinux kernel: [35640.096346]  [<ffffffffc01deb1f>] radeon_fence_wait_seq_timeout.constprop.7+0x1ef/0x2c0 [radeon]
Nov  4 20:59:36 eaglinux kernel: [35640.096400]  [<ffffffffc01de782>] ? radeon_fence_emit+0x62/0x150 [radeon]
Nov  4 20:59:36 eaglinux kernel: [35640.096408]  [<ffffffff810b7340>] ? prepare_to_wait_event+0xf0/0xf0
Nov  4 20:59:36 eaglinux kernel: [35640.096463]  [<ffffffffc01deeab>] radeon_fence_wait+0x7b/0xb0 [radeon]
Nov  4 20:59:36 eaglinux kernel: [35640.096530]  [<ffffffffc0201c56>] r100_ib_test+0x186/0x270 [radeon]
Nov  4 20:59:36 eaglinux kernel: [35640.096604]  [<ffffffffc029d0b8>] radeon_ib_ring_tests+0x58/0xc0 [radeon]
Nov  4 20:59:36 eaglinux kernel: [35640.096654]  [<ffffffffc01c5ea3>] radeon_gpu_reset+0x223/0x310 [radeon]
Nov  4 20:59:36 eaglinux kernel: [35640.096708]  [<ffffffffc01de060>] ? radeon_fence_default_wait+0x130/0x130 [radeon]
Nov  4 20:59:36 eaglinux kernel: [35640.096771]  [<ffffffffc01f47be>] radeon_gem_handle_lockup.part.5+0xe/0x20 [radeon]
Nov  4 20:59:36 eaglinux kernel: [35640.096833]  [<ffffffffc01f56da>] radeon_gem_wait_idle_ioctl+0xca/0x130 [radeon]
Nov  4 20:59:36 eaglinux kernel: [35640.096882]  [<ffffffffc001e6c3>] drm_ioctl+0x363/0x680 [drm]
Nov  4 20:59:36 eaglinux kernel: [35640.096945]  [<ffffffffc01f5610>] ? radeon_gem_busy_ioctl+0xe0/0xe0 [radeon]
Nov  4 20:59:36 eaglinux kernel: [35640.096957]  [<ffffffff81085be6>] ? __set_current_blocked+0x36/0x60
Nov  4 20:59:36 eaglinux kernel: [35640.096966]  [<ffffffff8101f8ec>] ? fpu__activate_curr+0x3c/0x80
Nov  4 20:59:36 eaglinux kernel: [35640.096974]  [<ffffffff81085c95>] ? signal_setup_done+0x65/0xa0
Nov  4 20:59:36 eaglinux kernel: [35640.097023]  [<ffffffffc01c304b>] radeon_drm_ioctl+0x4b/0x80 [radeon]
Nov  4 20:59:36 eaglinux kernel: [35640.097033]  [<ffffffff811fd90d>] do_vfs_ioctl+0x2cd/0x4b0
Nov  4 20:59:36 eaglinux kernel: [35640.097041]  [<ffffffff81082b8f>] ? recalc_sigpending+0x1f/0x60
Nov  4 20:59:36 eaglinux kernel: [35640.097048]  [<ffffffff8102102d>] ? fpu__restore_sig+0x4d/0x60
Nov  4 20:59:36 eaglinux kernel: [35640.097056]  [<ffffffff811fdb69>] SyS_ioctl+0x79/0x90
Nov  4 20:59:36 eaglinux kernel: [35640.097066]  [<ffffffff81014fb6>] ? sys_rt_sigreturn+0xa6/0xc0
Nov  4 20:59:36 eaglinux kernel: [35640.097073]  [<ffffffff817ba2f2>] entry_SYSCALL_64_fastpath+0x16/0x75
Nov  4 21:01:36 eaglinux kernel: [35760.096115] INFO: task Xorg:1151 blocked for more than 120 seconds.
Nov  4 21:01:36 eaglinux kernel: [35760.096129]       Not tainted 4.2.0-16-generic #19~14.04.1-Ubuntu
Nov  4 21:01:36 eaglinux kernel: [35760.096133] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov  4 21:01:36 eaglinux kernel: [35760.096138] Xorg            D ffff88007fc16640     0  1151   1128 0x00400004
Nov  4 21:01:36 eaglinux kernel: [35760.096150]  ffff8800792e3958 0000000000000086 ffffffff81c14500 ffff880078aacb00
Nov  4 21:01:36 eaglinux kernel: [35760.096158]  ffff880035883aa8 ffff8800792e4000 ffff8800792e3ad8 ffff88003590c000
Nov  4 21:01:36 eaglinux kernel: [35760.096165]  ffff8800792e3a70 ffff88003590d490 ffff8800792e3978 ffffffff817b6a77
Nov  4 21:01:36 eaglinux kernel: [35760.096172] Call Trace:
Nov  4 21:01:36 eaglinux kernel: [35760.096190]  [<ffffffff817b6a77>] schedule+0x37/0x80
Nov  4 21:01:36 eaglinux kernel: [35760.096200]  [<ffffffff817b9431>] schedule_timeout+0x201/0x2a0
Nov  4 21:01:36 eaglinux kernel: [35760.096208]  [<ffffffff810de79e>] ? internal_add_timer+0x7e/0x90
Nov  4 21:01:36 eaglinux kernel: [35760.096291]  [<ffffffffc01de886>] ? radeon_fence_process+0x16/0x40 [radeon]
Nov  4 21:01:36 eaglinux kernel: [35760.096347]  [<ffffffffc01deb1f>] radeon_fence_wait_seq_timeout.constprop.7+0x1ef/0x2c0 [radeon]
Nov  4 21:01:36 eaglinux kernel: [35760.096402]  [<ffffffffc01de782>] ? radeon_fence_emit+0x62/0x150 [radeon]
Nov  4 21:01:36 eaglinux kernel: [35760.096410]  [<ffffffff810b7340>] ? prepare_to_wait_event+0xf0/0xf0
Nov  4 21:01:36 eaglinux kernel: [35760.096465]  [<ffffffffc01deeab>] radeon_fence_wait+0x7b/0xb0 [radeon]
Nov  4 21:01:36 eaglinux kernel: [35760.096532]  [<ffffffffc0201c56>] r100_ib_test+0x186/0x270 [radeon]
Nov  4 21:01:36 eaglinux kernel: [35760.096606]  [<ffffffffc029d0b8>] radeon_ib_ring_tests+0x58/0xc0 [radeon]
Nov  4 21:01:36 eaglinux kernel: [35760.096656]  [<ffffffffc01c5ea3>] radeon_gpu_reset+0x223/0x310 [radeon]
Nov  4 21:01:36 eaglinux kernel: [35760.096710]  [<ffffffffc01de060>] ? radeon_fence_default_wait+0x130/0x130 [radeon]
Nov  4 21:01:36 eaglinux kernel: [35760.096773]  [<ffffffffc01f47be>] radeon_gem_handle_lockup.part.5+0xe/0x20 [radeon]
Nov  4 21:01:36 eaglinux kernel: [35760.096835]  [<ffffffffc01f56da>] radeon_gem_wait_idle_ioctl+0xca/0x130 [radeon]
Nov  4 21:01:36 eaglinux kernel: [35760.096883]  [<ffffffffc001e6c3>] drm_ioctl+0x363/0x680 [drm]
Nov  4 21:01:36 eaglinux kernel: [35760.096946]  [<ffffffffc01f5610>] ? radeon_gem_busy_ioctl+0xe0/0xe0 [radeon]
Nov  4 21:01:36 eaglinux kernel: [35760.096958]  [<ffffffff81085be6>] ? __set_current_blocked+0x36/0x60
Nov  4 21:01:36 eaglinux kernel: [35760.096968]  [<ffffffff8101f8ec>] ? fpu__activate_curr+0x3c/0x80
Nov  4 21:01:36 eaglinux kernel: [35760.096975]  [<ffffffff81085c95>] ? signal_setup_done+0x65/0xa0
Nov  4 21:01:36 eaglinux kernel: [35760.097024]  [<ffffffffc01c304b>] radeon_drm_ioctl+0x4b/0x80 [radeon]
Nov  4 21:01:36 eaglinux kernel: [35760.097034]  [<ffffffff811fd90d>] do_vfs_ioctl+0x2cd/0x4b0
Nov  4 21:01:36 eaglinux kernel: [35760.097042]  [<ffffffff81082b8f>] ? recalc_sigpending+0x1f/0x60
Nov  4 21:01:36 eaglinux kernel: [35760.097049]  [<ffffffff8102102d>] ? fpu__restore_sig+0x4d/0x60
Nov  4 21:01:36 eaglinux kernel: [35760.097057]  [<ffffffff811fdb69>] SyS_ioctl+0x79/0x90
Nov  4 21:01:36 eaglinux kernel: [35760.097067]  [<ffffffff81014fb6>] ? sys_rt_sigreturn+0xa6/0xc0
Nov  4 21:01:36 eaglinux kernel: [35760.097074]  [<ffffffff817ba2f2>] entry_SYSCALL_64_fastpath+0x16/0x75
Nov  4 21:03:36 eaglinux kernel: [35880.096113] INFO: task Xorg:1151 blocked for more than 120 seconds.
Nov  4 21:03:36 eaglinux kernel: [35880.096127]       Not tainted 4.2.0-16-generic #19~14.04.1-Ubuntu
Nov  4 21:03:36 eaglinux kernel: [35880.096132] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov  4 21:03:36 eaglinux kernel: [35880.096137] Xorg            D ffff88007fc16640     0  1151   1128 0x00400004
Nov  4 21:03:36 eaglinux kernel: [35880.096149]  ffff8800792e3958 0000000000000086 ffffffff81c14500 ffff880078aacb00
Nov  4 21:03:36 eaglinux kernel: [35880.096156]  ffff880035883aa8 ffff8800792e4000 ffff8800792e3ad8 ffff88003590c000
Nov  4 21:03:36 eaglinux kernel: [35880.096164]  ffff8800792e3a70 ffff88003590d490 ffff8800792e3978 ffffffff817b6a77
Nov  4 21:03:36 eaglinux kernel: [35880.096170] Call Trace:
Nov  4 21:03:36 eaglinux kernel: [35880.096188]  [<ffffffff817b6a77>] schedule+0x37/0x80
Nov  4 21:03:36 eaglinux kernel: [35880.096198]  [<ffffffff817b9431>] schedule_timeout+0x201/0x2a0
Nov  4 21:03:36 eaglinux kernel: [35880.096207]  [<ffffffff810de79e>] ? internal_add_timer+0x7e/0x90
Nov  4 21:03:36 eaglinux kernel: [35880.096289]  [<ffffffffc01de886>] ? radeon_fence_process+0x16/0x40 [radeon]
Nov  4 21:03:36 eaglinux kernel: [35880.096345]  [<ffffffffc01deb1f>] radeon_fence_wait_seq_timeout.constprop.7+0x1ef/0x2c0 [radeon]
Nov  4 21:03:36 eaglinux kernel: [35880.096400]  [<ffffffffc01de782>] ? radeon_fence_emit+0x62/0x150 [radeon]
Nov  4 21:03:36 eaglinux kernel: [35880.096408]  [<ffffffff810b7340>] ? prepare_to_wait_event+0xf0/0xf0
Nov  4 21:03:36 eaglinux kernel: [35880.096463]  [<ffffffffc01deeab>] radeon_fence_wait+0x7b/0xb0 [radeon]
Nov  4 21:03:36 eaglinux kernel: [35880.096542]  [<ffffffffc0201c56>] r100_ib_test+0x186/0x270 [radeon]
Nov  4 21:03:36 eaglinux kernel: [35880.096615]  [<ffffffffc029d0b8>] radeon_ib_ring_tests+0x58/0xc0 [radeon]
Nov  4 21:03:36 eaglinux kernel: [35880.096665]  [<ffffffffc01c5ea3>] radeon_gpu_reset+0x223/0x310 [radeon]
Nov  4 21:03:36 eaglinux kernel: [35880.096719]  [<ffffffffc01de060>] ? radeon_fence_default_wait+0x130/0x130 [radeon]
Nov  4 21:03:36 eaglinux kernel: [35880.096782]  [<ffffffffc01f47be>] radeon_gem_handle_lockup.part.5+0xe/0x20 [radeon]
Nov  4 21:03:36 eaglinux kernel: [35880.096844]  [<ffffffffc01f56da>] radeon_gem_wait_idle_ioctl+0xca/0x130 [radeon]
Nov  4 21:03:36 eaglinux kernel: [35880.096893]  [<ffffffffc001e6c3>] drm_ioctl+0x363/0x680 [drm]
Nov  4 21:03:36 eaglinux kernel: [35880.096956]  [<ffffffffc01f5610>] ? radeon_gem_busy_ioctl+0xe0/0xe0 [radeon]
Nov  4 21:03:36 eaglinux kernel: [35880.096968]  [<ffffffff81085be6>] ? __set_current_blocked+0x36/0x60
Nov  4 21:03:36 eaglinux kernel: [35880.096978]  [<ffffffff8101f8ec>] ? fpu__activate_curr+0x3c/0x80
Nov  4 21:03:36 eaglinux kernel: [35880.096986]  [<ffffffff81085c95>] ? signal_setup_done+0x65/0xa0
Nov  4 21:03:36 eaglinux kernel: [35880.097034]  [<ffffffffc01c304b>] radeon_drm_ioctl+0x4b/0x80 [radeon]
Nov  4 21:03:36 eaglinux kernel: [35880.097044]  [<ffffffff811fd90d>] do_vfs_ioctl+0x2cd/0x4b0
Nov  4 21:03:36 eaglinux kernel: [35880.097052]  [<ffffffff81082b8f>] ? recalc_sigpending+0x1f/0x60
Nov  4 21:03:36 eaglinux kernel: [35880.097059]  [<ffffffff8102102d>] ? fpu__restore_sig+0x4d/0x60
Nov  4 21:03:36 eaglinux kernel: [35880.097067]  [<ffffffff811fdb69>] SyS_ioctl+0x79/0x90
Nov  4 21:03:36 eaglinux kernel: [35880.097077]  [<ffffffff81014fb6>] ? sys_rt_sigreturn+0xa6/0xc0
Nov  4 21:03:36 eaglinux kernel: [35880.097085]  [<ffffffff817ba2f2>] entry_SYSCALL_64_fastpath+0x16/0x75
Nov  4 21:05:36 eaglinux kernel: [36000.096111] INFO: task Xorg:1151 blocked for more than 120 seconds.
Nov  4 21:05:36 eaglinux kernel: [36000.096125]       Not tainted 4.2.0-16-generic #19~14.04.1-Ubuntu
Nov  4 21:05:36 eaglinux kernel: [36000.096130] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov  4 21:05:36 eaglinux kernel: [36000.096135] Xorg            D ffff88007fc16640     0  1151   1128 0x00400004
Nov  4 21:05:36 eaglinux kernel: [36000.096146]  ffff8800792e3958 0000000000000086 ffffffff81c14500 ffff880078aacb00
Nov  4 21:05:36 eaglinux kernel: [36000.096154]  ffff880035883aa8 ffff8800792e4000 ffff8800792e3ad8 ffff88003590c000
Nov  4 21:05:36 eaglinux kernel: [36000.096161]  ffff8800792e3a70 ffff88003590d490 ffff8800792e3978 ffffffff817b6a77
Nov  4 21:05:36 eaglinux kernel: [36000.096168] Call Trace:
Nov  4 21:05:36 eaglinux kernel: [36000.096186]  [<ffffffff817b6a77>] schedule+0x37/0x80
Nov  4 21:05:36 eaglinux kernel: [36000.096206]  [<ffffffff817b9431>] schedule_timeout+0x201/0x2a0
Nov  4 21:05:36 eaglinux kernel: [36000.096215]  [<ffffffff810de79e>] ? internal_add_timer+0x7e/0x90
Nov  4 21:05:36 eaglinux kernel: [36000.096296]  [<ffffffffc01de886>] ? radeon_fence_process+0x16/0x40 [radeon]
Nov  4 21:05:36 eaglinux kernel: [36000.096353]  [<ffffffffc01deb1f>] radeon_fence_wait_seq_timeout.constprop.7+0x1ef/0x2c0 [radeon]
Nov  4 21:05:36 eaglinux kernel: [36000.096407]  [<ffffffffc01de782>] ? radeon_fence_emit+0x62/0x150 [radeon]
Nov  4 21:05:36 eaglinux kernel: [36000.096415]  [<ffffffff810b7340>] ? prepare_to_wait_event+0xf0/0xf0
Nov  4 21:05:36 eaglinux kernel: [36000.096470]  [<ffffffffc01deeab>] radeon_fence_wait+0x7b/0xb0 [radeon]
Nov  4 21:05:36 eaglinux kernel: [36000.096537]  [<ffffffffc0201c56>] r100_ib_test+0x186/0x270 [radeon]
Nov  4 21:05:36 eaglinux kernel: [36000.096612]  [<ffffffffc029d0b8>] radeon_ib_ring_tests+0x58/0xc0 [radeon]
Nov  4 21:05:36 eaglinux kernel: [36000.096661]  [<ffffffffc01c5ea3>] radeon_gpu_reset+0x223/0x310 [radeon]
Nov  4 21:05:36 eaglinux kernel: [36000.096715]  [<ffffffffc01de060>] ? radeon_fence_default_wait+0x130/0x130 [radeon]
Nov  4 21:05:36 eaglinux kernel: [36000.096778]  [<ffffffffc01f47be>] radeon_gem_handle_lockup.part.5+0xe/0x20 [radeon]
Nov  4 21:05:36 eaglinux kernel: [36000.096840]  [<ffffffffc01f56da>] radeon_gem_wait_idle_ioctl+0xca/0x130 [radeon]
Nov  4 21:05:36 eaglinux kernel: [36000.096890]  [<ffffffffc001e6c3>] drm_ioctl+0x363/0x680 [drm]
Nov  4 21:05:36 eaglinux kernel: [36000.096953]  [<ffffffffc01f5610>] ? radeon_gem_busy_ioctl+0xe0/0xe0 [radeon]
Nov  4 21:05:36 eaglinux kernel: [36000.096964]  [<ffffffff81085be6>] ? __set_current_blocked+0x36/0x60
Nov  4 21:05:36 eaglinux kernel: [36000.096974]  [<ffffffff8101f8ec>] ? fpu__activate_curr+0x3c/0x80
Nov  4 21:05:36 eaglinux kernel: [36000.096982]  [<ffffffff81085c95>] ? signal_setup_done+0x65/0xa0
Nov  4 21:05:36 eaglinux kernel: [36000.097031]  [<ffffffffc01c304b>] radeon_drm_ioctl+0x4b/0x80 [radeon]
Nov  4 21:05:36 eaglinux kernel: [36000.097040]  [<ffffffff811fd90d>] do_vfs_ioctl+0x2cd/0x4b0
Nov  4 21:05:36 eaglinux kernel: [36000.097049]  [<ffffffff81082b8f>] ? recalc_sigpending+0x1f/0x60
Nov  4 21:05:36 eaglinux kernel: [36000.097055]  [<ffffffff8102102d>] ? fpu__restore_sig+0x4d/0x60
Nov  4 21:05:36 eaglinux kernel: [36000.097064]  [<ffffffff811fdb69>] SyS_ioctl+0x79/0x90
Nov  4 21:05:36 eaglinux kernel: [36000.097073]  [<ffffffff81014fb6>] ? sys_rt_sigreturn+0xa6/0xc0
Nov  4 21:05:36 eaglinux kernel: [36000.097081]  [<ffffffff817ba2f2>] entry_SYSCALL_64_fastpath+0x16/0x75
Nov  4 21:06:15 eaglinux dhclient: PRC: Renewing lease on eth0.
Nov  4 21:06:15 eaglinux dhclient: XMT: Renew on eth0, interval 10820ms.
Nov  4 21:06:15 eaglinux dhclient: RCV: Reply message on eth0 from fe80::ea94:f6ff:fed4:4622.
Nov  4 21:06:16 eaglinux NetworkManager[1047]: <info> (eth0): DHCPv6 state changed renew6 -> renew6
Nov  4 21:06:16 eaglinux NetworkManager[1047]: <info>   address fdd5:636f:7401::9be/128
Nov  4 21:06:16 eaglinux NetworkManager[1047]: <info>   nameserver 'fdd5:636f:7401::1'
Nov  4 21:06:16 eaglinux NetworkManager[1047]: <info>   domain search 'lan.'
Nov  4 21:06:16 eaglinux dbus[528]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Nov  4 21:06:16 eaglinux dbus[528]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Nov  4 21:07:36 eaglinux kernel: [36120.096112] INFO: task Xorg:1151 blocked for more than 120 seconds.
Nov  4 21:07:36 eaglinux kernel: [36120.096125]       Not tainted 4.2.0-16-generic #19~14.04.1-Ubuntu
Nov  4 21:07:36 eaglinux kernel: [36120.096130] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov  4 21:07:36 eaglinux kernel: [36120.096135] Xorg            D ffff88007fc16640     0  1151   1128 0x00400004
Nov  4 21:07:36 eaglinux kernel: [36120.096147]  ffff8800792e3958 0000000000000086 ffffffff81c14500 ffff880078aacb00
Nov  4 21:07:36 eaglinux kernel: [36120.096155]  ffff880035883aa8 ffff8800792e4000 ffff8800792e3ad8 ffff88003590c000
Nov  4 21:07:36 eaglinux kernel: [36120.096162]  ffff8800792e3a70 ffff88003590d490 ffff8800792e3978 ffffffff817b6a77
Nov  4 21:07:36 eaglinux kernel: [36120.096169] Call Trace:
Nov  4 21:07:36 eaglinux kernel: [36120.096187]  [<ffffffff817b6a77>] schedule+0x37/0x80
Nov  4 21:07:36 eaglinux kernel: [36120.096196]  [<ffffffff817b9431>] schedule_timeout+0x201/0x2a0
Nov  4 21:07:36 eaglinux kernel: [36120.096205]  [<ffffffff810de79e>] ? internal_add_timer+0x7e/0x90
Nov  4 21:07:36 eaglinux kernel: [36120.096287]  [<ffffffffc01de886>] ? radeon_fence_process+0x16/0x40 [radeon]
Nov  4 21:07:36 eaglinux kernel: [36120.096343]  [<ffffffffc01deb1f>] radeon_fence_wait_seq_timeout.constprop.7+0x1ef/0x2c0 [radeon]
Nov  4 21:07:36 eaglinux kernel: [36120.096398]  [<ffffffffc01de782>] ? radeon_fence_emit+0x62/0x150 [radeon]
Nov  4 21:07:36 eaglinux kernel: [36120.096406]  [<ffffffff810b7340>] ? prepare_to_wait_event+0xf0/0xf0
Nov  4 21:07:36 eaglinux kernel: [36120.096461]  [<ffffffffc01deeab>] radeon_fence_wait+0x7b/0xb0 [radeon]
Nov  4 21:07:36 eaglinux kernel: [36120.096528]  [<ffffffffc0201c56>] r100_ib_test+0x186/0x270 [radeon]
Nov  4 21:07:36 eaglinux kernel: [36120.096602]  [<ffffffffc029d0b8>] radeon_ib_ring_tests+0x58/0xc0 [radeon]
Nov  4 21:07:36 eaglinux kernel: [36120.096652]  [<ffffffffc01c5ea3>] radeon_gpu_reset+0x223/0x310 [radeon]
Nov  4 21:07:36 eaglinux kernel: [36120.096706]  [<ffffffffc01de060>] ? radeon_fence_default_wait+0x130/0x130 [radeon]
Nov  4 21:07:36 eaglinux kernel: [36120.096769]  [<ffffffffc01f47be>] radeon_gem_handle_lockup.part.5+0xe/0x20 [radeon]
Nov  4 21:07:36 eaglinux kernel: [36120.096831]  [<ffffffffc01f56da>] radeon_gem_wait_idle_ioctl+0xca/0x130 [radeon]
Nov  4 21:07:36 eaglinux kernel: [36120.096880]  [<ffffffffc001e6c3>] drm_ioctl+0x363/0x680 [drm]
Nov  4 21:07:36 eaglinux kernel: [36120.096943]  [<ffffffffc01f5610>] ? radeon_gem_busy_ioctl+0xe0/0xe0 [radeon]
Nov  4 21:07:36 eaglinux kernel: [36120.096954]  [<ffffffff81085be6>] ? __set_current_blocked+0x36/0x60
Nov  4 21:07:36 eaglinux kernel: [36120.096964]  [<ffffffff8101f8ec>] ? fpu__activate_curr+0x3c/0x80
Nov  4 21:07:36 eaglinux kernel: [36120.096972]  [<ffffffff81085c95>] ? signal_setup_done+0x65/0xa0
Nov  4 21:07:36 eaglinux kernel: [36120.097020]  [<ffffffffc01c304b>] radeon_drm_ioctl+0x4b/0x80 [radeon]
Nov  4 21:07:36 eaglinux kernel: [36120.097030]  [<ffffffff811fd90d>] do_vfs_ioctl+0x2cd/0x4b0
Nov  4 21:07:36 eaglinux kernel: [36120.097039]  [<ffffffff81082b8f>] ? recalc_sigpending+0x1f/0x60
Nov  4 21:07:36 eaglinux kernel: [36120.097045]  [<ffffffff8102102d>] ? fpu__restore_sig+0x4d/0x60
Nov  4 21:07:36 eaglinux kernel: [36120.097053]  [<ffffffff811fdb69>] SyS_ioctl+0x79/0x90
Nov  4 21:07:36 eaglinux kernel: [36120.097063]  [<ffffffff81014fb6>] ? sys_rt_sigreturn+0xa6/0xc0
Nov  4 21:07:36 eaglinux kernel: [36120.097071]  [<ffffffff817ba2f2>] entry_SYSCALL_64_fastpath+0x16/0x75
```

From what I understand, there is a problem with the radeon driver. I have tried several different kernels, that is 3.16.0-38, 3.16.0-51, 3.19.0-31, 4.2.0.16 and even the latest 4.3.0-040300, all with no luck.
Is there everything else I can try? Is there any old linux distribution that is supposed to better support my video card?

---

### Post by QIII on 2015-11-05
Hello!

What have you heard about the Radeon driver?  It should support that card just fine.

From your description and a brief review of your logs, I am more inclined to suspect hardware failure than software.

You might try a live session of another distro with a slightly older kernel to see what happens.

---

### Post by hardhu on 2015-11-05
> **QIII said:**
> Hello!

What have you heard about the Radeon driver?  It should support that card just fine.

From your description and a brief review of your logs, I am more inclined to suspect hardware failure than software.

You might try a live session of another distro with a slightly older kernel to see what happens.

Thanks for your answer. Yes, my card is listed as supported by Radeon driver, however I have just installed Lubuntu 14.04 alongside Mint, and I will monitor if it's working fine,  it has kernel 3.19.0-32-generic and X.org 1.17.1, my suspect is that is the combination of kernel and X server to give problems.

---

### Post by QIII on 2015-11-05
Ubuntu's Unity DE may just have been a bit too much for that older GPU.  If you get good performance now, that's great!

Fingers crossed.

---

### Post by hardhu on 2015-11-06
> **QIII said:**
> Ubuntu's Unity DE may just have been a bit too much for that older GPU.  If you get good performance now, that's great!

Fingers crossed.

I don't think is DE related, before I was using Linux Mint 17.2 Xfce and I had the same problems.
Now, with Lubuntu and kernel 3.19.0-32-generic I have similar problems: X session crashed but I could at least switch to console mode and reboot from there. 
Here are last lines from syslog:
```

Nov  6 18:40:53 eaglubuntu kernel: [  835.116037] radeon 0000:01:00.0: ring 0 stalled for more than 10496msec
Nov  6 18:40:53 eaglubuntu kernel: [  835.116046] radeon 0000:01:00.0: GPU lockup (current fence id 0x000000000000006b last fence id 0x00000000000000ac on ring 0)

```


Now I am trying kernel 3.19.0-25-generic to see if it's happening again.

---

### Post by hardhu on 2015-11-18
I have the same problem with kernel 3.19.0-25, and also with an older 3.13 one...now I am trying to install old fglrx driver to check if my problem is hardware related. I have been able to install it, but I can't configure correctly the resolution of my monitor, that is 1280x800@60. I cannot use the command
```
amdconfig --initial 
``` because it says that my video adapter is not supported. I tried to follow this tutorial ([https://wiki.archlinux.org/index.php/Xorg#Monitor_settings]("https://wiki.archlinux.org/index.php/Xorg#Monitor_settings")) and I created this 10-monitor.conf file

```

Section "Monitor"
    Identifier             "Monitor0"
EndSection

Section "Device"
    Identifier             "Device0"
    Driver                 "fglrx" #Choose the driver used for this monitor
EndSection

Section "Screen"
    Identifier             "Screen0"  #Collapse Monitor and Device section to Screen section
    Device                 "Device0"
    Monitor                "Monitor0"
    DefaultDepth           16 #Choose the depth (16||24)
    SubSection             "Display"
        Depth              16
        Modes              "1280x800_60.00" #Choose the resolution
    EndSubSection
EndSection

```

that I put in  /usr/share/X11/xorg.conf.d/ , but then the X session fails to start. Any suggestion?

---

