---
title: "Computer hard locks up loading page on Firefox (compiz.real)"
date: 2009-07-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tghe-retford on 2009-07-13
Had something completely weird happen with my computer a few minutes ago. As I loaded a page on Firefox, the computer just hard locked up, everything stopped working aside from the keyboard. The only way to get out was to use ALT+SYS RQ+REISUB.

Kernel log when the crash occurred:
```
Jul 13 19:24:33 TGHE kernel: [ 1943.845872] PGD 7e49a067 PUD 6e5b2067 PMD 0 
Jul 13 19:24:33 TGHE kernel: [ 1943.845881] CPU 1 
Jul 13 19:24:33 TGHE kernel: [ 1943.845883] Modules linked in: binfmt_misc bridge stp bnep video output lp snd_hda_codec_realtek dvb_pll cx22702 cx88_dvb cx88_vp3054_i2c videobuf_dvb dvb_core snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer cx8802 cx8800 cx88xx snd_seq_device ir_common i2c_algo_bit v4l2_common ppdev psmouse snd i2c_nforce2 tveeprom videodev v4l1_compat v4l2_compat_ioctl32 videobuf_dma_sg videobuf_core btcx_risc serio_raw pcspkr soundcore snd_page_alloc joydev asus_atk0110 parport_pc parport nvidia(P) hid_microsoft ohci1394 ieee1394 forcedeth usbhid vesafb fbcon tileblit font bitblit softcursor
Jul 13 19:24:33 TGHE kernel: [ 1943.845922] Pid: 4013, comm: compiz.real Tainted: P           2.6.30-8-generic #9-Ubuntu System Product Name
Jul 13 19:24:33 TGHE kernel: [ 1943.845924] RIP: 0010:[<ffffffffa0545fd6>]  [<ffffffffa0545fd6>] _nv010124rm+0x6/0x34c [nvidia]
Jul 13 19:24:33 TGHE kernel: [ 1943.846030] RSP: 0018:ffff880069db5d08  EFLAGS: 00010202
Jul 13 19:24:33 TGHE kernel: [ 1943.846031] RAX: 0000000000000000 RBX: ffff88007d9ae400 RCX: ffff88007cd20000
Jul 13 19:24:33 TGHE kernel: [ 1943.846034] RDX: ffff88007cd20350 RSI: ffff88007cd20000 RDI: ffff880078d4a000
Jul 13 19:24:33 TGHE kernel: [ 1943.846036] RBP: ffff88006b9b5bd0 R08: ffff88007dc32000 R09: 0000000000000008
Jul 13 19:24:33 TGHE kernel: [ 1943.846038] R10: 0000000000000000 R11: 0000000000000206 R12: ffff88007cd20000
Jul 13 19:24:33 TGHE kernel: [ 1943.846040] R13: ffff880078d4a000 R14: ffff88007c842000 R15: ffff88007f1c94a8
Jul 13 19:24:33 TGHE kernel: [ 1943.846042] FS:  00007f037bc1a780(0000) GS:ffff88000102b000(0000) knlGS:0000000000000000
Jul 13 19:24:33 TGHE kernel: [ 1943.846044] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jul 13 19:24:33 TGHE kernel: [ 1943.846046] CR2: 000000000000024e CR3: 000000006b98c000 CR4: 00000000000006a0
Jul 13 19:24:33 TGHE kernel: [ 1943.846048] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jul 13 19:24:33 TGHE kernel: [ 1943.846050] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jul 13 19:24:33 TGHE kernel: [ 1943.846053] Process compiz.real (pid: 4013, threadinfo ffff880069db4000, task ffff88006e7ad9c0)
Jul 13 19:24:33 TGHE kernel: [ 1943.846056]  ffff880078d4a000 ffff88007c842000 ffff88007f1c94a8 ffffffffa043c909
Jul 13 19:24:33 TGHE kernel: [ 1943.847242]  RSP <ffff880069db5d08>
Jul 13 19:24:33 TGHE kernel: [ 1943.847246] ---[ end trace cc5125079f6c2807 ]---
Jul 13 19:25:21 TGHE kernel: [ 1991.889798] SysRq : Keyboard mode set to system default
Jul 13 19:25:22 TGHE exiting on signal 15
```
Annoying, as I was trying to figure out another problem with Firefox at the time. Anyone else had the same problem?

---

