---
title: "Upgraded to mainline kernel ppa 2.6.33 - machine freeze"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by nevbear666 on 2010-02-26
Dear ladies and gentleman

i am having quite a problem after upgrading my karmic to an 2.6.33 kernel and trying to do an nfs transfer.

the nfs transfer bugs out in (and then freezes the box totally up, so that only pressing the reboot button on the pc itself helps anymore):

```

Feb 26 22:31:24 localhost kernel: [ 3964.123290] INFO: task rdesktop:10331 blocked for more than 120 seconds.
Feb 26 22:31:24 localhost kernel: [ 3964.123292] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Feb 26 22:31:24 localhost kernel: [ 3964.123294] rdesktop      D ffff880028215bc0     0 10331  10330 0x00000000
Feb 26 22:31:24 localhost kernel: [ 3964.123297]  ffff880017ce71b8 0000000000000082 ffffffff8154024e ffff880017ce7fd8
Feb 26 22:31:24 localhost kernel: [ 3964.123300]  ffff8801294e44a0 0000000000015bc0 0000000000015bc0 ffff880017ce7fd8
Feb 26 22:31:24 localhost kernel: [ 3964.123302]  0000000000015bc0 ffff880017ce7fd8 0000000000015bc0 ffff8801294e44a0
Feb 26 22:31:24 localhost kernel: [ 3964.123305] Call Trace:
Feb 26 22:31:24 localhost kernel: [ 3964.123308]  [<ffffffff8154024e>] ? common_interrupt+0xe/0x13
Feb 26 22:31:24 localhost kernel: [ 3964.123310]  [<ffffffff8153de82>] io_schedule+0x42/0x60
Feb 26 22:31:24 localhost kernel: [ 3964.123318]  [<ffffffffa0c6eff9>] nfs_wait_bit_uninterruptible+0x9/0x10 [nfs]
Feb 26 22:31:24 localhost kernel: [ 3964.123321]  [<ffffffff8153e635>] __wait_on_bit+0x55/0x80
Feb 26 22:31:24 localhost kernel: [ 3964.123329]  [<ffffffffa0c6eff0>] ? nfs_wait_bit_uninterruptible+0x0/0x10 [nfs]
Feb 26 22:31:24 localhost kernel: [ 3964.123337]  [<ffffffffa0c6eff0>] ? nfs_wait_bit_uninterruptible+0x0/0x10 [nfs]
Feb 26 22:31:24 localhost kernel: [ 3964.123340]  [<ffffffff8153e6d8>] out_of_line_wait_on_bit+0x78/0x90
Feb 26 22:31:24 localhost kernel: [ 3964.123343]  [<ffffffff81079d40>] ? wake_bit_function+0x0/0x30
Feb 26 22:31:24 localhost kernel: [ 3964.123351]  [<ffffffffa0c6efe8>] nfs_wait_on_request+0x28/0x30 [nfs]
Feb 26 22:31:24 localhost kernel: [ 3964.123359]  [<ffffffffa0c731e9>] nfs_wait_on_requests_locked+0x79/0xd0 [nfs]
Feb 26 22:31:24 localhost kernel: [ 3964.123361]  [<ffffffff810bd0a0>] ? call_rcu_sched+0x10/0x20
Feb 26 22:31:24 localhost kernel: [ 3964.123370]  [<ffffffffa0c742a3>] nfs_sync_mapping_wait+0xb3/0x140 [nfs]
Feb 26 22:31:24 localhost kernel: [ 3964.123379]  [<ffffffffa0c743b6>] nfs_wb_page_priority+0x86/0xe0 [nfs]
Feb 26 22:31:24 localhost kernel: [ 3964.123387]  [<ffffffffa0c7441e>] nfs_wb_page+0xe/0x10 [nfs]
Feb 26 22:31:24 localhost kernel: [ 3964.123394]  [<ffffffffa0c63a05>] nfs_release_page+0x35/0x60 [nfs]
Feb 26 22:31:24 localhost kernel: [ 3964.123397]  [<ffffffff810e40bb>] try_to_release_page+0x2b/0x40
Feb 26 22:31:24 localhost kernel: [ 3964.123399]  [<ffffffff810f0ca9>] shrink_page_list+0x4a9/0x540
Feb 26 22:31:24 localhost kernel: [ 3964.123402]  [<ffffffff810f12a5>] shrink_inactive_list+0x295/0x680
Feb 26 22:31:24 localhost kernel: [ 3964.123405]  [<ffffffff81047210>] ? __enqueue_entity+0x80/0x90
Feb 26 22:31:24 localhost kernel: [ 3964.123408]  [<ffffffff810f16e1>] shrink_list+0x51/0xa0
Feb 26 22:31:24 localhost kernel: [ 3964.123410]  [<ffffffff810f18f9>] shrink_zone+0x1c9/0x1e0
Feb 26 22:31:24 localhost kernel: [ 3964.123413]  [<ffffffff810f2423>] shrink_zones+0x63/0xf0
Feb 26 22:31:24 localhost kernel: [ 3964.123415]  [<ffffffff810f2520>] do_try_to_free_pages+0x70/0x270
Feb 26 22:31:24 localhost kernel: [ 3964.123418]  [<ffffffff810e9e4b>] ? get_page_from_freelist+0x2db/0x450
Feb 26 22:31:24 localhost kernel: [ 3964.123421]  [<ffffffff810f2960>] try_to_free_pages+0xa0/0xc0
Feb 26 22:31:24 localhost kernel: [ 3964.123423]  [<ffffffff810f0fc0>] ? isolate_pages_global+0x0/0x50
Feb 26 22:31:24 localhost kernel: [ 3964.123426]  [<ffffffff810ea21d>] __alloc_pages_slowpath+0x25d/0x540
Feb 26 22:31:24 localhost kernel: [ 3964.123429]  [<ffffffff81030899>] ? default_spin_lock_flags+0x9/0x10
Feb 26 22:31:24 localhost kernel: [ 3964.123432]  [<ffffffff810ea646>] __alloc_pages_nodemask+0x146/0x180
Feb 26 22:31:24 localhost kernel: [ 3964.123435]  [<ffffffff8107a0d9>] ? add_wait_queue+0x49/0x60
Feb 26 22:31:24 localhost kernel: [ 3964.123438]  [<ffffffff8111d228>] kmalloc_large_node+0x68/0xc0
Feb 26 22:31:24 localhost kernel: [ 3964.123440]  [<ffffffff81120b4a>] __kmalloc_node_track_caller+0x11a/0x180
Feb 26 22:31:24 localhost kernel: [ 3964.123443]  [<ffffffff8143b15f>] ? sock_alloc_send_pskb+0xdf/0x240
Feb 26 22:31:24 localhost kernel: [ 3964.123445]  [<ffffffff8143e8d6>] __alloc_skb+0x76/0x180
Feb 26 22:31:24 localhost kernel: [ 3964.123448]  [<ffffffff8143b15f>] sock_alloc_send_pskb+0xdf/0x240
Feb 26 22:31:24 localhost kernel: [ 3964.123450]  [<ffffffff8143b2d0>] sock_alloc_send_skb+0x10/0x20
Feb 26 22:31:24 localhost kernel: [ 3964.123453]  [<ffffffff814c8690>] unix_stream_sendmsg+0x280/0x380
Feb 26 22:31:24 localhost kernel: [ 3964.123456]  [<ffffffff81437f16>] do_sock_write+0xc6/0xe0
Feb 26 22:31:24 localhost kernel: [ 3964.123458]  [<ffffffff81437f9b>] sock_aio_write+0x6b/0x70
Feb 26 22:31:24 localhost kernel: [ 3964.123460]  [<ffffffff81439e12>] ? sock_common_recvmsg+0x32/0x50
Feb 26 22:31:24 localhost kernel: [ 3964.123463]  [<ffffffff81437f30>] ? sock_aio_write+0x0/0x70
Feb 26 22:31:24 localhost kernel: [ 3964.123465]  [<ffffffff8112b8cb>] do_sync_readv_writev+0xcb/0x110
Feb 26 22:31:24 localhost kernel: [ 3964.123468]  [<ffffffff8122e511>] ? security_file_permission+0x11/0x20
Feb 26 22:31:24 localhost kernel: [ 3964.123470]  [<ffffffff8112c5db>] do_readv_writev+0xcb/0x1e0
Feb 26 22:31:24 localhost kernel: [ 3964.123473]  [<ffffffff8112c729>] vfs_writev+0x39/0x60
Feb 26 22:31:24 localhost kernel: [ 3964.123475]  [<ffffffff8112c860>] sys_writev+0x50/0xb0
Feb 26 22:31:24 localhost kernel: [ 3964.123478]  [<ffffffff81009f02>] system_call_fastpath+0x16/0x1b

```

the hardware is brand new, and tested to be ok, i did a memtest, no errors, and i did hd checks, no errors either, the network cabling is ok too...

i got me the kernel i installed from here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/)

i got me the amd64 bins and installed it this way:
```

dpkg -i linux-headers-2.6.33-020633_2.6.33-020633_all.deb \
linux-headers-2.6.33-020633-generic_2.6.33-020633_amd64.deb \
linux-image-2.6.33-020633-generic_2.6.33-020633_amd64.deb \
linux-source-2.6.33_2.6.33-020633_all.deb

```

afterwards i had to upgrade my nvidia dkms to ppa version as well, by using this deb and deb-src:

```

deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu karmic main

```

the nfs transfer happens between this ubuntu karmic and a debian 5.0.4 stable with an nfs user server.

im transfering like that (on the ubuntu system):

```

mount servername:/mountpoint /mountdir -o nolock
mv /local/path/filename.iso /mountdir/subdir/

```

the exports file entry on the debian server looks like the following:

```

/mountpoint xxx.xxx.xxx.xxx(rw,crossmnt,insecure_locks,no_root_squash)

```

the grub2 kernel bootparams are as follows:

```

GRUB_CMDLINE_LINUX="noapic acpi=off"

```

```

a bit of hardware information:
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E7300  @ 2.66GHz
stepping	: 6
cpu MHz		: 2667.188
cache size	: 3072 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm
bogomips	: 5334.37
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 23
model name	: Intel(R) Core(TM)2 Duo CPU     E7300  @ 2.66GHz
stepping	: 6
cpu MHz		: 2667.188
cache size	: 3072 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm
bogomips	: 5333.63
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8400 GS] (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)

             total       used       free     shared    buffers     cached
Mem:          3962       3933         28          0        131       2890
-/+ buffers/cache:        911       3051
Swap:          956          0        956

```

thx in advance for taking the time to assist me in this.

---

### Post by schradt on 2010-02-27
I have the same issue with NFS (V3) transfers (file copy from client to server).
After 30-60GB transferred, the client transfer hangs (sometimes the hole system is frozen).

Kernel 2.6.32(.7) does work without problems (same config)

Hardware Clients: Lenovo T61/T400, 2,5/3Ghz Dualcore, 8GBRam, x64
Hardware Servers: some Dual Xeons, x64 and i386 tested

The issue is only with Kernel 2.6.33 (vanilla, self compiled).

---

### Post by Pencioner on 2010-02-27
Oh, yes, i've just compiled the 2.6.33 kernel from fresh source friday evening, on my local home gateway computer, and it was like all ok, but saturday morning i realized that the nfs mounts from other computer (there are karmic, latest generic ubuntu kernel package for 2.6.31) doesn't work. dmesg said me something like "server doesn't answer ..." or so (can't look now i'm transferring some partitions on that compy booted from live cd)

Can anyone figure are there troubles with kernel itself or maybe we need newer nfs-utils? (nfs-common and nfs-kernel-server are derived from nfs-utils 1.2.0 but it seems there are at least 1.2.1 in fedora packages)

---

### Post by nevbear666 on 2010-02-28
> **Pencioner said:**
>  ...
Can anyone figure are there troubles with kernel itself or maybe we need newer nfs-utils? (nfs-common and nfs-kernel-server are derived from nfs-utils 1.2.0 but it seems there are at least 1.2.1 in fedora packages)

it is definitely a kernel issue, i tried to transfer over samba, and after a while i got the same effect.

im currently testing some grub params that might have fixed it, will know in 1-2 days for sure...

---

### Post by Pencioner on 2010-02-28
Thanks for Your efforts. Though, i've just booted back into 2.6.32.9 and can't do any testing because that computer is gateway and sharing internet for wife as well... though i'd like to try quirk some kernel configurations as well (not just only kernel boot strings, kernel .config too)

---

### Post by schradt on 2010-03-05
Now I compiled 2.6.32.9 and I had the same freeze again! :confused:  With 2.6.32.7 I had no issues.

[FONT="Courier New"]
Mar  5 09:03:21 aix-162 kernel: [64800.280133] INFO: task kswapd0:346 blocked for more than 120 seconds.
Mar  5 09:03:21 aix-162 kernel: [64800.280141] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Mar  5 09:03:21 aix-162 kernel: [64800.280147] kswapd0       D ffff880028313800     0   346      2 0x00000000
Mar  5 09:03:21 aix-162 kernel: [64800.280158]  ffff880239023790 0000000000000046 ffff880239023758 ffff880239023754
Mar  5 09:03:21 aix-162 kernel: [64800.280169]  ffff880239023700 ffffffff8105fb6c ffff880239023fd8 ffff880239023fd8
Mar  5 09:03:21 aix-162 kernel: [64800.280178]  ffff88023b275d48 000000000000dce8 0000000000013800 ffff88023b275d48
Mar  5 09:03:21 aix-162 kernel: [64800.280187] Call Trace:
Mar  5 09:03:21 aix-162 kernel: [64800.280204]  [<ffffffff8105fb6c>] ? timekeeping_get_ns+0x16/0x38
Mar  5 09:03:21 aix-162 kernel: [64800.280214]  [<ffffffff8105fb6c>] ? timekeeping_get_ns+0x16/0x38
Mar  5 09:03:21 aix-162 kernel: [64800.280222]  [<ffffffff810602f4>] ? ktime_get_ts+0x80/0x89
Mar  5 09:03:21 aix-162 kernel: [64800.280262]  [<ffffffffa054ce53>] ? nfs_wait_bit_uninterruptible+0x0/0xd [nfs]
Mar  5 09:03:21 aix-162 kernel: [64800.280311]  [<ffffffffa054ce53>] ? nfs_wait_bit_uninterruptible+0x0/0xd [nfs]
Mar  5 09:03:21 aix-162 kernel: [64800.280325]  [<ffffffff81332d51>] io_schedule+0x3e/0x58
Mar  5 09:03:21 aix-162 kernel: [64800.280354]  [<ffffffffa054ce5c>] nfs_wait_bit_uninterruptible+0x9/0xd [nfs]
Mar  5 09:03:21 aix-162 kernel: [64800.280366]  [<ffffffff8133321b>] __wait_on_bit+0x43/0x76
Mar  5 09:03:21 aix-162 kernel: [64800.280377]  [<ffffffff811b27c3>] ? __lookup_tag+0xbd/0x12d
Mar  5 09:03:21 aix-162 kernel: [64800.280387]  [<ffffffff813332b7>] out_of_line_wait_on_bit+0x69/0x74
Mar  5 09:03:21 aix-162 kernel: [64800.280417]  [<ffffffffa054ce53>] ? nfs_wait_bit_uninterruptible+0x0/0xd [nfs]
Mar  5 09:03:21 aix-162 kernel: [64800.280430]  [<ffffffff8105943f>] ? wake_bit_function+0x0/0x2e
Mar  5 09:03:21 aix-162 kernel: [64800.280460]  [<ffffffffa054ce51>] nfs_wait_on_request+0x23/0x25 [nfs]
Mar  5 09:03:21 aix-162 kernel: [64800.280494]  [<ffffffffa0551037>] nfs_sync_mapping_wait+0xf0/0x211 [nfs]
Mar  5 09:03:21 aix-162 kernel: [64800.280529]  [<ffffffffa05511ea>] nfs_wb_page+0x92/0xc2 [nfs]
Mar  5 09:03:21 aix-162 kernel: [64800.280541]  [<ffffffff810aa905>] ? __dec_zone_page_state+0x29/0x2b
Mar  5 09:03:21 aix-162 kernel: [64800.280565]  [<ffffffffa0543ed2>] nfs_release_page+0x3c/0x4e [nfs]
Mar  5 09:03:21 aix-162 kernel: [64800.280576]  [<ffffffff810976e6>] try_to_release_page+0x2f/0x38
Mar  5 09:03:21 aix-162 kernel: [64800.280587]  [<ffffffff810a21aa>] shrink_page_list+0x2e2/0x47e
Mar  5 09:03:21 aix-162 kernel: [64800.280598]  [<ffffffff810a1298>] ? isolate_pages_global+0x19a/0x210
Mar  5 09:03:21 aix-162 kernel: [64800.280608]  [<ffffffff810a26cf>] shrink_inactive_list+0x389/0x651
Mar  5 09:03:21 aix-162 kernel: [64800.280619]  [<ffffffff811af17a>] ? cpumask_next_and+0x2c/0x39
Mar  5 09:03:21 aix-162 kernel: [64800.280629]  [<ffffffff8109eaf3>] ? determine_dirtyable_memory+0x15/0x28
Mar  5 09:03:21 aix-162 kernel: [64800.280638]  [<ffffffff8109eb75>] ? get_dirty_limits+0x22/0x256
Mar  5 09:03:21 aix-162 kernel: [64800.280648]  [<ffffffff810a2cc4>] shrink_list+0x90/0x96
Mar  5 09:03:21 aix-162 kernel: [64800.280657]  [<ffffffff810a2f32>] shrink_zone+0x268/0x32c
Mar  5 09:03:21 aix-162 kernel: [64800.280667]  [<ffffffff810a3731>] balance_pgdat+0x378/0x56b
Mar  5 09:03:21 aix-162 kernel: [64800.280677]  [<ffffffff810a10fe>] ? isolate_pages_global+0x0/0x210
Mar  5 09:03:21 aix-162 kernel: [64800.280687]  [<ffffffff810a3a3c>] kswapd+0x118/0x11a
Mar  5 09:03:21 aix-162 kernel: [64800.280696]  [<ffffffff8105940b>] ? autoremove_wake_function+0x0/0x34
Mar  5 09:03:21 aix-162 kernel: [64800.280706]  [<ffffffff810a3924>] ? kswapd+0x0/0x11a
Mar  5 09:03:21 aix-162 kernel: [64800.280715]  [<ffffffff8105912f>] kthread+0x7a/0x82
Mar  5 09:03:21 aix-162 kernel: [64800.280725]  [<ffffffff8100c9da>] child_rip+0xa/0x20

Mar  5 09:03:21 aix-162 kernel: [64800.280734]  [<ffffffff810590b5>] ? kthread+0x0/0x82
Mar  5 09:03:21 aix-162 kernel: [64800.280742]  [<ffffffff8100c9d0>] ? child_rip+0x0/0x20
Mar  5 09:03:21 aix-162 kernel: [64800.280797] INFO: task openbox:6005 blocked for more than 120 seconds.
Mar  5 09:03:21 aix-162 kernel: [64800.280803] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Mar  5 09:03:21 aix-162 kernel: [64800.280810] openbox       D ffff88002830dce8     0  6005   5943 0x00000000
Mar  5 09:03:21 aix-162 kernel: [64800.280822]  ffff8802374572c8 0000000000000086 0000000000000000 0000000000000246
Mar  5 09:03:21 aix-162 kernel: [64800.280833]  ffff880237457238 ffffffff8105fb6c ffff880237457fd8 ffff880237457fd8
Mar  5 09:03:21 aix-162 kernel: [64800.280844]  ffff88023b258388 000000000000dce8 0000000000013800 ffff88023b258388
Mar  5 09:03:21 aix-162 kernel: [64800.280855] Call Trace:
Mar  5 09:03:21 aix-162 kernel: [64800.280864]  [<ffffffff8105fb6c>] ? timekeeping_get_ns+0x16/0x38
Mar  5 09:03:21 aix-162 kernel: [64800.280895]  [<ffffffffa054ce53>] ? nfs_wait_bit_uninterruptible+0x0/0xd [nfs]
Mar  5 09:03:21 aix-162 kernel: [64800.280926]  [<ffffffffa054ce53>] ? nfs_wait_bit_uninterruptible+0x0/0xd [nfs]
Mar  5 09:03:21 aix-162 kernel: [64800.280937]  [<ffffffff81332d51>] io_schedule+0x3e/0x58
Mar  5 09:03:21 aix-162 kernel: [64800.280966]  [<ffffffffa054ce5c>] nfs_wait_bit_uninterruptible+0x9/0xd [nfs]
Mar  5 09:03:21 aix-162 kernel: [64800.280977]  [<ffffffff8133321b>] __wait_on_bit+0x43/0x76
Mar  5 09:03:21 aix-162 kernel: [64800.280986]  [<ffffffff811b27c3>] ? __lookup_tag+0xbd/0x12d
Mar  5 09:03:21 aix-162 kernel: [64800.280996]  [<ffffffff813332b7>] out_of_line_wait_on_bit+0x69/0x74
Mar  5 09:03:21 aix-162 kernel: [64800.281026]  [<ffffffffa054ce53>] ? nfs_wait_bit_uninterruptible+0x0/0xd [nfs]
Mar  5 09:03:21 aix-162 kernel: [64800.281037]  [<ffffffff8105943f>] ? wake_bit_function+0x0/0x2e
Mar  5 09:03:21 aix-162 kernel: [64800.281067]  [<ffffffffa054ce51>] nfs_wait_on_request+0x23/0x25 [nfs]
Mar  5 09:03:21 aix-162 kernel: [64800.281101]  [<ffffffffa0551037>] nfs_sync_mapping_wait+0xf0/0x211 [nfs]
Mar  5 09:03:21 aix-162 kernel: [64800.281136]  [<ffffffffa05511ea>] nfs_wb_page+0x92/0xc2 [nfs]
Mar  5 09:03:21 aix-162 kernel: [64800.281146]  [<ffffffff810aa905>] ? __dec_zone_page_state+0x29/0x2b
Mar  5 09:03:21 aix-162 kernel: [64800.281170]  [<ffffffffa0543ed2>] nfs_release_page+0x3c/0x4e [nfs]
...
[/FONT]

---

### Post by Pencioner on 2010-03-05
Hmmmm seems we got different problems, since on 2.6.32.9 all is working good for me...

---

### Post by nevbear666 on 2010-03-05
i switched back to the stable kernel for now...

still having the same errors in messages and syslog, but its no longer freezing the box...

the kernel bootparams:
noapic acpi=off nolapic_timer clocksource=pit divider=10

helped a bit, especially the nolapic option, but the error is still ocurring and making the cpu more busy than it should be...

---

