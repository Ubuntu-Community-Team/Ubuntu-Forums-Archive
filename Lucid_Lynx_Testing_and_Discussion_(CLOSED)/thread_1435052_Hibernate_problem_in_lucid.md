---
title: "Hibernate problem in lucid"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by megaexception on 2010-03-21
when laptop is not restoring from hibernate, it just boots clean system.
i've checked dmesg, i find large bunch of traces (see code below). these traces appear only when laptop is resuming, and do not appear on normal boot.
hibernate worked perfectly in karmic.

how can i get hibernate working?

```

Mar 21 09:10:13 t00l kernel: Inspecting /boot/System.map-2.6.32-16-generic-pae
Mar 21 09:10:13 t00l kernel: Cannot find map file.
Mar 21 09:10:13 t00l kernel: Loaded 71324 symbols from 93 modules.
Mar 21 09:10:13 t00l kernel: [   28.228319]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:13 t00l kernel: [   28.228375]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:13 t00l kernel: [   28.228431]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:13 t00l kernel: [   28.228487]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:13 t00l kernel: [   28.228543] udevd         D 00008339     0   101     78 0x00000000
Mar 21 09:10:13 t00l kernel: [   28.228665]  f6e19e88 00000082 f6e3a000 00008339 00000000 c08b1440 f6e0c2bc c08b1440
Mar 21 09:10:13 t00l kernel: [   28.228995]  e49506c9 00000001 c08b1440 c08b1440 f6e0c2bc c08b1440 c08b1440 f6e14380
Mar 21 09:10:13 t00l kernel: [   28.229326]  00000000 00000001 f6e0c010 f6e0c010 00000000 00000002 f6e19e9c c0175ccd
Mar 21 09:10:13 t00l kernel: [   28.229656] Call Trace:
Mar 21 09:10:13 t00l kernel: [   28.229709]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:13 t00l kernel: [   28.229765]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:13 t00l kernel: [   28.229824]  [<c0136198>] ? ptep_set_access_flags+0x58/0x70
Mar 21 09:10:13 t00l kernel: [   28.229883]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:13 t00l kernel: [   28.229939]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:13 t00l kernel: [   28.229996]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.230054]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.230111]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.230168]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.230225]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.230280] udevd         D 0000837f     0   102     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.230403]  f6e3be88 00000082 f6e3c000 0000837f 00000000 c08b1440 f6e0cf8c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.230735]  e4951188 00000001 c08b1440 c08b1440 f6e0cf8c c08b1440 c08b1440 f6e14540
Mar 21 09:10:14 t00l kernel: [   28.231062]  00000000 00000001 f6e0cce0 f6e0cce0 00000000 00000002 f6e3be9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.231392] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.231444]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.231501]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.231560]  [<c0136198>] ? ptep_set_access_flags+0x58/0x70
Mar 21 09:10:14 t00l kernel: [   28.231617]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.231674]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.231731]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.231789]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.231846]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.231902]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.231959]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.232024] udevd         D 00008bc5     0   103     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.232145]  f6e3de88 00000086 f6e40000 00008bc5 00000000 c08b1440 f6e0dc5c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.232474]  e4951d9c 00000001 c08b1440 c08b1440 f6e0dc5c c08b1440 c08b1440 f6e14700
Mar 21 09:10:14 t00l kernel: [   28.232802]  00000000 00000001 f6e0d9b0 f6e0d9b0 00000000 00000002 f6e3de9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.233133] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.233185]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.233242]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.233301]  [<c0136198>] ? ptep_set_access_flags+0x58/0x70
Mar 21 09:10:14 t00l kernel: [   28.233359]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.233416]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.233473]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.233532]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.233589]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.233645]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.233702]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.233758] udevd         D 000087ed     0   104     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.233880]  f6e41e88 00000086 f6e42000 000087ed 00000000 c08b1440 f6e0e92c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.234208]  e4952969 00000001 c08b1440 c08b1440 f6e0e92c c08b1440 c08b1440 f6e148c0
Mar 21 09:10:14 t00l kernel: [   28.234537]  00000000 00000001 f6e0e680 f6e0e680 00000000 00000002 f6e41e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.234867] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.234919]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.234977]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.235036]  [<c0136198>] ? ptep_set_access_flags+0x58/0x70
Mar 21 09:10:14 t00l kernel: [   28.235096]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.235151]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.235209]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.235267]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.235325]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.235381]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.235438]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.235492] udevd         D 00008766     0   105     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.235615]  f6e43e88 00000082 f6e44000 00008766 00000000 c08b1440 f6e482ac c08b1440
Mar 21 09:10:14 t00l kernel: [   28.235945]  e4953437 00000001 c08b1440 c08b1440 f6e482ac c08b1440 c08b1440 f6e14a80
Mar 21 09:10:14 t00l kernel: [   28.236284]  00000000 00000001 f6e48000 f6e48000 00000000 00000002 f6e43e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.236610] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.236663]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.236719]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.236778]  [<c0136198>] ? ptep_set_access_flags+0x58/0x70
Mar 21 09:10:14 t00l kernel: [   28.236837]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.236894]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.236950]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.237008]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.237065]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.237121]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.237177]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.237233] udevd         D 00008365     0   106     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.237355]  f6e45e88 00000082 f6e46000 00008365 00000000 c08b1440 f6e48f7c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.237683]  e4953f19 00000001 c08b1440 c08b1440 f6e48f7c c08b1440 c08b1440 f6e14c40
Mar 21 09:10:14 t00l kernel: [   28.238011]  00000000 00000001 f6e48cd0 f6e48cd0 00000000 00000002 f6e45e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.238341] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.238393]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.238450]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.238508]  [<c0136198>] ? ptep_set_access_flags+0x58/0x70
Mar 21 09:10:14 t00l kernel: [   28.238567]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.238622]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.238679]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.238738]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.238795]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.238852]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.238908]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.238963] udevd         D 00008d50     0   107     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.239084]  f6e47e88 00000086 f6e58000 00008d50 00000000 c08b1440 f6e49c4c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.239417]  e4954aaa 00000001 c08b1440 c08b1440 f6e49c4c c08b1440 c08b1440 f6e14e00
Mar 21 09:10:14 t00l kernel: [   28.239746]  00000000 00000001 f6e499a0 f6e499a0 00000000 00000002 f6e47e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.240083] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.240136]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.240191]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.240250]  [<c0136198>] ? ptep_set_access_flags+0x58/0x70
Mar 21 09:10:14 t00l kernel: [   28.240309]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.240365]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.240422]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.240480]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.240538]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.240595]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.240652]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.240707] udevd         D 00008977     0   108     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.240829]  f6e59e88 00000086 f6e78000 00008977 00000000 c08b1440 f6e4a91c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.241158]  e495565f 00000001 c08b1440 c08b1440 f6e4a91c c08b1440 c08b1440 f6e14fc0
Mar 21 09:10:14 t00l kernel: [   28.241489]  00000000 00000001 f6e4a670 f6e4a670 00000000 00000002 f6e59e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.241817] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.241869]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.241924]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.241983]  [<c0136198>] ? ptep_set_access_flags+0x58/0x70
Mar 21 09:10:14 t00l kernel: [   28.242042]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.242098]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.242155]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.242213]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.242270]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.242325]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.242381]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.242437] udevd         D 00008a48     0   109     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.242560]  f6e79e88 00000082 f6e7a000 00008a48 00000000 c08b1440 f6e4b5ec c08b1440
Mar 21 09:10:14 t00l kernel: [   28.242890]  e4956173 00000001 c08b1440 c08b1440 f6e4b5ec c08b1440 c08b1440 f6e15180
Mar 21 09:10:14 t00l kernel: [   28.244010]  00000000 00000001 f6e4b340 f6e4b340 00000000 00000002 f6e79e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.244339] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.244392]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.244449]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.244508]  [<c0136198>] ? ptep_set_access_flags+0x58/0x70
Mar 21 09:10:14 t00l kernel: [   28.244568]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.244623]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.244681]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.244739]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.244795]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.244851]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.244908]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.244962] udevd         D 00008c0c     0   110     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.245085]  f6e7be88 00000082 f6d9a000 00008c0c 00000000 c08b1440 f6e4c2bc c08b1440
Mar 21 09:10:14 t00l kernel: [   28.245415]  e4956ce6 00000001 c08b1440 c08b1440 f6e4c2bc c08b1440 c08b1440 f6e15340
Mar 21 09:10:14 t00l kernel: [   28.245744]  00000000 00000001 f6e4c010 f6e4c010 00000000 00000002 f6e7be9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.246074] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.246127]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.246182]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.246241]  [<c0136198>] ? ptep_set_access_flags+0x58/0x70
Mar 21 09:10:14 t00l kernel: [   28.246299]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.246356]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.246413]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.246471]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.246528]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.246585]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.246642]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.246698] udevd         D 00008366     0   169     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.246822]  f6d9be88 00000086 f6f54000 00008366 00000000 c08b1440 f6eae92c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.247151]  e495777d 00000001 c08b1440 c08b1440 f6eae92c c08b1440 c08b1440 f6d88700
Mar 21 09:10:14 t00l kernel: [   28.247481]  00000000 00000001 f6eae680 f6eae680 00000000 00000002 f6d9be9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.247810] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.247862]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.247918]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.247977]  [<c0136198>] ? ptep_set_access_flags+0x58/0x70
Mar 21 09:10:14 t00l kernel: [   28.248044]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.248100]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.248157]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.248216]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.248272]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.248328]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.248385]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.248441] udevd         D 00008439     0   170     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.248563]  f6f55e88 00000086 f6f56000 00008439 00000000 c08b1440 f6f582ac c08b1440
Mar 21 09:10:14 t00l kernel: [   28.248893]  e49582b9 00000001 c08b1440 c08b1440 f6f582ac c08b1440 c08b1440 f6d881c0
Mar 21 09:10:14 t00l kernel: [   28.249223]  00000000 00000001 f6f58000 f6f58000 00000000 00000002 f6f55e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.249551] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.249604]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.249661]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.249720]  [<c040ebb3>] ? scsi_device_unbusy+0x93/0xa0
Mar 21 09:10:14 t00l kernel: [   28.249777]  [<c04078ed>] ? scsi_finish_command+0x9d/0x100
Mar 21 09:10:14 t00l kernel: [   28.249836]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.249892]  [<c044a01b>] ? ahci_interrupt+0x9b/0x100
Mar 21 09:10:14 t00l kernel: [   28.249950]  [<c03461b2>] ? blk_done_softirq+0x62/0x70
Mar 21 09:10:14 t00l kernel: [   28.250008]  [<c015937b>] ? __do_softirq+0xeb/0x1b0
Mar 21 09:10:14 t00l kernel: [   28.250065]  [<c01a6534>] ? handle_IRQ_event+0x54/0x150
Mar 21 09:10:14 t00l kernel: [   28.250122]  [<c01a9709>] ? move_native_irq+0x19/0x50
Mar 21 09:10:14 t00l kernel: [   28.250181]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.250238]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.250294]  [<c05c85c5>] ? do_IRQ+0x55/0xc0
Mar 21 09:10:14 t00l kernel: [   28.250350]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.250406]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.250462] udevd         D 00007fb6     0   171     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.250583]  f6f57e88 00000082 f6ee2000 00007fb6 00000000 c08b1440 f6f58f7c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.250913]  e4958e5e 00000001 c08b1440 c08b1440 f6f58f7c c08b1440 c08b1440 f6d88a80
Mar 21 09:10:14 t00l kernel: [   28.251242]  00000000 00000001 f6f58cd0 f6f58cd0 00000000 00000002 f6f57e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.251573] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.251625]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.251682]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.251740]  [<c0136198>] ? ptep_set_access_flags+0x58/0x70
Mar 21 09:10:14 t00l kernel: [   28.251799]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.251854]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.251912]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.251970]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.252038]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.252094]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.252150]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.252206] udevd         D 00008162     0   172     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.252327]  f6ee3e88 00000086 f6f74000 00008162 00000000 c08b1440 f6f59c4c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.252656]  e4959959 00000001 c08b1440 c08b1440 f6f59c4c c08b1440 c08b1440 f6ee4000
Mar 21 09:10:14 t00l kernel: [   28.252983]  00000000 00000001 f6f599a0 f6f599a0 00000000 00000002 f6ee3e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.253308] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.253360]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.253416]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.253475]  [<c0136198>] ? ptep_set_access_flags+0x58/0x70
Mar 21 09:10:14 t00l kernel: [   28.253533]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.253589]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.253646]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.253704]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.253762]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.253818]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.253875]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.253930] udevd         D 000080bc     0   173     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.254051]  f6f75e88 00000086 f6f76000 000080bc 00000000 c08b1440 f6f5a91c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.254379]  e495a51d 00000001 c08b1440 c08b1440 f6f5a91c c08b1440 c08b1440 f6ee41c0
Mar 21 09:10:14 t00l kernel: [   28.254709]  00000000 00000001 f6f5a670 f6f5a670 00000000 00000002 f6f75e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.255038] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.255090]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.255148]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.255205]  [<c0136198>] ? ptep_set_access_flags+0x58/0x70
Mar 21 09:10:14 t00l kernel: [   28.255263]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.255319]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.255376]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.255434]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.255492]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.255549]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.255606]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.255662] udevd         D 00008327     0   174     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.255784]  f6f77e88 00000082 f6f78000 00008327 00000000 c08b1440 f6f5b5ec c08b1440
Mar 21 09:10:14 t00l kernel: [   28.256121]  e495b0d6 00000001 c08b1440 c08b1440 f6f5b5ec c08b1440 c08b1440 f6ee4380
Mar 21 09:10:14 t00l kernel: [   28.256452]  00000000 00000001 f6f5b340 f6f5b340 00000000 00000002 f6f77e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.256781] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.256834]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.256890]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.256949]  [<c0136198>] ? ptep_set_access_flags+0x58/0x70
Mar 21 09:10:14 t00l kernel: [   28.257008]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.257064]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.257122]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.257180]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.257238]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.257295]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.257351]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.257407] udevd         D 00008ceb     0   175     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.257529]  f6f79e88 00000082 f6f8a000 00008ceb 00000000 c08b1440 f6f5c2bc c08b1440
Mar 21 09:10:14 t00l kernel: [   28.257858]  e495bc8b 00000001 c08b1440 c08b1440 f6f5c2bc c08b1440 c08b1440 f6ee4540
Mar 21 09:10:14 t00l kernel: [   28.258189]  00000000 00000001 f6f5c010 f6f5c010 00000000 00000002 f6f79e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.258516] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.258568]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.258624]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.258683]  [<c0136198>] ? ptep_set_access_flags+0x58/0x70
Mar 21 09:10:14 t00l kernel: [   28.258741]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.258797]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.258854]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.258913]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.258970]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.259027]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.259083]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.259137] udevd         D 00009069     0   180     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.259260]  f6f8be88 00000086 f6fac000 00009069 00000000 c08b1440 f6f80f7c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.259588]  e495c7e5 00000001 c08b1440 c08b1440 f6f80f7c c08b1440 c08b1440 f6ee4e00
Mar 21 09:10:14 t00l kernel: [   28.259915]  00000000 00000001 f6f80cd0 f6f80cd0 00000000 00000002 f6f8be9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.260253] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.260306]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.260363]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.260421]  [<c0136198>] ? ptep_set_access_flags+0x58/0x70
Mar 21 09:10:14 t00l kernel: [   28.260480]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.260536]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.260594]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.260652]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.260709]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.260764]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.261604]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.261659] udevd         D 00008681     0   181     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.261780]  f6fade88 00000086 f6fae000 00008681 00000000 c08b1440 f6f81c4c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.262110]  e495d335 00000001 c08b1440 c08b1440 f6f81c4c c08b1440 c08b1440 f6ee4fc0
Mar 21 09:10:14 t00l kernel: [   28.262439]  00000000 00000001 f6f819a0 f6f819a0 00000000 00000002 f6fade9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.262768] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.262821]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.262878]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.262937]  [<c0136198>] ? ptep_set_access_flags+0x58/0x70
Mar 21 09:10:14 t00l kernel: [   28.262996]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.263052]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.263109]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.263168]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.263224]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.263281]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.263337]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.263393] udevd         D 0000a0e4     0   182     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.263515]  f6fafe88 00000082 f6fb0000 0000a0e4 00000000 c08b1440 f6f8291c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.263844]  e495df85 00000001 c08b1440 c08b1440 f6f8291c c08b1440 c08b1440 f6ee5180
Mar 21 09:10:14 t00l kernel: [   28.264182]  00000000 00000001 f6f82670 f6f82670 00000000 00000002 f6fafe9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.264510] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.264563]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.264618]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.264677]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.264733]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.264788]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.264845]  [<c04ea5bb>] ? sys_send+0x3b/0x40
Mar 21 09:10:14 t00l kernel: [   28.264902]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.264958]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.265015]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.265072]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.265127] udevd         D 0000a6b5     0   183     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.265248]  f6fb1e88 00000082 f6fb2000 0000a6b5 00000000 c08b1440 f6f835ec c08b1440
Mar 21 09:10:14 t00l kernel: [   28.265575]  e495eb7b 00000001 c08b1440 c08b1440 f6f835ec c08b1440 c08b1440 f6ee5340
Mar 21 09:10:14 t00l kernel: [   28.265904]  00000000 00000001 f6f83340 f6f83340 00000000 00000002 f6fb1e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.266234] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.266287]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.266343]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.266403]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.266459]  [<c01714af>] ? __remove_hrtimer+0x2f/0xa0
Mar 21 09:10:14 t00l kernel: [   28.266516]  [<c0171838>] ? lock_hrtimer_base+0x28/0x50
Mar 21 09:10:14 t00l kernel: [   28.266573]  [<c0172606>] ? hrtimer_try_to_cancel+0x36/0xb0
Mar 21 09:10:14 t00l kernel: [   28.266631]  [<c04ea5bb>] ? sys_send+0x3b/0x40
Mar 21 09:10:14 t00l kernel: [   28.266687]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.266744]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.266800]  [<c0156fe4>] ? alarm_setitimer+0x34/0x70
Mar 21 09:10:14 t00l kernel: [   28.266857]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.266914]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.266969] udevd         D 0000a3b4     0   184     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.267092]  f6fb3e88 00000086 f6fb4000 0000a3b4 00000000 c08b1440 f6f842bc c08b1440
Mar 21 09:10:14 t00l kernel: [   28.267420]  e495f6d5 00000001 c08b1440 c08b1440 f6f842bc c08b1440 c08b1440 f6ee5500
Mar 21 09:10:14 t00l kernel: [   28.267748]  00000000 00000001 f6f84010 f6f84010 00000000 00000002 f6fb3e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.268083] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.268136]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.268193]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.268252]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.268308]  [<c01714af>] ? __remove_hrtimer+0x2f/0xa0
Mar 21 09:10:14 t00l kernel: [   28.268365]  [<c0171838>] ? lock_hrtimer_base+0x28/0x50
Mar 21 09:10:14 t00l kernel: [   28.268422]  [<c0172606>] ? hrtimer_try_to_cancel+0x36/0xb0
Mar 21 09:10:14 t00l kernel: [   28.268480]  [<c04ea5bb>] ? sys_send+0x3b/0x40
Mar 21 09:10:14 t00l kernel: [   28.268536]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.268593]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.268650]  [<c0156fe4>] ? alarm_setitimer+0x34/0x70
Mar 21 09:10:14 t00l kernel: [   28.268707]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.268763]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.268819] udevd         D 00009aee     0   185     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.268942]  f6fb5e88 00000086 f6e9a000 00009aee 00000000 c08b1440 f6f84f8c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.269271]  e496020c 00000001 c08b1440 c08b1440 f6f84f8c c08b1440 c08b1440 f6ee56c0
Mar 21 09:10:14 t00l kernel: [   28.269600]  00000000 00000001 f6f84ce0 f6f84ce0 00000000 00000002 f6fb5e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.269929] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.269981]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.270038]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.270097]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.270152]  [<c01714af>] ? __remove_hrtimer+0x2f/0xa0
Mar 21 09:10:14 t00l kernel: [   28.270210]  [<c0171838>] ? lock_hrtimer_base+0x28/0x50
Mar 21 09:10:14 t00l kernel: [   28.270268]  [<c0172606>] ? hrtimer_try_to_cancel+0x36/0xb0
Mar 21 09:10:14 t00l kernel: [   28.270327]  [<c04ea5bb>] ? sys_send+0x3b/0x40
Mar 21 09:10:14 t00l kernel: [   28.270383]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.270440]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.270496]  [<c0156fe4>] ? alarm_setitimer+0x34/0x70
Mar 21 09:10:14 t00l kernel: [   28.270553]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.270610]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.270665] udevd         D 0000b07e     0   186     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.270787]  f6e9be88 00000082 f6fb6000 0000b07e 00000000 c08b1440 f6f85c5c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.271116]  e4960dc0 00000001 c08b1440 c08b1440 f6f85c5c c08b1440 c08b1440 f6ee5880
Mar 21 09:10:14 t00l kernel: [   28.271443]  00000000 00000001 f6f859b0 f6f859b0 00000000 00000002 f6e9be9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.271773] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.271825]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.271882]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.271940]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.271997]  [<c01714af>] ? __remove_hrtimer+0x2f/0xa0
Mar 21 09:10:14 t00l kernel: [   28.272064]  [<c0171838>] ? lock_hrtimer_base+0x28/0x50
Mar 21 09:10:14 t00l kernel: [   28.272121]  [<c0172606>] ? hrtimer_try_to_cancel+0x36/0xb0
Mar 21 09:10:14 t00l kernel: [   28.272180]  [<c04ea5bb>] ? sys_send+0x3b/0x40
Mar 21 09:10:14 t00l kernel: [   28.272236]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.272294]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.272350]  [<c0156fe4>] ? alarm_setitimer+0x34/0x70
Mar 21 09:10:14 t00l kernel: [   28.272408]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.272465]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.272520] udevd         D 00006ed4     0   187     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.272643]  f6fb7e88 00000082 f6e94000 00006ed4 00000000 c08b1440 f6f8692c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.272971]  e496182f 00000001 c08b1440 c08b1440 f6f8692c c08b1440 c08b1440 f6ee5a40
Mar 21 09:10:14 t00l kernel: [   28.273299]  00000000 00000001 f6f86680 f6f86680 00000000 00000002 f6fb7e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.273628] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.273681]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.273738]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.273797]  [<c0136198>] ? ptep_set_access_flags+0x58/0x70
Mar 21 09:10:14 t00l kernel: [   28.273856]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.273912]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.273969]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.274027]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.274084]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.274140]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.274196]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.274252] udevd         D 00009f1c     0   188     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.274374]  f6e95e88 00000086 f6fd6000 00009f1c 00000000 c08b1440 f6f2b5ec c08b1440
Mar 21 09:10:14 t00l kernel: [   28.274704]  e49623b1 00000001 c08b1440 c08b1440 f6f2b5ec c08b1440 c08b1440 f6ee5c00
Mar 21 09:10:14 t00l kernel: [   28.275033]  00000000 00000001 f6f2b340 f6f2b340 00000000 00000002 f6e95e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.275359] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.275413]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.275470]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.275529]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.275585]  [<c01714af>] ? __remove_hrtimer+0x2f/0xa0
Mar 21 09:10:14 t00l kernel: [   28.275642]  [<c0171838>] ? lock_hrtimer_base+0x28/0x50
Mar 21 09:10:14 t00l kernel: [   28.275700]  [<c0172606>] ? hrtimer_try_to_cancel+0x36/0xb0
Mar 21 09:10:14 t00l kernel: [   28.275758]  [<c04ea5bb>] ? sys_send+0x3b/0x40
Mar 21 09:10:14 t00l kernel: [   28.275814]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.275870]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.275925]  [<c0156fe4>] ? alarm_setitimer+0x34/0x70
Mar 21 09:10:14 t00l kernel: [   28.275982]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.276047]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.276103] udevd         D 00009c8a     0   189     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.276226]  f6fd7e88 00000086 f680a000 00009c8a 00000000 c08b1440 f6f2a91c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.276551]  e4962f25 00000001 c08b1440 c08b1440 f6f2a91c c08b1440 c08b1440 f6ee5dc0
Mar 21 09:10:14 t00l kernel: [   28.276878]  00000000 00000001 f6f2a670 f6f2a670 00000000 00000002 f6fd7e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.277210] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.277262]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.277318]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.277377]  [<c0136198>] ? ptep_set_access_flags+0x58/0x70
Mar 21 09:10:14 t00l kernel: [   28.277436]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.277492]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.277550]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.277608]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.277665]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.277721]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.277777]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.277832] udevd         D 0000a840     0   190     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.277954]  f680be88 00000082 f680c000 0000a840 00000000 c08b1440 f68102ac c08b1440
Mar 21 09:10:14 t00l kernel: [   28.278283]  e4963af7 00000001 c08b1440 c08b1440 f68102ac c08b1440 c08b1440 f6f30a80
Mar 21 09:10:14 t00l kernel: [   28.278611]  00000000 00000001 f6810000 f6810000 00000000 00000002 f680be9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.279722] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.279775]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.279831]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.279891]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.279947]  [<c01714af>] ? __remove_hrtimer+0x2f/0xa0
Mar 21 09:10:14 t00l kernel: [   28.280013]  [<c0171838>] ? lock_hrtimer_base+0x28/0x50
Mar 21 09:10:14 t00l kernel: [   28.280071]  [<c0172606>] ? hrtimer_try_to_cancel+0x36/0xb0
Mar 21 09:10:14 t00l kernel: [   28.280130]  [<c04ea5bb>] ? sys_send+0x3b/0x40
Mar 21 09:10:14 t00l kernel: [   28.280184]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.280241]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.280297]  [<c0156fe4>] ? alarm_setitimer+0x34/0x70
Mar 21 09:10:14 t00l kernel: [   28.280353]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.280409]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.280465] udevd         D 000078de     0   191     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.280586]  f680de88 00000086 f6838000 000078de 00000000 c08b1440 f6810f7c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.280917]  e4964706 00000001 c08b1440 c08b1440 f6810f7c c08b1440 c08b1440 f680e000
Mar 21 09:10:14 t00l kernel: [   28.281245]  00000000 00000001 f6810cd0 f6810cd0 00000000 00000002 f680de9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.281576] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.281629]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.281686]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.281746]  [<c0136198>] ? ptep_set_access_flags+0x58/0x70
Mar 21 09:10:14 t00l kernel: [   28.281805]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.281861]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.281919]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.281977]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.282035]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.282092]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.282148]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.282202] udevd         D 0000872a     0   192     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.282324]  f6839e88 00000086 f683a000 0000872a 00000000 c08b1440 f6811c4c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.282653]  e4965247 00000001 c08b1440 c08b1440 f6811c4c c08b1440 c08b1440 f680e1c0
Mar 21 09:10:14 t00l kernel: [   28.282981]  00000000 00000001 f68119a0 f68119a0 00000000 00000002 f6839e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.283308] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.283362]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.283418]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.283477]  [<c0136198>] ? ptep_set_access_flags+0x58/0x70
Mar 21 09:10:14 t00l kernel: [   28.283535]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.283589]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.283647]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.283705]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.283761]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.283818]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.283874]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.283930] udevd         D 00008c89     0   193     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.284062]  f683be88 00000082 f6f14000 00008c89 00000000 c08b1440 f681291c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.284390]  e4965df6 00000001 c08b1440 c08b1440 f681291c c08b1440 c08b1440 f680e380
Mar 21 09:10:14 t00l kernel: [   28.284715]  00000000 00000001 f6812670 f6812670 00000000 00000002 f683be9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.285042] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.285095]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.285151]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.285210]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.285266]  [<c01714af>] ? __remove_hrtimer+0x2f/0xa0
Mar 21 09:10:14 t00l kernel: [   28.285324]  [<c0171838>] ? lock_hrtimer_base+0x28/0x50
Mar 21 09:10:14 t00l kernel: [   28.285381]  [<c0172606>] ? hrtimer_try_to_cancel+0x36/0xb0
Mar 21 09:10:14 t00l kernel: [   28.285439]  [<c04ea5bb>] ? sys_send+0x3b/0x40
Mar 21 09:10:14 t00l kernel: [   28.285496]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.285553]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.285609]  [<c0156fe4>] ? alarm_setitimer+0x34/0x70
Mar 21 09:10:14 t00l kernel: [   28.285665]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.285722]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.285778] udevd         D 000091a2     0   194     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.285899]  f6f15e88 00000082 f6f16000 000091a2 00000000 c08b1440 f68135ec c08b1440
Mar 21 09:10:14 t00l kernel: [   28.286229]  e4966a4b 00000001 c08b1440 c08b1440 f68135ec c08b1440 c08b1440 f680e540
Mar 21 09:10:14 t00l kernel: [   28.286555]  00000000 00000001 f6813340 f6813340 00000000 00000002 f6f15e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.286885] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.286938]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.286994]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.287054]  [<c0136198>] ? ptep_set_access_flags+0x58/0x70
Mar 21 09:10:14 t00l kernel: [   28.287113]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.287168]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.287225]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.287283]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.287340]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.287396]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.287452]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.287507] udevd         D 000061a7     0   195     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.287631]  f6f17e88 00000086 f683c000 000061a7 00000000 c08b1440 f68142bc c08b1440
Mar 21 09:10:14 t00l kernel: [   28.287961]  e49675c8 00000001 c08b1440 c08b1440 f68142bc c08b1440 c08b1440 f680e700
Mar 21 09:10:14 t00l kernel: [   28.288299]  00000000 00000001 f6814010 f6814010 00000000 00000002 f6f17e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.288627] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.288680]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.288736]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.288795]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.288852]  [<c01eccd8>] ? handle_mm_fault+0x198/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.288910]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.288967]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.289022]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.289079]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.289134] udevd         D 0000950c     0   196     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.289255]  f683de88 00000086 f683e000 0000950c 00000000 c08b1440 f6814f8c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.289584]  e496815f 00000001 c08b1440 c08b1440 f6814f8c c08b1440 c08b1440 f680e8c0
Mar 21 09:10:14 t00l kernel: [   28.289914]  00000000 00000001 f6814ce0 f6814ce0 00000000 00000002 f683de9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.290243] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.290294]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.290349]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.290409]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.290465]  [<c01380c4>] ? kmap_atomic+0x24/0x30
Mar 21 09:10:14 t00l kernel: [   28.290521]  [<c01ecf1f>] ? handle_mm_fault+0x3df/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.290580]  [<c04ea5bb>] ? sys_send+0x3b/0x40
Mar 21 09:10:14 t00l kernel: [   28.290636]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.290693]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.290750]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.290807]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.290862] udevd         D 00004e90     0   206     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.290985]  f683fe88 00000082 f68d6000 00004e90 00000000 c08b1440 f6815c5c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.291317]  e4968d9b 00000001 c08b1440 c08b1440 f6815c5c c08b1440 c08b1440 f680ea80
Mar 21 09:10:14 t00l kernel: [   28.291645]  00000000 00000001 f68159b0 f68159b0 00000000 00000002 f683fe9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.291974] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.292036]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.292093]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.292152]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.292209]  [<c01eccd8>] ? handle_mm_fault+0x198/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.292268]  [<c04ea5bb>] ? sys_send+0x3b/0x40
Mar 21 09:10:14 t00l kernel: [   28.292324]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.292381]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.292437]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.292494]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.292549] udevd         D 00008eab     0   245     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.292671]  f68d7e88 00000082 f68f8000 00008eab 00000000 c08b1440 f68a5c5c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.293000]  e49699cc 00000001 c08b1440 c08b1440 f68a5c5c c08b1440 c08b1440 f68caa80
Mar 21 09:10:14 t00l kernel: [   28.293327]  00000000 00000001 f68a59b0 f68a59b0 00000000 00000002 f68d7e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.293651] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.293704]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.293761]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.293821]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.293877]  [<c01eccd8>] ? handle_mm_fault+0x198/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.293936]  [<c04ea5bb>] ? sys_send+0x3b/0x40
Mar 21 09:10:14 t00l kernel: [   28.293993]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.294050]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.294105]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.294163]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.294218] udevd         D 00005b7b     0   246     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.294340]  f68f9e88 00000082 f68fa000 00005b7b 00000000 c08b1440 f68a692c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.294668]  e496a53f 00000001 c08b1440 c08b1440 f68a692c c08b1440 c08b1440 f68cac40
Mar 21 09:10:14 t00l kernel: [   28.294998]  00000000 00000001 f68a6680 f68a6680 00000000 00000002 f68f9e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.295328] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.295381]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.295438]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.295497]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.295554]  [<c01eccd8>] ? handle_mm_fault+0x198/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.295613]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.295669]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.295726]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.295782]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.295838] udevd         D 00004ed0     0   247     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.295961]  f68fbe88 00000086 f6910000 00004ed0 00000000 c08b1440 f69002ac c08b1440
Mar 21 09:10:14 t00l kernel: [   28.296301]  e496b112 00000001 c08b1440 c08b1440 f69002ac c08b1440 c08b1440 f68cae00
Mar 21 09:10:14 t00l kernel: [   28.296630]  00000000 00000001 f6900000 f6900000 00000000 00000002 f68fbe9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.296959] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.297012]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.297851]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.297909]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.297966]  [<c01eccd8>] ? handle_mm_fault+0x198/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.298025]  [<c04ea5bb>] ? sys_send+0x3b/0x40
Mar 21 09:10:14 t00l kernel: [   28.298081]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.298138]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.298195]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.298251]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.298306] udevd         D 000050f5     0   248     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.298429]  f6911e88 00000086 f6912000 000050f5 00000000 c08b1440 f6900f7c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.298758]  e496bbdb 00000001 c08b1440 c08b1440 f6900f7c c08b1440 c08b1440 f68cafc0
Mar 21 09:10:14 t00l kernel: [   28.299087]  00000000 00000001 f6900cd0 f6900cd0 00000000 00000002 f6911e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.299414] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.299466]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.299522]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.299581]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.299638]  [<c01eccd8>] ? handle_mm_fault+0x198/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.299696]  [<c04ea5bb>] ? sys_send+0x3b/0x40
Mar 21 09:10:14 t00l kernel: [   28.299751]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.299808]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.299865]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.299921]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.299976] udevd         D 0000733f     0   249     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.300107]  f6913e88 00000082 f6914000 0000733f 00000000 c08b1440 f6901c4c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.300435]  e496c7a3 00000001 c08b1440 c08b1440 f6901c4c c08b1440 c08b1440 f68cb180
Mar 21 09:10:14 t00l kernel: [   28.300763]  00000000 00000001 f69019a0 f69019a0 00000000 00000002 f6913e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.301093] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.301145]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.301201]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.301259]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.301315]  [<c01eccd8>] ? handle_mm_fault+0x198/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.301374]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.301432]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.301488]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.301543]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.301598] udevd         D 000056e6     0   250     78 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.301720]  f6915e88 00000082 f688e000 000056e6 00000000 c08b1440 f690291c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.302048]  e496d2d6 00000001 c08b1440 c08b1440 f690291c c08b1440 c08b1440 f68cb340
Mar 21 09:10:14 t00l kernel: [   28.302377]  00000000 00000001 f6902670 f6902670 00000000 00000002 f6915e9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.302705] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.302758]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.302815]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.302875]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.302931]  [<c01eccd8>] ? handle_mm_fault+0x198/0x4a0
Mar 21 09:10:14 t00l kernel: [   28.302988]  [<c04ea5bb>] ? sys_send+0x3b/0x40
Mar 21 09:10:14 t00l kernel: [   28.303044]  [<c0162e4e>] ? sigprocmask+0x7e/0x100
Mar 21 09:10:14 t00l kernel: [   28.303101]  [<c021f4fe>] ? sys_ppoll+0x5e/0x120
Mar 21 09:10:14 t00l kernel: [   28.303157]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.303214]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.303269] resume        D 0001c1fb     0   314      1 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.303391]  f688fe88 00000086 f6db2000 0001c1fb 00000000 c08b1440 f68a0f7c c08b1440
Mar 21 09:10:14 t00l kernel: [   28.303721]  e496d973 00000001 c08b1440 c08b1440 f68a0f7c c08b1440 c08b1440 f6ee48c0
Mar 21 09:10:14 t00l kernel: [   28.304060]  00000000 00000001 f68a0cd0 f68a0cd0 00000000 00000002 f688fe9c c0175ccd
Mar 21 09:10:14 t00l kernel: [   28.304390] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.304443]  [<c0175ccd>] refrigerator+0xad/0xe0
Mar 21 09:10:14 t00l kernel: [   28.304500]  [<c0165e5d>] get_signal_to_deliver+0x23d/0x3c0
Mar 21 09:10:14 t00l kernel: [   28.304590]  [<c0145273>] ? finish_task_switch+0x43/0xc0
Mar 21 09:10:14 t00l kernel: [   28.304648]  [<c01094c3>] do_signal+0x73/0x170
Mar 21 09:10:14 t00l kernel: [   28.304706]  [<c0130ad8>] ? default_spin_lock_flags+0x8/0x10
Mar 21 09:10:14 t00l kernel: [   28.304764]  [<c05c410f>] ? _spin_lock_irqsave+0x2f/0x50
Mar 21 09:10:14 t00l kernel: [   28.304821]  [<c016e401>] ? remove_wait_queue+0x41/0x50
Mar 21 09:10:14 t00l kernel: [   28.304878]  [<c0155fa3>] ? do_wait+0x173/0x210
Mar 21 09:10:14 t00l kernel: [   28.304934]  [<c01560c9>] ? sys_wait4+0x89/0xc0
Mar 21 09:10:14 t00l kernel: [   28.304991]  [<c0154180>] ? child_wait_callback+0x0/0x90
Mar 21 09:10:14 t00l kernel: [   28.305048]  [<c0109615>] do_notify_resume+0x55/0x80
Mar 21 09:10:14 t00l kernel: [   28.305104]  [<c01098e8>] work_notifysig+0x13/0x1b
Mar 21 09:10:14 t00l kernel: [   28.305161] resume        R running      0   316    314 0x00000000
Mar 21 09:10:14 t00l kernel: [   28.305283]  00000000 00000000 00000001 f6db3e2b f6db3e1c f68a19a0 f68a19a0 00000000
Mar 21 09:10:14 t00l kernel: [   28.305612]  f6db3e4c c010ce13 00000000 c0733299 f6db3e70 c01439d0 c0700d8e 00000000
Mar 21 09:10:14 t00l kernel: [   28.305942]  0000013c 0000013a 00000000 f68a19a0 f68a19a0 f6db3e88 c014946e c07078f8
Mar 21 09:10:14 t00l kernel: [   28.306273] Call Trace:
Mar 21 09:10:14 t00l kernel: [   28.306325]  [<c010ce13>] ? show_stack+0x23/0x30
Mar 21 09:10:14 t00l kernel: [   28.306381]  [<c01439d0>] ? sched_show_task+0xa0/0x100
Mar 21 09:10:14 t00l kernel: [   28.306439]  [<c014946e>] ? show_state_filter+0x5e/0xa0
Mar 21 09:10:14 t00l kernel: [   28.306497]  [<c0189d81>] ? try_to_freeze_tasks+0x1d1/0x260
Mar 21 09:10:14 t00l kernel: [   28.306556]  [<c0189e7b>] ? freeze_processes+0x6b/0x90
Mar 21 09:10:14 t00l kernel: [   28.306613]  [<c018a74d>] ? prepare_processes+0xd/0x40
Mar 21 09:10:14 t00l kernel: [   28.306671]  [<c018ad5e>] ? software_resume+0x15e/0x1f0
Mar 21 09:10:14 t00l kernel: [   28.306729]  [<c018ae86>] ? resume_store+0x96/0xa0
Mar 21 09:10:14 t00l kernel: [   28.306786]  [<c018adf0>] ? resume_store+0x0/0xa0
Mar 21 09:10:14 t00l kernel: [   28.306842]  [<c0351950>] ? kobj_attr_store+0x20/0x30
Mar 21 09:10:14 t00l kernel: [   28.306898]  [<c0265415>] ? sysfs_write_file+0x95/0x100
Mar 21 09:10:14 t00l kernel: [   28.306957]  [<c020f2c2>] ? vfs_write+0xa2/0x1a0
Mar 21 09:10:14 t00l kernel: [   28.307013]  [<c0265380>] ? sysfs_write_file+0x0/0x100
Mar 21 09:10:14 t00l kernel: [   28.307071]  [<c020fbe2>] ? sys_write+0x42/0x70
Mar 21 09:10:14 t00l kernel: [   28.307127]  [<c010980c>] ? syscall_call+0x7/0xb
Mar 21 09:10:14 t00l kernel: [   28.307184] Sched Debug Version: v0.09, 2.6.32-16-generic-pae #25-Ubuntu
Mar 21 09:10:14 t00l kernel: [   28.307242] now at 28307.184035 msecs
Mar 21 09:10:14 t00l kernel: [   28.307296]   .jiffies                                 : 4294899372
Mar 21 09:10:14 t00l kernel: [   28.307355]   .sysctl_sched_latency                    : 5.000000
Mar 21 09:10:14 t00l kernel: [   28.307412]   .sysctl_sched_min_granularity            : 1.000000
Mar 21 09:10:14 t00l kernel: [   28.307470]   .sysctl_sched_wakeup_granularity         : 1.000000
Mar 21 09:10:14 t00l kernel: [   28.307527]   .sysctl_sched_child_runs_first           : 0.000000
Mar 21 09:10:14 t00l kernel: [   28.307584]   .sysctl_sched_features                   : 15834235
Mar 21 09:10:14 t00l kernel: [   28.307641]
Mar 21 09:10:14 t00l kernel: [   28.307642] cpu#0, 1396.610 MHz
Mar 21 09:10:14 t00l kernel: [   28.307741]   .nr_running                    : 1
Mar 21 09:10:14 t00l kernel: [   28.307795]   .load                          : 1024
Mar 21 09:10:14 t00l kernel: [   28.307849]   .nr_switches                   : 3089
Mar 21 09:10:14 t00l kernel: [   28.307904]   .nr_load_updates               : 5535
Mar 21 09:10:14 t00l kernel: [   28.307958]   .nr_uninterruptible            : 1
Mar 21 09:10:14 t00l kernel: [   28.308022]   .next_balance                  : 4294.894421
Mar 21 09:10:14 t00l kernel: [   28.308078]   .curr->pid                     : 316
Mar 21 09:10:14 t00l kernel: [   28.308133]   .clock                         : 28308.019133
Mar 21 09:10:14 t00l kernel: [   28.308189]   .cpu_load[0]                   : 1024
Mar 21 09:10:14 t00l kernel: [   28.308244]   .cpu_load[1]                   : 1024
Mar 21 09:10:14 t00l kernel: [   28.308299]   .cpu_load[2]                   : 1024
Mar 21 09:10:14 t00l kernel: [   28.308354]   .cpu_load[3]                   : 1024
Mar 21 09:10:14 t00l kernel: [   28.308409]   .cpu_load[4]                   : 1024
Mar 21 09:10:14 t00l kernel: [   28.308464]   .yld_count                     : 9139291
Mar 21 09:10:14 t00l kernel: [   28.308519]   .sched_switch                  : 0
Mar 21 09:10:14 t00l kernel: [   28.308573]   .sched_count                   : 9142379
Mar 21 09:10:14 t00l kernel: [   28.308627]   .sched_goidle                  : 183
Mar 21 09:10:14 t00l kernel: [   28.308681]   .avg_idle                      : 788060
Mar 21 09:10:14 t00l kernel: [   28.308737]   .ttwu_count                    : 1665
Mar 21 09:10:14 t00l kernel: [   28.308792]   .ttwu_local                    : 1665
Mar 21 09:10:14 t00l kernel: [   28.308847]   .bkl_count                     : 166
Mar 21 09:10:14 t00l kernel: [   28.308903]
Mar 21 09:10:14 t00l kernel: [   28.308903] cfs_rq[0]:/
Mar 21 09:10:14 t00l kernel: [   28.309000]   .exec_clock                    : 21451.291219
Mar 21 09:10:14 t00l kernel: [   28.309057]   .MIN_vruntime                  : 0.000001
Mar 21 09:10:14 t00l kernel: [   28.309112]   .min_vruntime                  : 20921.417011
Mar 21 09:10:14 t00l kernel: [   28.309169]   .max_vruntime                  : 0.000001
Mar 21 09:10:14 t00l kernel: [   28.309225]   .spread                        : 0.000000
Mar 21 09:10:14 t00l kernel: [   28.309281]   .spread0                       : 0.000000
Mar 21 09:10:14 t00l kernel: [   28.309337]   .nr_running                    : 1
Mar 21 09:10:14 t00l kernel: [   28.309390]   .load                          : 1024
Mar 21 09:10:14 t00l kernel: [   28.309445]   .nr_spread_over                : 44
Mar 21 09:10:14 t00l kernel: [   28.309499]   .shares                        : 0
Mar 21 09:10:14 t00l kernel: [   28.309555]
Mar 21 09:10:14 t00l kernel: [   28.309555] rt_rq[0]:/
Mar 21 09:10:14 t00l kernel: [   28.309652]   .rt_nr_running                 : 0
Mar 21 09:10:14 t00l kernel: [   28.309706]   .rt_throttled                  : 0
Mar 21 09:10:14 t00l kernel: [   28.309761]   .rt_time                       : 0.000000
Mar 21 09:10:14 t00l kernel: [   28.309817]   .rt_runtime                    : 950.000000
Mar 21 09:10:14 t00l kernel: [   28.309873]
Mar 21 09:10:14 t00l kernel: [   28.309874] runnable tasks:
Mar 21 09:10:14 t00l kernel: [   28.309875]             task   PID         tree-key  switches  prio     exec-runtime         sum-exec        sum-sleep
Mar 21 09:10:14 t00l kernel: [   28.309876] ----------------------------------------------------------------------------------------------------------
Mar 21 09:10:14 t00l kernel: [   28.310130] R         resume   316     20921.417011        37   120     20921.417011     20178.366419         0.191099 /
Mar 21 09:10:14 t00l kernel: [   28.310339]
Mar 21 09:10:14 t00l kernel: [   28.310389]  khubd
Mar 21 09:10:14 t00l kernel: [   28.310442]


```

---

### Post by ranch hand on 2010-03-21
A Lynx is cat.   I may be wrong but  I do not think that there are any cats that hibernate.

They generally just take cat naps.

We tried to tell them that it should have been Lounge Lizard.

Lizards do hibernate.

Not real sorry but I just could not resist.

---

### Post by megaexception on 2010-03-21
it looks like my problem is related to this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/499940](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/499940)


for now, i've added resume=/dev/sda2 option in grub.cfg, and hibernate is working .


p.s. ranch hand: i cannot get what are talking about.

---

### Post by autark on 2010-03-21
> **megaexception said:**
> it looks like my problem is related to this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/499940](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/499940)
for now, i've added resume=/dev/sda2 option in grub.cfg, and hibernate is working .

But that bug is supposed to be fixed by now. Assuming you are running a fully updated system, I suggest you add a comment to the bug, explaining your problem in detail.

---

