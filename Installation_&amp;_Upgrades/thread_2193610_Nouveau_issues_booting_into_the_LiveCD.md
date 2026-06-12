---
title: "Nouveau issues booting into the LiveCD"
date: 2013-12-13
forum: Installation &amp; Upgrades
---

### Post by Tiny Grasshopper on 2013-12-13
Split off from [http://ubuntuforums.org/showthread.php?t=2193474](http://ubuntuforums.org/showthread.php?t=2193474)

I have a GE40 2OC-218USK laptop. I am trying to repartition the hard drive to have it dual boot Ubuntu and Windows 8.

So I hit escape on the loading screen when booting the Ubuntu LiveCD in Legacy mode and it showed the stack trace off the kernel panic during boot it is the following below. It seems to indicate a problem with the nouveau kernel module during LiveCD boot. Anyone know what the right kernel parameters that I should with this are?

This person is literally getting the exact same behavior as me, in relation to the Nouveau behavior:
[http://ubuntuforums.org/showthread.php?t=2183578](http://ubuntuforums.org/showthread.php?t=2183578)

```
[   26.154100] divide error: 000 [#1] SMP
[   26.154179] nouveau E[    PBUS][000:01:00.0] MMIO write of 0x00000000 FAULT at 0x418880 [ IBUS ]
[   26.155172] Modules linked in: btrfs(F) raid6_pq(F) libcrc32c(F) zlib_deflate(F) xor(F) x86_pkg_temp_thermal coretemp kvm_intel(F) kvm(F) crct10dif_pclmul(F) crc32_pclmul(F) ghash_clmulni_intel(F) joydev(F) snd_hda_codec_hdmi aesni_intel(F) snd_hda_codec_realtek aes_x86_64(F) lrw(F) gf128mul(F) glue_helper(F) msi_wmi snd_hda_intel ablk_helper(F) cryptd(F) snd_hda_codec sparse_keymap snd_hwdep(F) snd_pcm(F) snd_page_alloc(F) snd_seq_midi(F) snd_seq_midi_event(F) arc4(F) dm_multipath(F) rts5139(C) snd_rawmidi(F) rt18723ae rtl_pci rtlwifi scsi_dh(F) mac80211 snd_seq(F) snd_seq_device(F) snd_timer(F) cfg80211 snd(F) soundcore(F) btusb mei_me lpc_ich mei psmouse(F) serio_raw(F) mac_hid intel_rst microcode(F) parport_pc(F) ppdev(F) lp(F) parport(F) bnep rfcomm bluetooth squashfs(F) overlayfs(F) nls_iso8859_1(F) dm_mirror(F) dm_region_hash(F) dm_log(F) usb_storage(F) nouveau i915 ttm i2c_algo_bit ahci(F) drm_kms_helper libahci(F) drm alx mdio mxm_wmi wmi video(F)
[   26.158381] CPU: 5 PID: 2346 Comm: Xorg Tainted: GF        C   3.11.0-12-generic #19-Ubuntu
[   26.159108] Hardware name: Micro-Star International Co., Ltd. CR42 2M/GE40 2OC/MS-1492, BIOS E1492IMS.10N 11/14/2013
[   26.159840] task: ffff880221358000 ti: ffff880222810000 task.ti: ffff880222810000
[   26.160556] RIP: 0010:[<ffffffffa0206cb0>]  [<ffffffffa0206cb0>] nve4_graph_init+0x250/0x7e0 [nouveau]
[   26.161322] RSP: 0018:ffff880222811c10  EFLAGS: 00010246
[   26.162069] RAX: 00000000007fffff RBX: 0000000000000000 RCX: 0000000000000000
[   26.162808] RDX: 0000000000000000 RSI: ffffc90016303018 RDI: 0000000000000000
[   26.163563] RBP: ffff880222811ce8 R08: 0000000000000007 R09: 0000000000000000
[   26.164314] R10: 000000000000902d R11: ffff88021e234000 R12: ffff88021e234000
[   26.165055] R13: ffffffffa0270080 R14: 0000000000000000 R15: ffff88021e2340eb
[   26.165794] FS:  00007f277c762980(0000) GS:ffff88022fb40000(0000) knlGS:0000000000000000
[   26.166549] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[   26.167300] CR2: 00007f27760d2f50 CR3: 0000000222fa9000 CR4: 00000000001407e0
[   26.168013] Stack:
[   26.168756]  ffff880222811c20 0000000000000000 0000000000000000 0000000000000000
[   26.169521]  0000000000000000 0000000000000000 0000000000000000 0000000000000000
[   26.170280]  0000000000000000 0000000000000000 0000000000000000 0000000000000000
[   26.171032] Call Trace:
[   26.171805]  [<ffffffffa01b1fad>] nouveau_object_inc+0xbd/0x1b0 [nouveau]
[   26.172574]  [<ffffffffa01b2170>] nouveau_object_new+0xbd/0x230 [nouveau]
[   26.173353]  [<ffffffffa0213730>] nouveau_abi16_ioctl_grobj_alloc+0x70/0xe0 [nouveau]
[   26.174136]  [<ffffffffa0030212>] drm_ioctl+0x532/0x660 [drm]
[   26.174920]  [<ffffffff816f06a4>] ? __do_page_fault+0x204/0x540
[   26.175727]  [<ffffffff8116e9d5>] ? do_mmap_pgoff+0x305/0x3c0
[   26.176522]  [<ffffffff811b8ba5>] do_vfs_ioctl+0x2e5/0x4d0
[   26.177317]  [<ffffffff811b8e11>] SyS_ioctl+0x81/0xa0
[   26.178116]  [<ffffffff816f521d>] system_call_fastpath+0x1a/0x1f
[   26.178923] Code: 7d 11 89 f8 c1 f8 03 48 98 44 8b 84 85 30 ff ff ff eb a0 8b bd 30 ff ff ff 8d 83 ff ff 7f 00 45 31 f6 4d 8d bc 24 eb 00 00 00 99 <f7> fb bb 14 09 50 00 8d b0 80 89 41
[   26.180694] RIP  [<ffffffffa0206cb0>] nve4_graph_init+0x250/0x7e0 [nouveau]
[   26.181584]  RSP <ffff880222811c10>
```

[IMG]http://i.stack.imgur.com/wLRvq.jpg[/IMG]

---

### Post by efflandt on 2013-12-14
I have a GE60 20E-073US (slightly larger w/1080p 15.6" screen, i7-4700MQ and combo Intel/GTX 765M graphics). Fortunately it came with Win7, so I did not have to deal with UEFI yet (it uses Legacy mode with msdos partitions).

Have you tried **nomodeset** boot parameter for the live/install iso? Not sure if I did not wait long enough in a black screen the first time I booted 64-bit 13.10 from USB stick for it to go through its hardware detection. But I know that nomodeset is sometimes needed for nvidia (and sometimes not) and with the dual Intel/Nvidia graphics I figured it might be needed (doesn't hurt to try it) and it did work. I still get 2 or 3 lines of some error on the screen related to drm after install and installing nvidia drivers, but it does not seem to really be an issue.

---

