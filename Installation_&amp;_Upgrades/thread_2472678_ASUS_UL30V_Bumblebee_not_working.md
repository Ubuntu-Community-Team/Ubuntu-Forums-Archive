---
title: "ASUS UL30V Bumblebee not working"
date: 2022-03-08
forum: Installation &amp; Upgrades
---

### Post by randomas on 2022-03-08
Hallo there, I'm having issues configuring my ancient lapotop with 20.04. It's an ASUS ul30v with hybrid graphics. I had everything working on 14.04 but it was a wee bit out of date so I upgraded, that didn't go well, so I reinstalled the system. 
To disable the intel graphics you can set the sata mode to compatible in the BIOS (don't ask!). However I had it working with bumblebee and now I just can't get bumblebee to start up. 
First up the drivers for this nvidia card are not compatible with new kernels I had to download a modified 340 driver from ppa, but that is working now. 
If I start the PC up with sata in enhanced mode the system reaches the login screen but when I login the system just blinks me back into the gdm. 

I found an error about GLX not being found on device :0 


Any help, please.

 
TIA

---

### Post by #&amp;thj^% on 2022-03-08
Can we see this:
```
inxi -Gx

```
You'll see this "Message: Unable to show GL data. Required tool glxinfo missing."

---

### Post by randomas on 2022-03-09
Yes thank you, this is what I get with the sata mode set as compatible with the desktop working and the intel card forced off in the BIOS:
```
Graphics:
  Device-1: NVIDIA GT218M [GeForce G210M] vendor: ASUSTeK driver: nvidia 
  v: 340.108 bus ID: 01:00.0 
  Display: x11 server: X.Org 1.20.13 driver: nvidia 
  resolution: 1366x768~60Hz 
  OpenGL: renderer: GeForce G210M/PCIe/SSE2 v: 3.3.0 NVIDIA 340.108 
  direct render: Yes 
  
```

And this is what I get from terminal (can't access desktop) with the sata mode set to enhanced:

```

Graphics:  Device-1: Intel Mobile 4 Series Integrated Graphics vendor: ASUSTeK driver: i915 v: kernel bus ID: 00:02.0 
           Display: server: X.org 1.20.13 driver: modesetting FAILED: nvidia unloaded: fbdev,vesa tty: 170x48 
           Message: Advanced graphics data unavailable in console. Try -G --display 
```

I can get the intel card to work but I have to purge the nvidia drivers from the system, I would like to get the system working with bumblebee and only use the nvida drivers when needed. 

this is the error I find in syslog for bumblebee rightly complaining that it cannot find the intel card (sata compatible).
```

Mar 10 00:01:16 Sabertooth systemd[1]: bumblebeed.service: Scheduled restart job, restart counter is at 6.
Mar 10 00:01:16 Sabertooth systemd[1]: Stopped Bumblebee C Daemon.
Mar 10 00:01:16 Sabertooth systemd[1]: Started Bumblebee C Daemon.
Mar 10 00:01:16 Sabertooth bumblebeed[3159]: [  391.869510] [ERROR]No integrated video card found, quitting.
Mar 10 00:01:16 Sabertooth systemd[1]: bumblebeed.service: Main process exited, code=exited, status=1/FAILURE
Mar 10 00:01:16 Sabertooth systemd[1]: bumblebeed.service: Failed with result 'exit-code'.

```

while this is what I'm seing with sata enhanced 

```

Mar 10 00:14:48 Sabertooth kernel: [   22.429610] bbswitch: loading out-of-tree module taints kernel.
Mar 10 00:14:48 Sabertooth kernel: [   22.429680] bbswitch: module verification failed: signature and/or required key missing - tainting kernel
Mar 10 00:14:48 Sabertooth kernel: [   22.429974] bbswitch: version 0.8
Mar 10 00:14:48 Sabertooth kernel: [   22.429986] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.VGA_
Mar 10 00:14:48 Sabertooth kernel: [   22.430001] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.P0P1.VGA_
Mar 10 00:14:48 Sabertooth kernel: [   22.430024] ACPI Warning: \_SB.PCI0.P0P1.VGA._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20210331/nsarguments-61)
Mar 10 00:14:48 Sabertooth kernel: [   22.430312] bbswitch: detected a nVidia _DSM function
Mar 10 00:14:48 Sabertooth kernel: [   22.430355] pci 0000:01:00.0: enabling device (0000 -> 0003)
Mar 10 00:14:48 Sabertooth kernel: [   22.430457] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on
Mar 10 00:14:48 Sabertooth kernel: [   22.434848] bbswitch: disabling discrete graphics
Mar 10 00:14:48 Sabertooth kernel: [   22.453029] pcieport 0000:00:01.0: pciehp: Slot(16): Card not present
Mar 10 00:14:48 Sabertooth kernel: [   22.808149] snd_hda_codec_hdmi hdaudioC1D3: Unable to sync register 0x4f0d00. -5
Mar 10 00:14:48 Sabertooth kernel: [   22.808189] snd_hda_codec_hdmi hdaudioC1D3: HDMI: invalid ELD buf size -1
Mar 10 00:14:48 Sabertooth kernel: [   23.092131] snd_hda_codec_hdmi hdaudioC1D2: Unable to sync register 0x4f0d00. -5
Mar 10 00:14:48 Sabertooth kernel: [   23.092158] snd_hda_codec_hdmi hdaudioC1D2: HDMI: invalid ELD buf size -1
Mar 10 00:14:48 Sabertooth kernel: [   23.380063] snd_hda_codec_hdmi hdaudioC1D1: Unable to sync register 0x4f0d00. -5
Mar 10 00:14:48 Sabertooth kernel: [   23.380082] snd_hda_codec_hdmi hdaudioC1D1: HDMI: invalid ELD buf size -1
Mar 10 00:14:48 Sabertooth kernel: [   23.668128] snd_hda_codec_hdmi hdaudioC1D0: Unable to sync register 0x4f0d00. -5
Mar 10 00:14:48 Sabertooth kernel: [   23.668156] snd_hda_codec_hdmi hdaudioC1D0: HDMI: invalid ELD buf size -1
Mar 10 00:14:48 Sabertooth kernel: [   23.868363] i915 0000:00:02.0: vgaarb: changed VGA decodes: olddecodes=none,decodes=io+mem:owns=io+mem

```

and this:

```

Mar 10 00:19:01 Sabertooth kernel: [  274.774061] BUG: kernel NULL pointer dereference, address: 0000000000000058
Mar 10 00:19:01 Sabertooth kernel: [  274.774122] #PF: supervisor read access in kernel mode
Mar 10 00:19:01 Sabertooth kernel: [  274.774158] #PF: error_code(0x0000) - not-present page
Mar 10 00:19:01 Sabertooth kernel: [  274.774194] PGD 0 P4D 0 
Mar 10 00:19:01 Sabertooth kernel: [  274.774219] Oops: 0000 [#1] SMP PTI
Mar 10 00:19:01 Sabertooth kernel: [  274.774246] CPU: 0 PID: 634 Comm: bumblebeed Tainted: G          IOE     5.13.0-30-generic #33~20.04.1-Ubuntu
Mar 10 00:19:01 Sabertooth kernel: [  274.774306] Hardware name: ASUSTeK Computer Inc.         UL30VT              /UL30VT    , BIOS 211     07/14/2010
Mar 10 00:19:01 Sabertooth kernel: [  274.774367] RIP: 0010:dis_dev_get+0x15/0x40 [bbswitch]
Mar 10 00:19:01 Sabertooth kernel: [  274.774410] Code: 48 c7 c6 a0 10 09 c1 48 89 e5 e8 76 ac ab c9 5d c3 0f 1f 40 00 0f 1f 44 00 00 48 8b 05 e4 34 00 00 48 8b 40 10 48 85 c0 74 20 <48> 8b 78 38 48 85 ff 74 17 55
 48 81 c7 c8 00 00 00 be 04 00 00 00
Mar 10 00:19:01 Sabertooth kernel: [  274.774516] RSP: 0018:ffffb76a409efce8 EFLAGS: 00010202
Mar 10 00:19:01 Sabertooth kernel: [  274.774551] RAX: 0000000000000020 RBX: ffffb76a409efdb0 RCX: 0000000000000006
Mar 10 00:19:01 Sabertooth kernel: [  274.776192] RDX: 0000000000002500 RSI: 0000000000000001 RDI: ffff9fbf02397f00
Mar 10 00:19:01 Sabertooth kernel: [  274.776192] RBP: ffffb76a409efd08 R08: 0000000000001000 R09: 0000000000000001
Mar 10 00:19:01 Sabertooth kernel: [  274.776192] R10: ffffb76a409efde8 R11: 0000000000000000 R12: ffff9fbf02397f00
Mar 10 00:19:01 Sabertooth kernel: [  274.781483] R13: 0000000000000001 R14: ffff9fbf02397f28 R15: ffff9fbf02397f00
Mar 10 00:19:01 Sabertooth kernel: [  274.781483] FS:  00007faa0a2dbb80(0000) GS:ffff9fbf3bc00000(0000) knlGS:0000000000000000
Mar 10 00:19:01 Sabertooth kernel: [  274.781483] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Mar 10 00:19:01 Sabertooth kernel: [  274.781483] CR2: 0000000000000058 CR3: 0000000106eac000 CR4: 00000000000406f0
Mar 10 00:19:01 Sabertooth kernel: [  274.781483] Call Trace:
Mar 10 00:19:01 Sabertooth kernel: [  274.781483]  <TASK>
Mar 10 00:19:01 Sabertooth kernel: [  274.781483]  ? bbswitch_proc_show+0x26/0xa0 [bbswitch]
Mar 10 00:19:01 Sabertooth kernel: [  274.781483]  seq_read_iter+0x120/0x450
Mar 10 00:19:01 Sabertooth kernel: [  274.781483]  seq_read+0xfd/0x150
Mar 10 00:19:01 Sabertooth kernel: [  274.781483]  proc_reg_read+0x66/0x90
Mar 10 00:19:01 Sabertooth kernel: [  274.781483]  vfs_read+0xa0/0x190
Mar 10 00:19:01 Sabertooth kernel: [  274.781483]  ksys_read+0x67/0xe0
Mar 10 00:19:01 Sabertooth kernel: [  274.781483]  __x64_sys_read+0x1a/0x20
Mar 10 00:19:01 Sabertooth kernel: [  274.781483]  do_syscall_64+0x61/0xb0
Mar 10 00:19:01 Sabertooth kernel: [  274.781483]  ? exit_to_user_mode_prepare+0x3d/0x1c0
Mar 10 00:19:01 Sabertooth kernel: [  274.781483]  ? syscall_exit_to_user_mode+0x27/0x50
Mar 10 00:19:01 Sabertooth kernel: [  274.781483]  ? __x64_sys_newfstat+0x16/0x20
Mar 10 00:19:01 Sabertooth kernel: [  274.781483]  ? do_syscall_64+0x6e/0xb0
Mar 10 00:19:01 Sabertooth kernel: [  274.781483]  ? exc_page_fault+0x8f/0x170
Mar 10 00:19:01 Sabertooth kernel: [  274.781483]  ? asm_exc_page_fault+0x8/0x30
Mar 10 00:19:01 Sabertooth kernel: [  274.781483]  entry_SYSCALL_64_after_hwframe+0x44/0xae
Mar 10 00:19:01 Sabertooth kernel: [  274.781483] RIP: 0033:0x7faa0a7c2002
Mar 10 00:19:01 Sabertooth kernel: [  274.781483] Code: c0 e9 c2 fe ff ff 50 48 8d 3d 7a cb 0a 00 e8 d5 1a 02 00 0f 1f 44 00 00 f3 0f 1e fa 64 8b 04 25 18 00 00 00 85 c0 75 10 0f 05 <48> 3d 00 f0 ff ff 77 56 c3 0f 1f 44 00 00 48 83 ec 28 48 89 54 24
Mar 10 00:19:01 Sabertooth kernel: [  274.781483] RSP: 002b:00007ffde02028c8 EFLAGS: 00000246 ORIG_RAX: 0000000000000000
Mar 10 00:19:01 Sabertooth kernel: [  274.781483] RAX: ffffffffffffffda RBX: 0000000000000d68 RCX: 00007faa0a7c2002
Mar 10 00:19:01 Sabertooth kernel: [  274.781483] RDX: 000000000000000e RSI: 0000559c7df728a0 RDI: 0000000000000004
Mar 10 00:19:01 Sabertooth kernel: [  274.781483] RBP: 0000559c7df63eb0 R08: 0000000000000004 R09: 0000000000000001
Mar 10 00:19:01 Sabertooth kernel: [  274.781483] R10: 0000000000000000 R11: 0000000000000246 R12: 000000000000000e
Mar 10 00:19:01 Sabertooth kernel: [  274.781483] R13: 000000000000000e R14: 00007faa0a89c8a0 R15: 0000000000000001
Mar 10 00:19:01 Sabertooth kernel: [  274.781483]  </TASK>
Mar 10 00:19:01 Sabertooth kernel: [  274.781483] Modules linked in: rfcomm ccm bnep bbswitch(OE) iwldvm coretemp mac80211 uvcvideo libarc4 videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_common snd_hda_codec_realtek btusb btrtl btbcm snd_hda_codec_generic btintel kvm_intel ledtrig_audio snd_hda_codec_hdmi videodev i915 bluetooth kvm iwlwifi snd_hda_intel mc snd_intel_dspcfg ecdh_generic snd_intel_sdw_acpi ecc snd_hda_codec wmi_bmof snd_seq_midi mxm_wmi snd_seq_midi_event joydev cfg80211 input_leds snd_rawmidi snd_hda_core serio_raw snd_hwdep drm_kms_helper snd_pcm snd_seq asus_laptop snd_seq_device cec snd_timer rc_core i2c_algo_bit snd sparse_keymap fb_sys_fops soundcore syscopyarea sysfillrect mac_hid sysimgblt sch_fq_codel msr parport_pc ppdev lp parport drm ip_tables x_tables autofs4 btrfs blake2b_generic xor zstd_compress raid6_pq libcrc32c hid_logitech_hidpp hid_logitech_dj hid_generic usbhid hid ahci psmouse lpc_ich libahci atl1c video wmi
Mar 10 00:19:01 Sabertooth kernel: [  274.781483] CR2: 0000000000000058
Mar 10 00:19:01 Sabertooth kernel: [  274.782761] ---[ end trace 2ec659c747dde9ba ]---
Mar 10 00:19:01 Sabertooth kernel: [  274.782764] RIP: 0010:dis_dev_get+0x15/0x40 [bbswitch]
Mar 10 00:19:01 Sabertooth kernel: [  274.782771] Code: 48 c7 c6 a0 10 09 c1 48 89 e5 e8 76 ac ab c9 5d c3 0f 1f 40 00 0f 1f 44 00 00 48 8b 05 e4 34 00 00 48 8b 40 10 48 85 c0 74 20 <48> 8b 78 38 48 85 ff 74 17 55 48 81 c7 c8 00 00 00 be 04 00 00 00
Mar 10 00:19:01 Sabertooth kernel: [  274.782775] RSP: 0018:ffffb76a409efce8 EFLAGS: 00010202
Mar 10 00:19:01 Sabertooth kernel: [  274.782778] RAX: 0000000000000020 RBX: ffffb76a409efdb0 RCX: 0000000000000006
Mar 10 00:19:01 Sabertooth kernel: [  274.782781] RDX: 0000000000002500 RSI: 0000000000000001 RDI: ffff9fbf02397f00
Mar 10 00:19:01 Sabertooth kernel: [  274.782783] RBP: ffffb76a409efd08 R08: 0000000000001000 R09: 0000000000000001
Mar 10 00:19:01 Sabertooth kernel: [  274.782786] R10: ffffb76a409efde8 R11: 0000000000000000 R12: ffff9fbf02397f00
Mar 10 00:19:01 Sabertooth kernel: [  274.782788] R13: 0000000000000001 R14: ffff9fbf02397f28 R15: ffff9fbf02397f00
Mar 10 00:19:01 Sabertooth kernel: [  274.782791] FS:  00007faa0a2dbb80(0000) GS:ffff9fbf3bc00000(0000) knlGS:0000000000000000
Mar 10 00:19:01 Sabertooth kernel: [  274.782794] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Mar 10 00:19:01 Sabertooth kernel: [  274.782797] CR2: 0000000000000058 CR3: 0000000106eac000 CR4: 00000000000406f0


```


Hope this helps.

TIA

---

