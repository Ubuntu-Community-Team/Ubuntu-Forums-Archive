---
title: "Karmic on Compaq Presario X1000 - EXT4-fs error (device sda3): check_block_validity:"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Vox Humana on 2009-10-25
I apologize if this isn't the right place to post this; please point me to the right one if so.

I loaded Karmic on my Presario X1000 yesterday - clean install, replacing a years-old CentOS 5 install that was very stable.  I've been experiencing frequent hard drive issues, where the root filesystem (EXT4) becomes inaccessible.  I can't say for sure that it only happens after an extended period of drive inactivity, but that's what it feels like.  I have disabled drive spin-down in System -> Preferences -> Power Management to no effect.  The system is not suspending/hibernating at all.

ETA: Restarted to Karmic CD, ran "e2fsck -f -c /dev/sda3", no errors or bad blocks were detected.

Below is a section of the system messages that I captured to an attached USB drive using dmesg > dmesg.log

[FONT=Courier New][ 5241.354840] EXT4-fs error (device sda3): check_block_validity: inode #4196 logical block 54 mapped to 67638 (size 2)
[ 5241.354855] Aborting journal on device sda3:8.
[ 5241.355176] EXT4-fs (sda3): Remounting filesystem read-only
[ 5241.355292] BUG: unable to handle kernel paging request at febaebc0
[ 5241.355299] IP: [<c0288850>] ext4_mb_load_buddy+0x50/0x2f0
[ 5241.355311] *pde = 00000000 
[ 5241.355315] Oops: 0000 [#1] SMP 
[ 5241.355320] last sysfs file: /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/C11F/charge_full
[ 5241.355326] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat usb_storage radeon ttm drm i2c_algo_bit arc4 ecb lib80211_crypt_wep binfmt_misc snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss ipw2200 libipw snd_mixer_oss snd_pcm pcmcia snd_seq_dummy snd_seq_oss iptable_filter smsc_ircc2 snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device yenta_socket rsrc_nonstatic ip_tables irda joydev pcmcia_core lib80211 crc_ccitt snd soundcore snd_page_alloc x_tables ppdev parport_pc shpchp psmouse wbsd serio_raw lp parport ohci1394 ieee1394 8139too 8139cp mii video output intel_agp agpgart
[ 5241.355391] 
[ 5241.355396] Pid: 3466, comm: rsyslogd Tainted: G        W  (2.6.31-14-generic #48-Ubuntu) Compaq Presario X1000 DM777A#ABA
[ 5241.355401] EIP: 0060:[<c0288850>] EFLAGS: 00010212 CPU: 0
[ 5241.355406] EIP is at ext4_mb_load_buddy+0x50/0x2f0
[ 5241.355410] EAX: f6baf000 EBX: f236def0 ECX: 01fffef0 EDX: 0000007f
[ 5241.355414] ESI: ffff7813 EDI: f6b79c00 EBP: f236dec0 ESP: f236dea4
[ 5241.355417]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[ 5241.355422] Process rsyslogd (pid: 3466, ti=f236c000 task=f414bed0 task.ti=f236c000)
[ 5241.355425] Stack:
[ 5241.355427]  f6d92518 00000001 bc099e39 01fffef0 f6ee3040 f236df04 f6b79c00 f236df2c
[ 5241.355436] <0> c0289ede f236df1c 00000000 f6ea9080 fffff000 c1bc2ce0 f236df14 f6ee3058
[ 5241.355445] <0> f6b79c00 f6def000 f6ea9214 c01cadb8 f414bed0 00000000 00000000 00000000
[ 5241.355455] Call Trace:
[ 5241.355462]  [<c0289ede>] ? ext4_discard_preallocations+0x19e/0x330
[ 5241.355469]  [<c01cadb8>] ? __do_fault+0x388/0x470
[ 5241.355478]  [<c025f06e>] ? ext4_release_file+0x9e/0xb0
[ 5241.355484]  [<c01e8cba>] ? __fput+0xda/0x1f0
[ 5241.355489]  [<c01e8de5>] ? fput+0x15/0x20
[ 5241.355494]  [<c01e53d7>] ? filp_close+0x47/0x70
[ 5241.355499]  [<c01e5473>] ? sys_close+0x73/0xb0
[ 5241.355504]  [<c010336c>] ? syscall_call+0x7/0xb
[ 5241.355507] Code: f7 77 0c 8b 97 98 01 00 00 89 45 e8 8b 4a 5c 89 f0 d3 e8 8b 8f 98 01 00 00 89 45 f0 8b 82 88 01 00 00 8b 51 18 8b 4d f0 83 ea 01 <8b> 04 88 21 f2 8b 04 90 89 f2 89 45 f0 0f b6 47 10 66 89 43 18 
[ 5241.355557] EIP: [<c0288850>] ext4_mb_load_buddy+0x50/0x2f0 SS:ESP 0068:f236dea4
[ 5241.355564] CR2: 00000000febaebc0
[ 5241.355568] ---[ end trace a7919e7f17c0a727 ]---
[ 5241.361119] ------------[ cut here ]------------
[ 5241.361127] WARNING: at /build/buildd/linux-2.6.31/fs/ext4/inode.c:1121 check_block_validity+0x99/0xa0()
[ 5241.361131] Hardware name: Compaq Presario X1000 DM777A#ABA
[ 5241.361134] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat usb_storage radeon ttm drm i2c_algo_bit arc4 ecb lib80211_crypt_wep binfmt_misc snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss ipw2200 libipw snd_mixer_oss snd_pcm pcmcia snd_seq_dummy snd_seq_oss iptable_filter smsc_ircc2 snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device yenta_socket rsrc_nonstatic ip_tables irda joydev pcmcia_core lib80211 crc_ccitt snd soundcore snd_page_alloc x_tables ppdev parport_pc shpchp psmouse wbsd serio_raw lp parport ohci1394 ieee1394 8139too 8139cp mii video output intel_agp agpgart
[ 5241.361198] Pid: 1238, comm: Xorg Tainted: G      D W  2.6.31-14-generic #48-Ubuntu
[ 5241.361202] Call Trace:
[ 5241.361210]  [<c014518d>] warn_slowpath_common+0x6d/0xa0
[ 5241.361215]  [<c02620c9>] ? check_block_validity+0x99/0xa0
[ 5241.361220]  [<c02620c9>] ? check_block_validity+0x99/0xa0
[ 5241.361226]  [<c01451d5>] warn_slowpath_null+0x15/0x20
[ 5241.361230]  [<c02620c9>] check_block_validity+0x99/0xa0
[ 5241.361236]  [<c02653fe>] ext4_get_blocks+0x1ae/0x200
[ 5241.361241]  [<c0265886>] ext4_get_block+0x66/0xf0
[ 5241.361261]  [<c021157e>] do_mpage_readpage+0x1be/0x730
[ 5241.361269]  [<c01c6498>] ? __inc_zone_page_state+0x18/0x20
[ 5241.361276]  [<c01b3078>] ? add_to_page_cache_locked+0xa8/0x100
[ 5241.361281]  [<c01b3114>] ? add_to_page_cache_lru+0x44/0x70
[ 5241.361286]  [<c0211c0f>] mpage_readpages+0xbf/0x100
[ 5241.361291]  [<c0265820>] ? ext4_get_block+0x0/0xf0
[ 5241.361296]  [<c0262420>] ? ext4_readpages+0x0/0x20
[ 5241.361300]  [<c0262439>] ext4_readpages+0x19/0x20
[ 5241.361305]  [<c0265820>] ? ext4_get_block+0x0/0xf0
[ 5241.361311]  [<c01bae99>] read_pages+0x29/0xc0
[ 5241.361317]  [<c01bb094>] __do_page_cache_readahead+0x164/0x190
[ 5241.361323]  [<c01bb0e1>] ra_submit+0x21/0x30
[ 5241.361328]  [<c01b2920>] do_sync_mmap_readahead+0x90/0xc0
[ 5241.361332]  [<c01b3c4d>] ? find_get_page+0x1d/0x90
[ 5241.361337]  [<c01b4af6>] filemap_fault+0x316/0x340
[ 5241.361345]  [<c015f4b0>] ? enqueue_hrtimer+0x60/0x80
[ 5241.361350]  [<c01caa6b>] __do_fault+0x3b/0x470
[ 5241.361357]  [<c05707da>] ? _spin_lock_irqsave+0x2a/0x40
[ 5241.361362]  [<c01cc264>] handle_mm_fault+0x134/0x380
[ 5241.361368]  [<c0572cf8>] do_page_fault+0x148/0x380
[ 5241.361374]  [<c01f6ecd>] ? sys_select+0x3d/0xb0
[ 5241.361380]  [<c0572bb0>] ? do_page_fault+0x0/0x380
[ 5241.361384]  [<c0570be3>] error_code+0x73/0x80
[ 5241.361388] ---[ end trace a7919e7f17c0a728 ]---
[ 5241.361396] EXT4-fs error (device sda3): check_block_validity: inode #4196 logical block 54 mapped to 67638 (size 1)[/FONT]

Thanks in advance for any help you can offer.

Dave

---

### Post by Vox Humana on 2009-10-25
Followup - I have downgraded the root FS to EXT3 (copy data to USB drive, reformat, copy from USB drive) and I got a similar error, so this appears to not be an EXT4 problem.  This still seems to be happening after the systems been idle for several (15 or so) minutes.  I'll capture the dmesg the next time and post it here.

---

### Post by Vox Humana on 2009-10-25
OK, this seems to be related to the screensaver/GL rendering:


[LIST]
[*]If I let the machine go to screensaver - timeout is set to 10 minutes - the filesystem becomes inaccessible.
[*]If I try to access the drive after 9 minutes of idle time it works properly.
[*]The filesystem will freeze as soon as I bring up the screensaver dialog with a GL screensaver being previewed.
[/LIST]

So it's an issue with my video card - ATI Radeon Mobility - displaying GL screensavers.  It's odd that a video card issue would manifest itself as a filesystem problem - the video works fine even after the screensaver starts and ends - but that's where the evidence leads.

---

