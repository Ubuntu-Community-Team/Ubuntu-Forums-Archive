---
title: "Problems with encrypted home directory"
date: 2009-03-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Technoviking on 2009-03-12
In Jaunty Alpha 6 getting these error sometimes when I try to mount my encrypted home directory. Anyone else seeing this?
```

Mar 12 19:49:56 mikebuntu kernel: [ 86.586999] ecryptfs_init_crypt_ctx: cryptfs: init_crypt_ctx(): Error initializing cipher [aes]
Mar 12 19:49:56 mikebuntu kernel: [ 86.587054] BUG: unable to handle kernel paging request at 00200200
Mar 12 19:49:56 mikebuntu kernel: [ 86.587056] IP: [<c02ab508>] crypto_larval_kill+0x18/0x60
Mar 12 19:49:56 mikebuntu kernel: [ 86.587063] *pde = 00000000
Mar 12 19:49:56 mikebuntu kernel: [ 86.587065] Oops: 0002 [#1] SMP
Mar 12 19:49:56 mikebuntu kernel: [ 86.587066] last sysfs file: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/rfkill/rfkill0/state
Mar 12 19:49:56 mikebuntu kernel: [ 86.587069] Dumping ftrace buffer:
Mar 12 19:49:56 mikebuntu kernel: [ 86.587071] (ftrace buffer empty)
Mar 12 19:49:56 mikebuntu kernel: [ 86.587073] Modules linked in: cbc aes_i586 aes_generic binfmt_misc ppdev bridge stp bnep input_polldev lp parport joydev arc4 snd_hda_intel ecb snd_pcm_oss snd_mixer_oss snd_pcm iwl3945 snd_timer uvcvideo mac80211 snd compat_ioctl32 videodev nvidia(P) intel_agp led_class video ricoh_mmc sdhci_pci sdhci soundcore v4l1_compat iTCO_wdt iTCO_vendor_support pcspkr psmouse dcdbas agpgart snd_page_alloc serio_raw cfg80211 output ohci1394 ieee1394 tg3 ehci_hcd uhci_hcd fbcon tileblit font bitblit softcursor
Mar 12 19:49:56 mikebuntu kernel: [ 86.587093]
Mar 12 19:49:56 mikebuntu kernel: [ 86.587096] Pid: 3642, comm: gnome-keyring-d Tainted: P (2.6.28-9-generic #31-Ubuntu) XPS M1330
Mar 12 19:49:56 mikebuntu kernel: [ 86.587098] EIP: 0060:[<c02ab508>] EFLAGS: 00010246 CPU: 1
Mar 12 19:49:56 mikebuntu kernel: [ 86.587100] EIP is at crypto_larval_kill+0x18/0x60
Mar 12 19:49:56 mikebuntu kernel: [ 86.587101] EAX: 00200200 EBX: f5d0e800 ECX: f5d0e800 EDX: f5d0eb00
Mar 12 19:49:56 mikebuntu kernel: [ 86.587103] ESI: fffffffe EDI: 0000008f EBP: f5835d1c ESP: f5835d18
Mar 12 19:49:56 mikebuntu kernel: [ 86.587104] DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Mar 12 19:49:56 mikebuntu kernel: [ 86.587106] Process gnome-keyring-d (pid: 3642, ti=f5834000 task=f5ed9920 task.ti=f5834000)
Mar 12 19:49:56 mikebuntu kernel: [ 86.587107] Stack:
Mar 12 19:49:56 mikebuntu kernel: [ 86.587108] fffffffe f5835d2c c02aba35 00000000 f583666c f5835d48 c02abaa9 00000004
Mar 12 19:49:56 mikebuntu kernel: [ 86.587112] f629c3a0 00000000 f583666c f5836698 f5835d78 c0268f5a c0601cb4 c050e32f
Mar 12 19:49:56 mikebuntu kernel: [ 86.587115] f5836698 00000003 00000080 f5836720 f629c3a0 f582401a f583666c f5835df4
Mar 12 19:49:56 mikebuntu kernel: [ 86.587118] Call Trace:
Mar 12 19:49:56 mikebuntu kernel: [ 86.587120] [<c02aba35>] ? crypto_alg_mod_lookup+0x65/0x80
Mar 12 19:49:56 mikebuntu kernel: [ 86.587122] [<c02abaa9>] ? crypto_alloc_base+0x39/0x90
Mar 12 19:49:56 mikebuntu kernel: [ 86.587125] [<c0268f5a>] ? ecryptfs_init_crypt_ctx+0xaa/0xf0
Mar 12 19:49:56 mikebuntu kernel: [ 86.587129] [<c026c2aa>] ? parse_tag_3_packet+0x10a/0x340
Mar 12 19:49:56 mikebuntu kernel: [ 86.587131] [<c012738b>] ? kunmap_atomic+0x3b/0xb0
Mar 12 19:49:56 mikebuntu kernel: [ 86.587134] [<c026ca54>] ? ecryptfs_parse_packet_set+0x194/0x480
Mar 12 19:49:56 mikebuntu kernel: [ 86.587137] [<c01bdb03>] ? vfs_read+0xa3/0x100
Mar 12 19:49:56 mikebuntu kernel: [ 86.587140] [<c0269104>] ? ecryptfs_read_headers_virt+0x84/0x140
Mar 12 19:49:56 mikebuntu kernel: [ 86.587143] [<c026930c>] ? ecryptfs_read_metadata+0xec/0x160
Mar 12 19:49:56 mikebuntu kernel: [ 86.587145] [<c0264225>] ? ecryptfs_open+0xc5/0x270
Mar 12 19:49:56 mikebuntu kernel: [ 86.587147] [<c01bb706>] ? __dentry_open+0xb6/0x260
Mar 12 19:49:56 mikebuntu kernel: [ 86.587150] [<c01bb987>] ? nameidata_to_filp+0x47/0x60
Mar 12 19:49:56 mikebuntu kernel: [ 86.587152] [<c0264160>] ? ecryptfs_open+0x0/0x270
Mar 12 19:49:56 mikebuntu kernel: [ 86.587154] [<c01c8bd9>] ? do_filp_open+0x1c9/0x7b0
Mar 12 19:49:56 mikebuntu kernel: [ 86.587157] [<c01d1bb0>] ? alloc_fd+0xe0/0x100
Mar 12 19:49:56 mikebuntu kernel: [ 86.587159] [<c01bb4cf>] ? do_sys_open+0x5f/0x130
Mar 12 19:49:56 mikebuntu kernel: [ 86.587162] [<c01bb609>] ? sys_open+0x29/0x40
Mar 12 19:49:56 mikebuntu kernel: [ 86.587164] [<c0103f6b>] ? sysenter_do_call+0x12/0x2f
Mar 12 19:49:56 mikebuntu kernel: [ 86.587166] [<c04f0000>] ? check_tsc_sync_source+0x113/0x122
Mar 12 19:49:56 mikebuntu kernel: [ 86.587170] Code: 5d f8 8b 75 fc 89 ec 5d c3 8d 76 00 8d bc 27 00 00 00 00 55 89 e5 53 89 c3 b8 68 63 69 c0 e8 e0 80 24 00 8b 13 8b 43 04 89 42 04 <89> 10 b8 68 63 69 c0 c7 03 00 01 10 00 c7 43 04 00 02 20 00 e8
Mar 12 19:49:56 mikebuntu kernel: [ 86.587185] EIP: [<c02ab508>] crypto_larval_kill+0x18/0x60 SS:ESP 0068:f5835d18
Mar 12 19:49:56 mikebuntu kernel: [ 86.587190] ---[ end trace 1ad3356402d120f1 ]---
```

---

### Post by Yashiro on 2009-03-15
Encrypted home directory has been dropped from Jaunty and won't make the final release.

---

### Post by Technoviking on 2009-03-15
Thought it was going to be an option for the alt CD installer.

---

### Post by Yashiro on 2009-03-15
> The "encrypted home directory" option that was available in the desktop installer in previous alpha milestones has been disabled due to outstanding issues and will not be enabled as an install option for the final release. 
You might have heard extra info we are not privvy too, no idea.

Is your crash a result of upgrading from alpha 5 to 6?

---

### Post by Technoviking on 2009-03-15
> **Yashiro said:**
> You might have heard extra info we are not privvy too, no idea.

Is your crash a result of upgrading from alpha 5 to 6?

Alpha 6.

Running
```
ecryptfs-add-passphrase
```
and setting the ecyptfs password to match login password fixed my problem.

---

### Post by Yashiro on 2009-03-15
Great.

---

