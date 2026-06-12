---
title: "Latest kernal causing no display on 14.10"
date: 2014-11-27
forum: Installation &amp; Upgrades
---

### Post by solitaire on 2014-11-27
Hi

I've just upgraded to the latest kernel 3.16.0-26-generic #34
and I'm getting a kernel error which is causing my display to fail.
Processor AMD E-350 x2
Graphics Gallium 0.4 AMD Palm Radeon HD 6310 (running open source tested drivers.)

Error : 
```
Nov 27 14:17:45 zotac kernel: [   13.310565] BUG: unable to handle kernel paging request at ffffec2000000900
Nov 27 14:17:45 zotac kernel: [   13.311644] IP: [<ffffffff811c2046>] kfree+0x56/0x150
Nov 27 14:17:45 zotac kernel: [   13.312417] PGD 0 
Nov 27 14:17:45 zotac kernel: [   13.312725] Oops: 0000 [#1] SMP 
Nov 27 14:17:45 zotac kernel: [   13.313230] Modules linked in: snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep snd_pcm arc4 ath9k ath9k_common snd_seq_midi snd_seq_midi_event ath9k_hw snd_rawmidi ath kvm_amd kvm snd_seq mac80211 joydev radeon snd_seq_device rfcomm serio_raw bnep bluetooth 6lowpan_iphc cfg80211 k10temp snd_timer ttm drm_kms_helper sp5100_tco i2c_piix4 drm snd soundcore shpchp i2c_algo_bit parport_pc ppdev mac_hid lp parport hwmon_vid pata_acpi hid_generic usbhid hid psmouse r8169 mii ahci pata_atiixp libahci
Nov 27 14:17:45 zotac kernel: [   13.321495] CPU: 0 PID: 1416 Comm: Xorg Not tainted 3.16.0-26-generic #34-Ubuntu
Nov 27 14:17:45 zotac kernel: [   13.322582] Hardware name: MotherBoard By ZOTAC MotherBoard Fusion350-B-B/E/J/U/Fusion350-B-B/E/J/U, BIOS 4.6.4 11/14/2011
Nov 27 14:17:45 zotac kernel: [   13.324203] task: ffff88024138c750 ti: ffff880092d28000 task.ti: ffff880092d28000
Nov 27 14:17:45 zotac kernel: [   13.325299] RIP: 0010:[<ffffffff811c2046>]  [<ffffffff811c2046>] kfree+0x56/0x150
Nov 27 14:17:45 zotac kernel: [   13.326411] RSP: 0018:ffff880092d2b9b8  EFLAGS: 00010286
Nov 27 14:17:45 zotac kernel: [   13.327194] RAX: 0000022000000900 RBX: 0000100000024414 RCX: 0000000000000000
Nov 27 14:17:45 zotac kernel: [   13.328236] RDX: 000077ff80000000 RSI: 0000000000005f78 RDI: 0000100000024414
Nov 27 14:17:45 zotac kernel: [   13.329292] RBP: ffff880092d2b9d0 R08: 0000000000000003 R09: ffffec2000000900
Nov 27 14:17:45 zotac kernel: [   13.330345] R10: 0000000000000036 R11: 0000000000000000 R12: ffff880240d70000
Nov 27 14:17:45 zotac kernel: [   13.331400] R13: ffffffffc05614f7 R14: ffff88024328f200 R15: 0000000000000c00
Nov 27 14:17:45 zotac kernel: [   13.332448] FS:  00007f6ce2d3f9c0(0000) GS:ffff88024ec00000(0000) knlGS:0000000000000000
Nov 27 14:17:45 zotac kernel: [   13.333642] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Nov 27 14:17:45 zotac kernel: [   13.334490] CR2: ffffec2000000900 CR3: 0000000092520000 CR4: 00000000000007f0
Nov 27 14:17:45 zotac kernel: [   13.335550] Stack:
Nov 27 14:17:45 zotac kernel: [   13.335837]  ffff880240d70000 ffff880240d70000 0000000000000000 ffff880092d2ba98
Nov 27 14:17:45 zotac kernel: [   13.336975]  ffffffffc05614f7 000000024328f200 ffff880241fdd000 00007c4800007d2c
Nov 27 14:17:45 zotac kernel: [   13.338111]  ffff880200007c44 ffff88024328f000 ffff8800365e8100 0000100000024414
Nov 27 14:17:45 zotac kernel: [   13.339260] Call Trace:
Nov 27 14:17:45 zotac kernel: [   13.339676]  [<ffffffffc05614f7>] evergreen_hdmi_setmode+0x8d7/0xbd0 [radeon]
Nov 27 14:17:45 zotac kernel: [   13.340768]  [<ffffffffc0336cf4>] ? drm_detect_hdmi_monitor+0x74/0xc0 [drm]
Nov 27 14:17:45 zotac kernel: [   13.341841]  [<ffffffffc0568b58>] radeon_atom_encoder_mode_set+0x158/0x2d0 [radeon]
Nov 27 14:17:45 zotac kernel: [   13.342995]  [<ffffffffc0395966>] drm_crtc_helper_set_mode+0x356/0x530 [drm_kms_helper]
Nov 27 14:17:45 zotac kernel: [   13.344197]  [<ffffffffc03966db>] drm_crtc_helper_set_config+0x98b/0xb10 [drm_kms_helper]
Nov 27 14:17:45 zotac kernel: [   13.345426]  [<ffffffff8139c971>] ? idr_mark_full+0x61/0x70
Nov 27 14:17:45 zotac kernel: [   13.346279]  [<ffffffffc0513d64>] radeon_crtc_set_config+0x44/0x120 [radeon]
Nov 27 14:17:45 zotac kernel: [   13.347348]  [<ffffffffc032e6d1>] drm_mode_set_config_internal+0x61/0xe0 [drm]
Nov 27 14:17:45 zotac kernel: [   13.348446]  [<ffffffffc0332413>] drm_mode_setcrtc+0x283/0x580 [drm]
Nov 27 14:17:45 zotac kernel: [   13.349407]  [<ffffffffc0322a4f>] drm_ioctl+0x1df/0x680 [drm]
Nov 27 14:17:45 zotac kernel: [   13.350284]  [<ffffffffc04eb04c>] radeon_drm_ioctl+0x4c/0x80 [radeon]
Nov 27 14:17:45 zotac kernel: [   13.351256]  [<ffffffff811f5138>] do_vfs_ioctl+0x2c8/0x4a0
Nov 27 14:17:45 zotac kernel: [   13.352079]  [<ffffffff811f5391>] SyS_ioctl+0x81/0xa0
Nov 27 14:17:45 zotac kernel: [   13.352837]  [<ffffffff81789ead>] system_call_fastpath+0x1a/0x1f
Nov 27 14:17:45 zotac kernel: [   13.353738] Code: 00 00 00 80 ff 77 00 00 49 b9 00 00 00 00 00 ea ff ff 48 01 d8 48 0f 42 15 d8 7f a5 00 48 01 d0 48 c1 e8 0c 48 c1 e0 06 49 01 c1 <49> 8b 01 f6 c4 80 0f 85 b6 00 00 00 49 8b 01 a8 80 0f 84 83 00 
Nov 27 14:17:45 zotac kernel: [   13.357539] RIP  [<ffffffff811c2046>] kfree+0x56/0x150
Nov 27 14:17:45 zotac kernel: [   13.358322]  RSP <ffff880092d2b9b8>
Nov 27 14:17:45 zotac kernel: [   13.358837] CR2: ffffec2000000900
Nov 27 14:17:47 zotac kernel: [   15.930758] ip_tables: (C) 2000-2006 Netfilter Core Team

```

Only error like this i can find is from last year

[https://bugzilla.kernel.org/show_bug.cgi?id=67571](https://bugzilla.kernel.org/show_bug.cgi?id=67571)

I can boot and log-in fine with the previous kernel.

Any Ideas? or am i stuck till a new kernel update is released?

---

### Post by solitaire on 2014-11-29
*BUMP*

Tried a reboot in to latest kernel, Still getting same "no output". 
All software upto date.
Probably going to have to remove this kernel!

ANYONE got any other ideas?

---

### Post by casey12 on 2014-12-18
Hi Solitaire! Bumping this thread again to see if solitaire (or anyone) has found a solution or even cause of this mess. 

I'm running this on my home machine, with a **ASRock E35LM1 AMD E-240 APU AMD A50M Mini ITX** motherboard. This has AMD [COLOR=#0000ff]**Radeon 6310**[/COLOR] onboard graphics. I use this machine primarily as a Samba server for my home network, but also for experimenting with linux server components when I feel things are going well.

I was running 14.04 server for several months, and everything (including the graphics) worked perfectly and without any undue input on my part. In the normal course of events, I downloaded the 14.10 server image and did a fresh install. Sadly, in hindsight, HUGE MISTAKE. *After a very basic install* (no optional components but OpenSSH),* I was presented with a black screen. *

I discovered that the last Ubuntu recovery mode (3.16.0-25-generic) worked fine. Spent all morning with the aticonfig program, and it's 20 pages of --help, to no avail. Tried several other things from the [11.10 E-450 ATI 6320]("http://ubuntuforums.org/showthread.php?t=1857911") thread, also to no avail. I guess I'll just be reverting to 14.04 until some kind of solution is discovered...

---

### Post by solitaire on 2014-12-18
Forgot to add in the launchpad page for this bug.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1397553](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1397553)

They think they have found the problem. You might have to drop the proposed kernel back to a stable one for now and wait for Ubuntu to get the patch from upstream.

Or install one of the mainline kernels they seem to be OK.

---

