---
title: "Ndiswrapper and Belkin F6D4050"
date: 2009-08-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cellstije on 2009-08-15
hi there,

I posted this on another thread already, but since It relates to Karmic, I'll repost here as well.

I'm trying to get a belking wireless usb adapter to work, but no luck

It is a F6D4050 v1, the kernel driver rt2870sta does not recognize it.

Using ndiswrapper I got it recognized using the WinXp64 drivers (I installed the amd64 version of Karmic), while the WinXP32 does not work.

However, when I try to join a network, nothing happens and dmesg reports this:

[  812.816820] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)                                                                      
[  812.964061] usb 1-6: reset high speed USB device using ehci_hcd and address 4                                                          
[  813.110517] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver                                         
[  813.112930] ndiswrapper: driver rt2870 (Ralink Technology, Corp.,10/01/2008, 1.02.03.0000) loaded                                      
[  813.807137] wlan0: ethernet device 00:22:75:55:4c:da using NDIS driver: rt2870, version: 0x0, NDIS version: 0x501, vendor: 'IEEE 802.11 Wireless Card.', 050D:935A.F.conf                                                                                                        
[  813.807168] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  813.807246] usbcore: registered new interface driver ndiswrapper
[ 1018.128684] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1157.632630] BUG: unable to handle kernel NULL pointer dereference at 0000000000000010
[ 1157.632642] IP: [<ffffffffa03e7085>] IofCompleteRequest+0xc5/0x1c0 [ndiswrapper]
[ 1157.632683] PGD 3a801067 PUD 24d6a067 PMD 0
[ 1157.632693] Oops: 0002 [#1] SMP
[ 1157.632699] last sysfs file: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/net/wlan0/ifindex
[ 1157.632705] CPU 0
[ 1157.632710] Modules linked in: ndiswrapper nls_iso8859_1 vfat fat lp snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_emu10k1 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_util_mem snd_hwdep snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device ppdev snd parport_pc dell_wmi parport soundcore psmouse dcdbas serio_raw hid_apple squashfs aufs usbhid nls_cp437 isofs usb_storage ohci1394 floppy tg3 ieee1394 fbcon tileblit font bitblit softcursor i915 drm i2c_algo_bit video output intel_agp [last unloaded: ndiswrapper]
[ 1157.632813] Pid: 5266, comm: ntos_wq Tainted: P           2.6.31-5-generic #24-Ubuntu Precision WorkStation 380
[ 1157.632821] RIP: 0010:[<ffffffffa03e7085>]  [<ffffffffa03e7085>] IofCompleteRequest+0xc5/0x1c0 [ndiswrapper]
[ 1157.632857] RSP: 0018:ffff880022089dc0  EFLAGS: 00010202
[ 1157.632862] RAX: 0000000000000010 RBX: ffff880007d1e600 RCX: ffff880000f0d850
[ 1157.632868] RDX: 0000000000000000 RSI: 0000000000000002 RDI: 0000000000000002
[ 1157.632873] RBP: ffff880022089e00 R08: ffff880000f0d850 R09: 0000000000000000
[ 1157.632879] R10: 0000000000000000 R11: 00000000ffffffff R12: ffff880007d1e718
[ 1157.632885] R13: ffff880022089dcf R14: 0000000000000000 R15: ffffc9000450d688
[ 1157.632892] FS:  0000000000000000(0000) GS:ffff8800019c2000(0000) knlGS:0000000000000000
[ 1157.632899] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
[ 1157.632904] CR2: 0000000000000010 CR3: 000000000892f000 CR4: 00000000000006b0
[ 1157.632911] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 1157.632916] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 1157.632924] Process ntos_wq (pid: 5266, threadinfo ffff880022088000, task ffff880007c296b0)
[ 1157.632928] Stack:
[ 1157.632932]  ffff880007d856c0 00ff880007d1e600 ffff880022089e00 ffff880007d1e600
[ 1157.632942] <0> ffff880007d856c0 ffff880000f0d8d8 ffffc9000450d680 ffffc9000450d688
[ 1157.632951] <0> ffff880022089e30 ffffffffa03f1795 0000000000015580 ffffffffa0411cc0
[ 1157.632962] Call Trace:
[ 1157.633000]  [<ffffffffa03f1795>] wrap_urb_complete_worker+0xe5/0x1c0 [ndiswrapper]
[ 1157.633035]  [<ffffffffa03f16b0>] ? wrap_urb_complete_worker+0x0/0x1c0 [ndiswrapper]
[ 1157.633050]  [<ffffffff8106da65>] run_workqueue+0x95/0x170
[ 1157.633058]  [<ffffffff8106dbe4>] worker_thread+0xa4/0x120
[ 1157.633066]  [<ffffffff81072da0>] ? autoremove_wake_function+0x0/0x40
[ 1157.633074]  [<ffffffff8106db40>] ? worker_thread+0x0/0x120
[ 1157.633080]  [<ffffffff810729b6>] kthread+0x96/0xa0
[ 1157.633088]  [<ffffffff8101308a>] child_rip+0xa/0x20
[ 1157.633094]  [<ffffffff81072920>] ? kthread+0x0/0xa0
[ 1157.633100]  [<ffffffff81013080>] ? child_rip+0x0/0x20
[ 1157.633104] Code: 0a 01 00 00 80 7b 41 00 0f 84 b0 00 00 00 40 38 f7 0f 1f 44 00 00 0f 8c 8a 00 00 00 48 8b 43 48 48 85 c0 0f 1f 00 74 11 8b 53 30 <89> 10 48 8b 53 38 48 8b 43 48 48 89 50 08 48 8b 7b 50 48 85 ff
[ 1157.633184] RIP  [<ffffffffa03e7085>] IofCompleteRequest+0xc5/0x1c0 [ndiswrapper]
[ 1157.633219]  RSP <ffff880022089dc0>
[ 1157.633223] CR2: 0000000000000010
[ 1157.633228] ---[ end trace 506325aa9afa3c3d ]---


any clue?

c.

---

