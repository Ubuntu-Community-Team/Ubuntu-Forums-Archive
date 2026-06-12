---
title: "Applications crashing every half or 45 mins"
date: 2011-11-11
forum: Installation &amp; Upgrades
---

### Post by eyemole on 2011-11-11
kernel version running : 2.6.35-30-generic #61-Ubuntu SMP Tue Oct 11 17:52:57 UTC 2011 x86_64 GNU/Linux

Ubuntu dist : 10.10 Maverick (64 bit)
Hardware : Dell Latitude6410 

Apps like firefox and chromium crashes every 15-20 mins. VirtualBox running Windows7 cannot even stand 5 mins now.dmesg  has following while browser crashes.
```
[   28.108187] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.ECDV.ECR1] (Node ffff88011763dd60), AE_TIME
[   28.108246] ACPI Error (psparse-0537): Method parse/execution failed [\ECBT] (Node ffff88011763de40), AE_TIME
[   28.108277] ACPI Error (psparse-0537): Method parse/execution failed [\ECG2] (Node ffff88011763df00), AE_TIME
[   28.108307] ACPI Error (psparse-0537): Method parse/execution failed [\ECG6] (Node ffff88011763dfc0), AE_TIME
[   28.108336] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.BAT0._BST] (Node ffff88011763f5c0), AE_TIME
[   28.108370] ACPI Exception: AE_TIME, Evaluating _BST (20100428/battery-442)
[   28.391658] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input13
[   28.594898] Bluetooth: L2CAP ver 2.14
[   28.594900] Bluetooth: L2CAP socket layer initialized
[   28.599563] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.599566] Bluetooth: BNEP filters: protocol multicast
[   28.603337] Bluetooth: SCO (Voice Link) ver 0.6
[   28.603340] Bluetooth: SCO socket layer initialized
[   28.670682] Bluetooth: RFCOMM TTY layer initialized
[   28.670689] Bluetooth: RFCOMM socket layer initialized
[   28.670691] Bluetooth: RFCOMM ver 1.11
[   28.789716] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[   28.789722] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   28.792992] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   31.342933] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   36.975710] lo: Disabled Privacy Extensions
[   37.454828] eth1: no IPv6 routers present
[   37.985385] virbr0: no IPv6 routers present
[   38.625668] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   39.117000] lo: Disabled Privacy Extensions
[   39.435189] eth0: no IPv6 routers present
[ 7121.020452] lo: Disabled Privacy Extensions
[ 7556.372378] INFO: task chromium-browse:2393 blocked for more than 120 seconds.
[ 7556.372383] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 7556.372387] chromium-brow D 00000001000ab779     0  2393   2252 0x00000000
[ 7556.372392]  ffff8800c9fd3df8 0000000000000082 0000000e00000000 0000000000015b80
[ 7556.372399]  ffff8800c9fd3fd8 0000000000015b80 ffff8800c9fd3fd8 ffff8800d3fc8000
[ 7556.372405]  0000000000015b80 0000000000015b80 ffff8800c9fd3fd8 0000000000015b80
[ 7556.372411] Call Trace:
[ 7556.372425]  [<ffffffff812304d5>] jbd2_log_wait_commit+0xc5/0x150
[ 7556.372434]  [<ffffffff81080630>] ? autoremove_wake_function+0x0/0x40
[ 7556.372440]  [<ffffffff81230596>] ? __jbd2_log_start_commit+0x36/0x40
[ 7556.372454]  [<ffffffff811eaa48>] ext4_sync_file+0x138/0x2e0
[ 7556.372460]  [<ffffffff8117c73c>] vfs_fsync_range+0x7c/0xa0
[ 7556.372465]  [<ffffffff8117c7cc>] vfs_fsync+0x1c/0x20
[ 7556.372469]  [<ffffffff8117c80a>] do_fsync+0x3a/0x60
[ 7556.372473]  [<ffffffff8117c843>] sys_fdatasync+0x13/0x20
[ 7556.372482]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
[ 7556.372502] INFO: task ubuntuone-syncd:3030 blocked for more than 120 seconds.
[ 7556.372505] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 7556.372508] ubuntuone-syn D 00000001000ad1bd     0  3030      1 0x00000000
[ 7556.372514]  ffff8800a8d359f8 0000000000000086 ffff880000000000 0000000000015b80
[ 7556.372520]  ffff8800a8d35fd8 0000000000015b80 ffff8800a8d35fd8 ffff8800a8cc16f0
[ 7556.372526]  0000000000015b80 0000000000015b80 ffff8800a8d35fd8 0000000000015b80
[ 7556.372532] Call Trace:
[ 7556.372540]  [<ffffffff8122a85d>] do_get_write_access+0x2ed/0x5b0
[ 7556.372546]  [<ffffffff81080670>] ? wake_bit_function+0x0/0x40
[ 7556.372552]  [<ffffffff8122ac71>] jbd2_journal_get_write_access+0x31/0x50
[ 7556.372560]  [<ffffffff81211e78>] __ext4_journal_get_write_access+0x38/0x70
[ 7556.372566]  [<ffffffff811f0c23>] ext4_reserve_inode_write+0x73/0xa0
[ 7556.372572]  [<ffffffff81229b15>] ? jbd2_journal_start+0xb5/0x100
[ 7556.372577]  [<ffffffff811f0c9c>] ext4_mark_inode_dirty+0x4c/0x1d0
[ 7556.372582]  [<ffffffff812056a8>] ? ext4_journal_start_sb+0xf8/0x130
[ 7556.372587]  [<ffffffff8121de70>] ? ext4_xattr_get+0x60/0xa0
[ 7556.372592]  [<ffffffff811f0f90>] ext4_dirty_inode+0x40/0x60
[ 7556.372659]  [<ffffffff81178312>] __mark_inode_dirty+0x42/0x1d0
[ 7556.372666]  [<ffffffff8116bcbb>] file_update_time+0xfb/0x180
[ 7556.372674]  [<ffffffff81105180>] __generic_file_aio_write+0x210/0x470
[ 7556.372679]  [<ffffffff811601f5>] ? path_to_nameidata+0x25/0x60
[ 7556.372685]  [<ffffffff81170b30>] ? mntput_no_expire+0x30/0x110
[ 7556.372690]  [<ffffffff81105445>] generic_file_aio_write+0x65/0xd0
[ 7556.372695]  [<ffffffff811ea899>] ext4_file_write+0x39/0xb0
[ 7556.372701]  [<ffffffff8115f975>] ? putname+0x35/0x50
[ 7556.372705]  [<ffffffff811548ca>] do_sync_write+0xda/0x120
[ 7556.372713]  [<ffffffff81036df9>] ? default_spin_lock_flags+0x9/0x10
[ 7556.372721]  [<ffffffff81292e08>] ? apparmor_file_permission+0x18/0x20
[ 7556.372728]  [<ffffffff81262286>] ? security_file_permission+0x16/0x20
[ 7556.372733]  [<ffffffff81154ba8>] vfs_write+0xb8/0x1a0
[ 7556.372737]  [<ffffffff81155421>] sys_write+0x51/0x80
[ 7556.372743]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
[ 7556.372750] INFO: task atop:3721 blocked for more than 120 seconds.
[ 7556.372753] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 7556.372756] atop          D 00000001000ac5e4     0  3721      1 0x00000000
[ 7556.372762]  ffff88006f981a38 0000000000000082 0000000200000000 0000000000015b80
[ 7556.372768]  ffff88006f981fd8 0000000000015b80 ffff88006f981fd8 ffff8800bbcd5bc0
[ 7556.372774]  0000000000015b80 0000000000015b80 ffff88006f981fd8 0000000000015b80
[ 7556.372779] Call Trace:
[ 7556.372786]  [<ffffffff8122a85d>] do_get_write_access+0x2ed/0x5b0
[ 7556.372791]  [<ffffffff81080670>] ? wake_bit_function+0x0/0x40
[ 7556.372797]  [<ffffffff8122ac71>] jbd2_journal_get_write_access+0x31/0x50
[ 7556.372803]  [<ffffffff81211e78>] __ext4_journal_get_write_access+0x38/0x70
[ 7556.372809]  [<ffffffff811f0c23>] ext4_reserve_inode_write+0x73/0xa0
[ 7556.372814]  [<ffffffff81229b15>] ? jbd2_journal_start+0xb5/0x100
[ 7556.372819]  [<ffffffff811f0c9c>] ext4_mark_inode_dirty+0x4c/0x1d0
[ 7556.372824]  [<ffffffff812056a8>] ? ext4_journal_start_sb+0xf8/0x130
[ 7556.372830]  [<ffffffff811f0f90>] ext4_dirty_inode+0x40/0x60
[ 7556.372835]  [<ffffffff81178312>] __mark_inode_dirty+0x42/0x1d0
[ 7556.372840]  [<ffffffff8116be75>] touch_atime+0x135/0x180
[ 7556.372845]  [<ffffffff81104418>] T.859+0x2c8/0x420
[ 7556.372850]  [<ffffffff81104658>] generic_file_aio_read+0xe8/0x230
[ 7556.372855]  [<ffffffff811549ea>] do_sync_read+0xda/0x120
[ 7556.372860]  [<ffffffff81170b30>] ? mntput_no_expire+0x30/0x110
[ 7556.372866]  [<ffffffff81292e08>] ? apparmor_file_permission+0x18/0x20
[ 7556.372871]  [<ffffffff81262286>] ? security_file_permission+0x16/0x20
[ 7556.372876]  [<ffffffff81155265>] vfs_read+0xb5/0x1a0
[ 7556.372880]  [<ffffffff811553a1>] sys_read+0x51/0x80
[ 7556.372885]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
[ 8053.701679] show_signal_msg: 48 callbacks suppressed
[ 8053.701688] npviewer.bin[4260]: segfault at f5269bfc ip 00000000f7004c28 sp 00000000f27be05c error 6 in libpthread-2.12.1.so[f6ffa000+15000]
[13643.950150] npviewer.bin[4870]: segfault at 0 ip 00000000f5c95c91 sp 00000000ffa31290 error 4 in libflashplayer.so[f5818000+fc7000]
[14343.956829] npviewer.bin[5111]: segfault at 218 ip 00000000f5bf6e36 sp 00000000ffb99828 error 6 in libflashplayer.so[f58cb000+fc7000]
[19922.077195] lo: Disabled Privacy Extensions

```

---

### Post by raja.genupula on 2011-11-11
Application crashes sounds like Bugs ....you can report them as 

```
ubuntu-bug <app_name>
``` to launchpad

---

