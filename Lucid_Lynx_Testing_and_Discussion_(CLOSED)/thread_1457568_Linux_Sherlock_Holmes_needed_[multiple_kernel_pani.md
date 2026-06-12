---
title: "Linux Sherlock Holmes needed [multiple kernel panic, apparently unrelated]"
date: 2010-04-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by pedrogfrancisco on 2010-04-18
Hi!
I'm going to use this thread to dump information.

The situation: using a setup with an ath5k + iwl3945 wireless + usbserial GPS I'm having issues.

These issues are Kernel Panics which seem unrelated between themselves.
These issues existed in 9.10, which made me upgrade earlier.
These issues haven't been reported to kerneloops.org 'cause the frakin' uploader gets a permission denied error.

So people, here we go!



First, 2 apps then 3 kernel (**unable to handle paging request**) then 3 networking!

Fight!

**App 1**
```
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.018943] Modules linked in: cp210x ppp_async crc_ccitt ppdev joydev snd_hda_codec_si3054 snd_hda_codec_realtek fbcon tileblit font bitblit s
oftcursor vga16fb vgastate ipt_REJECT ipt_LOG xt_limit xt_tcpudp ipt_addrtype xt_state snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm ip6table_filter ip6_t
ables nf_nat_irc nf_conntrack_irc arc4 nf_nat_ftp nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_conntrack_ftp nf_conntrack snd_seq_dummy iptable_filter snd_seq_oss snd_seq_midi snd_ra
wmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device option ath5k i915 drm_kms_helper ath ip_tables snd uvcvideo sdhci_pci iwl3945 drm i2c_algo_bit soundcore x_tables videodev
 v4l1_compat usbserial usb_storage psmouse serio_raw ricoh_mmc sdhci lp intel_agp video iwlcore snd_page_alloc output mac80211 cfg80211 led_class parport agpgart usbhid hid ohci139
4 ieee1394 r8169 mii ahci
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019089] 
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019096] Pid: 2768, comm: hald-addon-stor Not tainted (2.6.32-21-generic #32-Ubuntu) HP Pavilion dv6500 Notebook PC    
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019102] EIP: 0060:[<c043cd05>] EFLAGS: 00010282 CPU: 0
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019112] EIP is at cdrom_ioctl_drive_status+0x15/0x120
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019117] EAX: f68dc198 EBX: ffffffe7 ECX: 00000000 EDX: 7fffffff
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019122] ESI: f6c22c00 EDI: 00005326 EBP: f2d5fe48 ESP: f2d5fe34
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019127]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019141]  00000000 39f1684a ffffffe7 f6c22c00 00005326 f2d5fea4 c043e58d 00005326
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019155] <0> 7fffffff f68dc198 c02328d9 f3270700 f68cf068 f70c8300 f2d5fe94 c0205f3f
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019170] <0> c02f551d f2d5fe88 c0210d7e f6cd6440 00000000 f6cd6440 f3270700 f2d5fef0
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019196]  [<c043e58d>] ? cdrom_ioctl+0x3ad/0xa40
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019205]  [<c02328d9>] ? blkdev_open+0x99/0xb0
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019214]  [<c0205f3f>] ? __dentry_open+0x1af/0x290
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019222]  [<c02f551d>] ? security_inode_permission+0x1d/0x30
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019231]  [<c0210d7e>] ? inode_permission+0x9e/0xb0
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019239]  [<c040daaf>] ? sr_block_ioctl+0x4f/0xa0
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019247]  [<c033f732>] ? __blkdev_driver_ioctl+0x72/0x80
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019255]  [<c033fbe9>] ? blkdev_ioctl+0x1e9/0x750
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019263]  [<c02312b1>] ? block_ioctl+0x31/0x50
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019270]  [<c0231280>] ? block_ioctl+0x0/0x50
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019276]  [<c0216231>] ? vfs_ioctl+0x21/0x90
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019284]  [<c02110fb>] ? putname+0x2b/0x40
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019290]  [<c0216519>] ? do_vfs_ioctl+0x79/0x310
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019297]  [<c0216817>] ? sys_ioctl+0x67/0x80
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019304]  [<c0205d4e>] ? sys_open+0x2e/0x40
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019311]  [<c01033ec>] ? syscall_call+0x7/0xb
Apr 18 22:22:44 MY_HOSTNAME kernel: [ 5849.019418] ---[ end trace dcdc34a905329518 ]---
```



**App 2**
```
Apr 18 23:05:09 MY_HOSTNAME kernel: [ 8394.972557] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat cp210x ppp_async crc_ccitt ppdev joydev snd_hda_codec_si3054 snd_hda_codec_real
tek fbcon tileblit font bitblit softcursor vga16fb vgastate ipt_REJECT ipt_LOG xt_limit xt_tcpudp ipt_addrtype xt_state snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_
oss snd_pcm ip6table_filter ip6_tables nf_nat_irc nf_conntrack_irc arc4 nf_nat_ftp nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_conntrack_ftp nf_conntrack snd_seq_dummy iptable_filte
r snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device option ath5k i915 drm_kms_helper ath ip_tables snd uvcvideo sdhci_pci iwl3945 drm i2c_alg
o_bit soundcore x_tables videodev v4l1_compat usbserial usb_storage psmouse serio_raw ricoh_mmc sdhci lp intel_agp video iwlcore snd_page_alloc output mac80211 cfg80211 led_class p
arport agpgart usbhid hid ohci1394 ieee1394 r8169 mii ahci
Apr 18 23:05:09 MY_HOSTNAME kernel: [ 8394.972659] 
Apr 18 23:05:09 MY_HOSTNAME kernel: [ 8394.972665] Pid: 1077, comm: Xorg Tainted: G      D    (2.6.32-21-generic #32-Ubuntu) HP Pavilion dv6500 Notebook PC    
Apr 18 23:05:09 MY_HOSTNAME kernel: [ 8394.972669] EIP: 0060:[<c01e7d29>] EFLAGS: 00013286 CPU: 1
Apr 18 23:05:09 MY_HOSTNAME kernel: [ 8394.972673] EIP is at find_vma+0x39/0x80
Apr 18 23:05:09 MY_HOSTNAME kernel: [ 8394.972676] EAX: f4324a80 EBX: bf68009c ECX: bf6800b4 EDX: b3cfd000
Apr 18 23:05:09 MY_HOSTNAME kernel: [ 8394.972679] ESI: f23cc000 EDI: f4324a80 EBP: f2c09f10 ESP: f2c09f08
Apr 18 23:05:09 MY_HOSTNAME kernel: [ 8394.972683]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Apr 18 23:05:09 MY_HOSTNAME kernel: [ 8394.972691]  b3cfd000 00001000 f2c09f38 c01e7f35 00000000 f2c09e70 b3d01000 f33e8a00
Apr 18 23:05:09 MY_HOSTNAME kernel: [ 8394.972701] <0> 00000000 00001000 c01e7ec0 f4324a80 f2c09f50 c01e8183 0011c4a6 00000001
Apr 18 23:05:09 MY_HOSTNAME kernel: [ 8394.972711] <0> ffffffb5 f33e8a00 f2c09f84 c01ea876 0011c4a6 00000001 00000000 f2c09f8c
Apr 18 23:05:09 MY_HOSTNAME kernel: [ 8394.972728]  [<c01e7f35>] ? arch_get_unmapped_area_topdown+0x75/0x170
Apr 18 23:05:09 MY_HOSTNAME kernel: [ 8394.972733]  [<c01e7ec0>] ? arch_get_unmapped_area_topdown+0x0/0x170
Apr 18 23:05:09 MY_HOSTNAME kernel: [ 8394.972739]  [<c01e8183>] ? get_unmapped_area_prot+0x53/0xb0
Apr 18 23:05:09 MY_HOSTNAME kernel: [ 8394.972744]  [<c01ea876>] ? do_mmap_pgoff+0xf6/0x300
Apr 18 23:05:09 MY_HOSTNAME kernel: [ 8394.972750]  [<c01dea33>] ? sys_mmap_pgoff+0x193/0x240
Apr 18 23:05:09 MY_HOSTNAME kernel: [ 8394.972755]  [<c01033ec>] ? syscall_call+0x7/0xb
Apr 18 23:05:09 MY_HOSTNAME kernel: [ 8394.972827] ---[ end trace dcdc34a905329519 ]---

```



**Kernel 1 -- BUG: unable to handle kernel paging request at 50001989**
```
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.116999] BUG: unable to handle kernel paging request at 50001989
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117009] IP: [<f864149e>] i915_gem_object_get_pages+0x6e/0x140 [i915]
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012] *pde = 00000000 
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012] Oops: 0000 [#1] SMP 
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012] last sysfs file: /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0A:00/power_supply/BAT0/charge_full
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012] Modules linked in: btrfs zlib_deflate crc32c libcrc32c ufs qnx4 hfsplus hfs minix ntfs vfat msdos fat jfs xfs exportfs reiserfs ppp
_async crc_ccitt ppdev joydev snd_hda_codec_si3054 snd_hda_codec_realtek fbcon tileblit font bitblit softcursor vga16fb vgastate snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss s
nd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi cp210x ath5k snd_rawmidi arc4 snd_seq_midi_event snd_seq snd_timer snd_seq_device iwl3945 iwlcore ath option snd i915 dr
m_kms_helper mac80211 uvcvideo videodev v4l1_compat usbserial usb_storage intel_agp soundcore lp psmouse serio_raw drm i2c_algo_bit ricoh_mmc sdhci_pci sdhci led_class cfg80211 vid
eo snd_page_alloc agpgart output parport usbhid hid ohci1394 ieee1394 ahci r8169 mii
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012] 
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012] Pid: 1044, comm: Xorg Not tainted (2.6.32-20-generic #30-Ubuntu) HP Pavilion dv6500 Notebook PC    
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012] EIP: 0060:[<f864149e>] EFLAGS: 00013282 CPU: 1
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012] EIP is at i915_gem_object_get_pages+0x6e/0x140 [i915]
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012] EAX: 500018dd EBX: f2e272a0 ECX: 00000000 EDX: f2e272a0
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012] ESI: f2e75080 EDI: 00000000 EBP: f3bd1ce8 ESP: f3bd1ccc
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012] Process Xorg (pid: 1044, ti=f3bd0000 task=f6904ce0 task.ti=f3bd0000)
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012] Stack:
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  f1100640 f2e272a0 00001200 00000001 f2e272a0 f2e75080 00000000 f3bd1d1c
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012] <0> f8643d48 00000000 f863fcac fa293000 ffffffff f4af5de4 00001200 f7173c00
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012] <0> 00001000 f2e75080 f2e272a0 f7173c00 f3bd1d30 f8643ffd 00000000 fa28e540
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012] Call Trace:
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  [<f8643d48>] ? i915_gem_object_bind_to_gtt+0xb8/0x2e0 [i915]
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  [<f863fcac>] ? i915_gem_object_flush_cpu_write_domain+0x3c/0x80 [i915]
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  [<f8643ffd>] ? i915_gem_object_pin+0x8d/0xa0 [i915]
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  [<f864473f>] ? i915_gem_object_pin_and_relocate+0x4f/0x3d0 [i915]
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  [<f86454f5>] ? i915_gem_do_execbuffer+0x255/0xc40 [i915]
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  [<c01ef86b>] ? __vmalloc_node+0x9b/0xa0
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  [<f86454f5>] ? i915_gem_do_execbuffer+0x255/0xc40 [i915]
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  [<f86456ab>] ? i915_gem_do_execbuffer+0x40b/0xc40 [i915]
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  [<c01ef925>] ? __vmalloc_area_node+0xb5/0x110
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  [<f864638d>] ? i915_gem_execbuffer+0x2fd/0x3d0 [i915]
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  [<f864638d>] ? i915_gem_execbuffer+0x2fd/0x3d0 [i915]
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  [<f864623b>] ? i915_gem_execbuffer+0x1ab/0x3d0 [i915]
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  [<c035315d>] ? copy_from_user+0x3d/0x130
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  [<f814e7cd>] ? drm_ioctl+0x25d/0x3e0 [drm]
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  [<f8646090>] ? i915_gem_execbuffer+0x0/0x3d0 [i915]
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  [<c0167740>] ? autoremove_wake_function+0x0/0x50
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  [<c02f4394>] ? security_file_permission+0x14/0x20
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  [<f814e570>] ? drm_ioctl+0x0/0x3e0 [drm]
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  [<c02161c1>] ? vfs_ioctl+0x21/0x90
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  [<c02164a9>] ? do_vfs_ioctl+0x79/0x310
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  [<c02167a7>] ? sys_ioctl+0x67/0x80
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012]  [<c01033ec>] ? syscall_call+0x7/0xb
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012] Code: 00 10 00 00 0f 87 85 00 00 00 ba d0 80 00 00 e8 a9 c1 bb c7 85 c0 89 46 2c 0f 84 84 00 00 00 8b 55 e8 8b 42 0c 8b 40 0c 8b 40 10 <8b> b8 ac 00 00 00 8b 45 f0 85 c0 7e 32 31 db 8d 76 00 8b 4f 3c 
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012] EIP: [<f864149e>] i915_gem_object_get_pages+0x6e/0x140 [i915] SS:ESP 0068:f3bd1ccc
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117012] CR2: 0000000050001989
Apr 14 18:57:20 MY_HOSTNAME kernel: [ 1957.117650] ---[ end trace 0e73e01e9206c6b2 ]---

```



**Kernel 2 -- BUG: unable to handle kernel paging request at 5d2b8498**
```
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347336] BUG: unable to handle kernel paging request at 5d2b8498
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347346] IP: [<c02f327b>] get_vfs_caps_from_disk+0x6b/0xe0
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347357] *pde = 00000000 
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347361] Oops: 0002 [#1] SMP 
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347366] last sysfs file: /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0A:00/power_supply/BAT0/charge_full
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347371] Modules linked in: rfcomm sco bridge stp bnep l2cap btusb bluetooth cp210x ppp_async crc_ccitt ppdev snd_hda_codec_si3054 snd_hda_c
odec_realtek snd_hda_intel fbcon tileblit font bitblit snd_hda_codec softcursor vga16fb snd_hwdep vgastate snd_pcm_oss snd_mixer_oss snd_pcm joydev snd_seq_dummy snd_seq_oss snd_se
q_midi snd_rawmidi arc4 snd_seq_midi_event i915 iwl3945 lp sdhci_pci uvcvideo drm_kms_helper snd_seq iwlcore ath5k videodev snd_timer snd_seq_device sdhci mac80211 intel_agp drm op
tion i2c_algo_bit agpgart video usbserial output ricoh_mmc psmouse ath parport v4l1_compat led_class serio_raw snd soundcore snd_page_alloc cfg80211 usb_storage usbhid hid ohci1394
 ahci ieee1394 r8169 mii
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347458] 
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347463] Pid: 3767, comm: kpackagekit Not tainted (2.6.32-20-generic #30-Ubuntu) HP Pavilion dv6500 Notebook PC    
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347467] EIP: 0060:[<c02f327b>] EFLAGS: 00210282 CPU: 0
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347471] EIP is at get_vfs_caps_from_disk+0x6b/0xe0
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347475] EAX: 00031050 EBX: de5b1c38 ECX: 00000000 EDX: 85c07464
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347478] ESI: e52b5e4c EDI: c0223180 EBP: e52b5e24 ESP: e52b5e00
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347481]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347485] Process kpackagekit (pid: 3767, ti=e52b4000 task=e1c10cd0 task.ti=e52b4000)
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347488] Stack:
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347490]  00000014 c0212b12 c0167760 00000000 00000000 00000500 e3459600 de5b1c38
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347500] <0> dfecc880 e52b5e6c c02f3996 00000001 c63f1400 c0798c20 df8a0000 e52b5e8f
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347510] <0> e52b5e68 c01ceda5 000284d0 00000000 00000000 00000000 00000000 00000000
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347521] Call Trace:
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347528]  [<c0212b12>] ? __link_path_walk+0x632/0xca0
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347534]  [<c0167760>] ? autoremove_wake_function+0x20/0x50
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347539]  [<c02f3996>] ? get_file_caps+0x76/0x190
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347544]  [<c01ceda5>] ? prep_new_page+0xf5/0x170
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347549]  [<c02f3ae2>] ? cap_bprm_set_creds+0x32/0x290
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347555]  [<c031dcab>] ? apparmor_bprm_set_creds+0x7b/0x4d0
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347560]  [<c01e8a95>] ? __vma_link_rb+0x35/0x40
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347565]  [<c01e8ae4>] ? __vma_link+0x44/0x90
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347569]  [<c01ea161>] ? __vm_enough_memory+0x31/0x160
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347575]  [<c02f3fe1>] ? security_bprm_set_creds+0x11/0x20
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347580]  [<c020dcc5>] ? prepare_binprm+0xa5/0x100
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347585]  [<c020e9ce>] ? do_execve+0x17e/0x2c0
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347589]  [<c0352f6a>] ? strncpy_from_user+0x3a/0x70
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347594]  [<c0101a1d>] ? sys_execve+0x2d/0x60
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347599]  [<c01033ec>] ? syscall_call+0x7/0xb
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347602] Code: 8b 82 9c 00 00 00 8b 78 48 85 ff 74 dd 8d 4d e0 ba 12 2c 6e c0 c7 04 24 14 00 00 00 89 d8 ff d7 8d 80 8d 10 03 00 ba 64 74 c0 85 <c0> 8d 74 26 00 78 bd 83 f8 03 77 0b b8 ea ff ff ff 8d 74 26 00 
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347662] EIP: [<c02f327b>] get_vfs_caps_from_disk+0x6b/0xe0 SS:ESP 0068:e52b5e00
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347669] CR2: 000000005d2b8498
Apr 14 20:42:50 MY_HOSTNAME kernel: [ 6273.347673] ---[ end trace 8c53f5a257c1836c ]---
```



**Kernel 3 -- BUG: unable to handle kernel paging request at 57f26498**
```
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480737] BUG: unable to handle kernel paging request at 57f26498
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480746] IP: [<c02f327b>] get_vfs_caps_from_disk+0x6b/0xe0
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480757] *pde = 00000000 
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480761] Oops: 0002 [#3] SMP 
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480766] last sysfs file: /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0A:00/power_supply/BAT0/charge_full
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480771] Modules linked in: rfcomm sco bridge stp bnep l2cap btusb bluetooth cp210x ppp_async crc_ccitt ppdev snd_hda_codec_si3054 snd_hda_c
odec_realtek snd_hda_intel fbcon tileblit font bitblit snd_hda_codec softcursor vga16fb snd_hwdep vgastate snd_pcm_oss snd_mixer_oss snd_pcm joydev snd_seq_dummy snd_seq_oss snd_se
q_midi snd_rawmidi arc4 snd_seq_midi_event i915 iwl3945 lp sdhci_pci uvcvideo drm_kms_helper snd_seq iwlcore ath5k videodev snd_timer snd_seq_device sdhci mac80211 intel_agp drm op
tion i2c_algo_bit agpgart video usbserial output ricoh_mmc psmouse ath parport v4l1_compat led_class serio_raw snd soundcore snd_page_alloc cfg80211 usb_storage usbhid hid ohci1394
 ahci ieee1394 r8169 mii
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480860] 
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480865] Pid: 3773, comm: kpackagekit Tainted: G      D    (2.6.32-20-generic #30-Ubuntu) HP Pavilion dv6500 Notebook PC    
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480869] EIP: 0060:[<c02f327b>] EFLAGS: 00210282 CPU: 0
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480874] EIP is at get_vfs_caps_from_disk+0x6b/0xe0
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480877] EAX: 00031050 EBX: de5b1c38 ECX: 00000000 EDX: 85c07464
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480880] ESI: dff23e4c EDI: c0223180 EBP: dff23e24 ESP: dff23e00
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480883]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480887] Process kpackagekit (pid: 3773, ti=dff22000 task=e1c10cd0 task.ti=dff22000)
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480890] Stack:
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480892]  00000014 c0212b12 c0167760 00000000 00000000 00000500 e1c70700 de5b1c38
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480902] <0> e198f480 dff23e6c c02f3996 00000001 c6439580 c0798c20 e1cac000 dff23e8f
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480912] <0> dff23e68 c01ceda5 000284d0 00000000 00000000 00000000 00000000 00000000
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480923] Call Trace:
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480930]  [<c0212b12>] ? __link_path_walk+0x632/0xca0
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480936]  [<c0167760>] ? autoremove_wake_function+0x20/0x50
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480941]  [<c02f3996>] ? get_file_caps+0x76/0x190
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480947]  [<c01ceda5>] ? prep_new_page+0xf5/0x170
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480952]  [<c02f3ae2>] ? cap_bprm_set_creds+0x32/0x290
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480958]  [<c031dcab>] ? apparmor_bprm_set_creds+0x7b/0x4d0
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480964]  [<c01e8a95>] ? __vma_link_rb+0x35/0x40
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480968]  [<c01e8ae4>] ? __vma_link+0x44/0x90
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480973]  [<c01ea161>] ? __vm_enough_memory+0x31/0x160
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480979]  [<c02f3fe1>] ? security_bprm_set_creds+0x11/0x20
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480984]  [<c020dcc5>] ? prepare_binprm+0xa5/0x100
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480988]  [<c020e9ce>] ? do_execve+0x17e/0x2c0
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480993]  [<c0352f6a>] ? strncpy_from_user+0x3a/0x70
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.480998]  [<c0101a1d>] ? sys_execve+0x2d/0x60
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.481003]  [<c01033ec>] ? syscall_call+0x7/0xb
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.481006] Code: 8b 82 9c 00 00 00 8b 78 48 85 ff 74 dd 8d 4d e0 ba 12 2c 6e c0 c7 04 24 14 00 00 00 89 d8 ff d7 8d 80 8d 10 03 00 ba 64 74 c0 85 <c0> 8d 74 26 00 78 bd 83 f8 03 77 0b b8 ea ff ff ff 8d 74 26 00 
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.481066] EIP: [<c02f327b>] get_vfs_caps_from_disk+0x6b/0xe0 SS:ESP 0068:dff23e00
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.481073] CR2: 0000000057f26498
Apr 14 20:42:58 MY_HOSTNAME kernel: [ 6281.481078] ---[ end trace 8c53f5a257c1836e ]---
```


_(and it goes on complaining about other memory locations)_



And now, the network related ones!


**Network 1**
```
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.068876] ------------[ cut here ]------------
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.068893] WARNING: at /build/buildd/linux-2.6.32/drivers/net/wireless/ath/ath5k/base.c:1142 ath5k_tasklet_rx+0x53b/0x5a0 [ath5k]()
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.068898] Hardware name: HP Pavilion dv6500 Notebook PC    
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.068902] invalid hw_rix: 1b
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.068905] Modules linked in: rfcomm ppdev sco bridge stp bnep l2cap ipt_REJECT ipt_LOG snd_hda_codec_si3054 snd_hda_codec_realtek xt_limit fb
con tileblit font bitblit softcursor xt_tcpudp vga16fb vgastate ipt_addrtype xt_state snd_hda_intel ip6table_filter snd_hda_codec ip6_tables snd_hwdep snd_pcm_oss snd_mixer_oss snd
_pcm nf_nat_irc snd_seq_dummy nf_conntrack_irc snd_seq_oss snd_seq_midi nf_nat_ftp nf_nat snd_rawmidi snd_seq_midi_event nf_conntrack_ipv4 nf_defrag_ipv4 arc4 joydev nf_conntrack_f
tp snd_seq i915 iwl3945 snd_timer nf_conntrack uvcvideo drm_kms_helper sdhci_pci snd_seq_device iwlcore ath5k videodev sdhci drm psmouse iptable_filter snd i2c_algo_bit ricoh_mmc a
th v4l1_compat mac80211 soundcore ip_tables x_tables serio_raw intel_agp video snd_page_alloc cfg80211 led_class btusb agpgart output bluetooth lp parport usbhid hid ohci1394 ieee1
394 ahci r8169 mii
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069042] Pid: 0, comm: swapper Tainted: G        W  2.6.32-21-generic #31-Ubuntu
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069046] Call Trace:
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069056]  [<c014c3d2>] warn_slowpath_common+0x72/0xa0
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069069]  [<f86b947b>] ? ath5k_tasklet_rx+0x53b/0x5a0 [ath5k]
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069081]  [<f86b947b>] ? ath5k_tasklet_rx+0x53b/0x5a0 [ath5k]
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069088]  [<c014c44b>] warn_slowpath_fmt+0x2b/0x30
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069102]  [<f86b947b>] ath5k_tasklet_rx+0x53b/0x5a0 [ath5k]
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069112]  [<c0151a77>] tasklet_action+0xa7/0xb0
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069119]  [<c0153068>] __do_softirq+0x98/0x1b0
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069126]  [<c012293b>] ? ack_apic_level+0x6b/0x170
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069132]  [<c016d7de>] ? sched_clock_tick+0x5e/0xa0
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069139]  [<c01531c5>] do_softirq+0x45/0x50
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069145]  [<c0153315>] irq_exit+0x65/0x70
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069152]  [<c058fa25>] do_IRQ+0x55/0xc0
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069158]  [<c016d4f5>] ? sched_clock_local+0xa5/0x180
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069165]  [<c0103a30>] common_interrupt+0x30/0x40
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069172]  [<c016007b>] ? sys_setrlimit+0xcb/0x120
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069179]  [<c039ccad>] ? acpi_idle_enter_bm+0x26b/0x29a
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069187]  [<c04a076a>] cpuidle_idle_call+0x7a/0x100
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069193]  [<c01021d4>] cpu_idle+0x94/0xd0
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069201]  [<c0579168>] rest_init+0x58/0x60
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069208]  [<c07a38ec>] start_kernel+0x351/0x357
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069214]  [<c07a33c7>] ? unknown_bootoption+0x0/0x19e
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069222]  [<c07a30aa>] i386_start_kernel+0xaa/0xb1
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069226] ---[ end trace 619124d376e0cfc1 ]---
Apr 16 13:16:33 MY_HOSTNAME kernel: [ 4836.069245] ------------[ cut here ]------------
```


**Network 2**
```
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.941762] ------------[ cut here ]------------
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.941791] WARNING: at /build/buildd/linux-2.6.32/net/mac80211/util.c:1056 ieee80211_reconfig+0x2ec/0x3e0 [mac80211]()
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.941794] Hardware name: HP Pavilion dv6500 Notebook PC    
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.941796] Harware became unavailable upon resume. This is could be a software issueprior to suspend or a harware issue
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.941798] Modules linked in: rfcomm ppdev sco bridge stp bnep l2cap ipt_REJECT ipt_LOG snd_hda_codec_si3054 snd_hda_codec_realtek xt_limit fb
con tileblit font bitblit softcursor xt_tcpudp vga16fb vgastate ipt_addrtype xt_state snd_hda_intel ip6table_filter snd_hda_codec ip6_tables snd_hwdep snd_pcm_oss snd_mixer_oss snd
_pcm nf_nat_irc snd_seq_dummy nf_conntrack_irc snd_seq_oss snd_seq_midi nf_nat_ftp nf_nat snd_rawmidi snd_seq_midi_event nf_conntrack_ipv4 nf_defrag_ipv4 arc4 joydev nf_conntrack_f
tp snd_seq i915 iwl3945 snd_timer nf_conntrack uvcvideo drm_kms_helper sdhci_pci snd_seq_device iwlcore ath5k videodev sdhci drm psmouse iptable_filter snd i2c_algo_bit ricoh_mmc a
th v4l1_compat mac80211 soundcore ip_tables x_tables serio_raw intel_agp video snd_page_alloc cfg80211 led_class btusb agpgart output bluetooth lp parport usbhid hid ohci1394 ieee1
394 ahci r8169 mii
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.941873] Pid: 3892, comm: pm-suspend Tainted: G        W  2.6.32-21-generic #31-Ubuntu
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.941876] Call Trace:
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.941887]  [<c014c3d2>] warn_slowpath_common+0x72/0xa0
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.941902]  [<f84dd95c>] ? ieee80211_reconfig+0x2ec/0x3e0 [mac80211]
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.941920]  [<f84dd95c>] ? ieee80211_reconfig+0x2ec/0x3e0 [mac80211]
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.941924]  [<c014c44b>] warn_slowpath_fmt+0x2b/0x30
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.941944]  [<f84dd95c>] ieee80211_reconfig+0x2ec/0x3e0 [mac80211]
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.941956]  [<c03eb3b0>] ? device_show_time+0x20/0x160
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.941969]  [<f84d54e6>] ieee80211_resume+0x16/0x20 [mac80211]
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.941984]  [<f814b496>] wiphy_resume+0x66/0x80 [cfg80211]
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.941988]  [<c03eb906>] device_resume+0x136/0x150
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.941994]  [<c034bd02>] ? kobject_get+0x12/0x20
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.941998]  [<c03eb9d1>] dpm_resume+0xb1/0x140
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.942002]  [<c03eba77>] dpm_resume_end+0x17/0x30
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.942008]  [<c01838e7>] suspend_devices_and_enter+0x97/0xd0
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.942013]  [<c0588f42>] ? printk+0x1d/0x23
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.942018]  [<c01839dd>] enter_state+0xbd/0xf0
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.942022]  [<c0183095>] state_store+0x75/0xc0
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.942026]  [<c0183020>] ? state_store+0x0/0xc0
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.942031]  [<c034ba80>] kobj_attr_store+0x20/0x30
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.942036]  [<c025e0b5>] sysfs_write_file+0x95/0x100
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.942042]  [<c0207bf2>] vfs_write+0xa2/0x1a0
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.942046]  [<c025e020>] ? sysfs_write_file+0x0/0x100
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.942051]  [<c058dae0>] ? do_page_fault+0x160/0x3a0
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.942055]  [<c0208512>] sys_write+0x42/0x70
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.942059]  [<c01033ec>] syscall_call+0x7/0xb
Apr 16 15:09:46 MY_HOSTNAME kernel: [ 5667.942062] ---[ end trace 619124d376e0cfcc ]---
```




**Network 3**
```
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.001326] ------------[ cut here ]------------
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.001367] WARNING: at /build/buildd/linux-2.6.32/net/mac80211/mlme.c:2091 ieee80211_sta_work+0x27d/0x460 [mac80211]()
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.001373] Hardware name: HP Pavilion dv6500 Notebook PC    
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.001376] STA MLME work scheduled while going to suspend
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.001380] Modules linked in: rfcomm ppdev sco bridge stp bnep l2cap ipt_REJECT ipt_LOG snd_hda_codec_si3054 snd_hda_codec_realtek xt_limit fb
con tileblit font bitblit softcursor xt_tcpudp vga16fb vgastate ipt_addrtype xt_state snd_hda_intel ip6table_filter snd_hda_codec ip6_tables snd_hwdep snd_pcm_oss snd_mixer_oss snd
_pcm nf_nat_irc snd_seq_dummy nf_conntrack_irc snd_seq_oss snd_seq_midi nf_nat_ftp nf_nat snd_rawmidi snd_seq_midi_event nf_conntrack_ipv4 nf_defrag_ipv4 arc4 joydev nf_conntrack_f
tp snd_seq i915 iwl3945 snd_timer nf_conntrack uvcvideo drm_kms_helper sdhci_pci snd_seq_device iwlcore ath5k videodev sdhci drm psmouse iptable_filter snd i2c_algo_bit ricoh_mmc a
th v4l1_compat mac80211 soundcore ip_tables x_tables serio_raw intel_agp video snd_page_alloc cfg80211 led_class btusb agpgart output bluetooth lp parport usbhid hid ohci1394 ieee1
394 ahci r8169 mii
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.001523] Pid: 704, comm: phy0 Tainted: G        W  2.6.32-21-generic #31-Ubuntu
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.001528] Call Trace:
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.001548]  [<c014c3d2>] warn_slowpath_common+0x72/0xa0
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.001563]  [<f84d0c7d>] ? ieee80211_sta_work+0x27d/0x460 [mac80211]
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.001578]  [<f84d0c7d>] ? ieee80211_sta_work+0x27d/0x460 [mac80211]
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.001583]  [<c014c44b>] warn_slowpath_fmt+0x2b/0x30
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.001600]  [<f84d0c7d>] ieee80211_sta_work+0x27d/0x460 [mac80211]
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.001609]  [<c013eff3>] ? finish_task_switch+0x43/0xc0
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.001616]  [<c016369e>] run_workqueue+0x8e/0x150
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.001629]  [<f84d0a00>] ? ieee80211_sta_work+0x0/0x460 [mac80211]
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.001634]  [<c01637e4>] worker_thread+0x84/0xe0
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.001640]  [<c0167740>] ? autoremove_wake_function+0x0/0x50
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.001643] ADDRCONF(NETDEV_UP): wlan1: link is not ready
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.001649]  [<c0163760>] ? worker_thread+0x0/0xe0
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.001653]  [<c01674b4>] kthread+0x74/0x80
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.001657]  [<c0167440>] ? kthread+0x0/0x80
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.001663]  [<c0104087>] kernel_thread_helper+0x7/0x10
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.001666] ---[ end trace 619124d376e0cfcd ]---
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.003058] r8169: eth0: link down
Apr 16 15:09:48 MY_HOSTNAME kernel: [ 5670.003476] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 16 15:09:49 MY_HOSTNAME kernel: [ 5671.699086] ------------[ cut here ]------------

```




There are a few more but they're similar.
I memtested the memory during 7 or 8 hours. No errors.
Sherlock Holmes, Watsons, Hercule Poirots, 007, Linus Torvalds, bearded guys, unbearded guys, whoever has a clue about this, hints please?

BTW, phy0 is my iwl3945, I believe.

Who shall I annoy... ahem... humbly request for help? I'm afraid to go to LKML with such random information but honestly I don't know where to get help...

---

### Post by pedrogfrancisco on 2010-04-21
Two more, this time with mainline kernel 2.6.33-020633-generic.

```
[17294.870172] BUG: unable to handle kernel paging request at 283a2877
[17294.870185] IP: [<c020f526>] __d_lookup+0x66/0x110
[17294.870201] *pde = 00000000 
[17294.870207] Oops: 0000 [#1] SMP 
[17294.870214] last sysfs file: /sys/devices/virtual/backlight/acpi_video0/brightness
[17294.870221] Modules linked in: btrfs zlib_deflate crc32c libcrc32c ufs qnx4 hfsplus hfs minix ntfs vfat msdos fat jfs xfs exportfs reiserfs ppp_async crc_ccitt binfmt_misc ppdev
 ipt_REJECT ipt_LOG xt_limit xt_tcpudp ipt_addrtype xt_state snd_hda_codec_si3054 snd_hda_codec_realtek snd_hda_intel ip6table_filter snd_hda_codec ip6_tables snd_hwdep nf_nat_irc 
snd_pcm_oss snd_mixer_oss fbcon tileblit font bitblit snd_pcm nf_conntrack_irc softcursor nf_nat_ftp nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 snd_seq_dummy snd_seq_oss snd_seq_midi 
nf_conntrack_ftp snd_rawmidi snd_seq_midi_event joydev snd_seq nf_conntrack iptable_filter arc4 snd_timer i915 iwl3945 drm_kms_helper iwlcore ath5k drm snd_seq_device ip_tables mac
80211 i2c_algo_bit ath lp parport snd ricoh_mmc cp210x uvcvideo x_tables intel_agp psmouse video option agpgart videodev serio_raw v4l1_compat cfg80211 sdhci_pci sdhci led_class so
undcore snd_page_alloc usbserial output hp_wmi usb_storage usbhid ohci1394 r8169 mii ieee1394
[17294.870396] 
[17294.870403] Pid: 18502, comm: kismet_server Tainted: G   M       2.6.33-020633-generic #020633 30CC/HP Pavilion dv6500 Notebook PC    
[17294.870411] EIP: 0060:[<c020f526>] EFLAGS: 00210206 CPU: 0
[17294.870417] EIP is at __d_lookup+0x66/0x110
[17294.870423] EAX: 283a2877 EBX: 283a2877 ECX: 00000011 EDX: 03649a98
[17294.870428] ESI: ef549efc EDI: f677a01c EBP: ef549e04 ESP: ef549dd4
[17294.870434]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[17294.870440] Process kismet_server (pid: 18502, ti=ef548000 task=f15e1960 task.ti=ef548000)
[17294.870445] Stack:
[17294.870449]  ef549df8 c0244980 f737c2a0 ef549e64 ef075220 f737c2f8 00000004 019fd950
[17294.870464] <0> f677a018 019fd950 ef549efc f677a01c ef549e2c c0207801 ef549e70 ef549e64
[17294.870479] <0> ef549e1c f6931a00 ef549e2c 019fd950 019fd950 f677a01c ef549e84 c0208f48
[17294.870497] Call Trace:
[17294.870506]  [<c0244980>] ? proc_lookup_de+0xe0/0xf0
[17294.870514]  [<c0207801>] ? do_lookup+0x41/0x1b0
[17294.870522]  [<c0208f48>] ? link_path_walk+0x498/0xb80
[17294.870530]  [<c01fab63>] ? __mem_cgroup_uncharge_common+0xb3/0x160
[17294.870538]  [<c0209672>] ? path_walk+0x42/0x90
[17294.870546]  [<c02097d0>] ? do_path_lookup+0x50/0xa0
[17294.870553]  [<c0209900>] ? do_filp_open+0xe0/0x8a0
[17294.870563]  [<c0334217>] ? strncpy_from_user+0x37/0x60
[17294.870570]  [<c0213ca7>] ? alloc_fd+0xd7/0xf0
[17294.870577]  [<c02071c5>] ? do_getname+0x35/0x80
[17294.870585]  [<c01fc711>] ? do_sys_open+0x51/0x110
[17294.870592]  [<c01fc839>] ? sys_open+0x29/0x40
[17294.870599]  [<c0102d23>] ? sysenter_do_call+0x12/0x28
[17294.870604] Code: 01 00 37 9e d3 e8 31 d0 23 05 b4 1d 7e c0 c1 e0 02 03 05 bc 1d 7e c0 8b 00 85 c0 89 c3 75 0c eb 4d 8d 74 26 00 8b 1b 85 db 74 43 <8b> 03 0f 18 00 90 8d 53 ec 8
b 4d ec 89 55 d4 39 4a 20 75 e6 8b 
[17294.870695] EIP: [<c020f526>] __d_lookup+0x66/0x110 SS:ESP 0068:ef549dd4
[17294.870707] CR2: 00000000283a2877
[17294.870713] ---[ end trace 8855cc17e7e01f44 ]---
```


```
[37046.704167] BUG: unable to handle kernel paging request at 000102ac
[37046.704177] IP: [<c020f526>] __d_lookup+0x66/0x110
[37046.704189] *pde = 00000000 
[37046.704194] Oops: 0000 [#2] SMP 
[37046.704198] last sysfs file: /sys/devices/virtual/backlight/acpi_video0/brightness
[37046.704203] Modules linked in: btrfs zlib_deflate crc32c libcrc32c ufs qnx4 hfsplus hfs minix ntfs vfat msdos fat jfs xfs exportfs reiserfs ppp_async crc_ccitt binfmt_misc ppdev ipt_REJECT ipt_LOG xt_limit xt_tcpudp ipt_addrtype xt_state snd_hda_codec_si3054 snd_hda_codec_realtek snd_hda_intel ip6table_filter snd_hda_codec ip6_tables snd_hwdep nf_nat_irc snd_pcm_oss snd_mixer_oss fbcon tileblit font bitblit snd_pcm nf_conntrack_irc softcursor nf_nat_ftp nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 snd_seq_dummy snd_seq_oss snd_seq_midi nf_conntrack_ftp snd_rawmidi snd_seq_midi_event joydev snd_seq nf_conntrack iptable_filter arc4 snd_timer i915 iwl3945 drm_kms_helper iwlcore ath5k drm snd_seq_device ip_tables mac80211 i2c_algo_bit ath lp parport snd ricoh_mmc cp210x uvcvideo x_tables intel_agp psmouse video option agpgart videodev serio_raw v4l1_compat cfg80211 sdhci_pci sdhci led_class soundcore snd_page_alloc usbserial output hp_wmi usb_storage usbhid ohci1394 r8169 mii ieee1394
[37046.704325] 
[37046.704330] Pid: 30157, comm: chrome Tainted: G   M  D    2.6.33-020633-generic #020633 30CC/HP Pavilion dv6500 Notebook PC    
[37046.704335] EIP: 0060:[<c020f526>] EFLAGS: 00210206 CPU: 0
[37046.704340] EIP is at __d_lookup+0x66/0x110
[37046.704343] EAX: 000102ac EBX: 000102ac ECX: 00000011 EDX: 16fa9045
[37046.704347] ESI: 00000000 EDI: f6c77f68 EBP: c4763e90 ESP: c4763e60
[37046.704351]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[37046.704355] Process chrome (pid: 30157, ti=c4762000 task=ec7f8cb0 task.ti=c4762000)
[37046.704357] Stack:
[37046.704360]  00000010 00200246 ef742d00 c4763f04 f6c77f68 00000000 00000018 1556ce48
[37046.704370] <0> c41e9009 c4763efc 00000000 f6c77f68 c4763eb0 c02079b2 c4763efc c4763f04
[37046.704381] <0> f6b22948 c4763efc 00000000 f6c77f68 c4763ebc c0207b25 00000000 c4763f68
[37046.704392] Call Trace:
[37046.704399]  [<c02079b2>] ? __lookup_hash+0x42/0x110
[37046.704404]  [<c0207b25>] ? lookup_hash+0x25/0x30
[37046.704409]  [<c0209aa4>] ? do_filp_open+0x284/0x8a0
[37046.704415]  [<c01fe37e>] ? do_sync_write+0xae/0xf0
[37046.704422]  [<c0334217>] ? strncpy_from_user+0x37/0x60
[37046.704427]  [<c0213ca7>] ? alloc_fd+0xd7/0xf0
[37046.704431]  [<c02071c5>] ? do_getname+0x35/0x80
[37046.704436]  [<c01fc711>] ? do_sys_open+0x51/0x110
[37046.704441]  [<c01fc839>] ? sys_open+0x29/0x40
[37046.704446]  [<c0102d23>] ? sysenter_do_call+0x12/0x28
[37046.704452]  [<c0590000>] ? cpu_init+0x110/0x230
[37046.704455] Code: 01 00 37 9e d3 e8 31 d0 23 05 b4 1d 7e c0 c1 e0 02 03 05 bc 1d 7e c0 8b 00 85 c0 89 c3 75 0c eb 4d 8d 74 26 00 8b 1b 85 db 74 43 <8b> 03 0f 18 00 90 8d 53 ec 8b 4d ec 89 55 d4 39 4a 20 75 e6 8b 
[37046.704517] EIP: [<c020f526>] __d_lookup+0x66/0x110 SS:ESP 0068:c4763e60
[37046.704524] CR2: 00000000000102ac
[37046.704529] ---[ end trace 8855cc17e7e01f45 ]---

```

---

### Post by Claus7 on 2010-04-21
Hello,

first of its your thread, so of course you can keep notes on what you are trying in order to solve your problem. The more you deal with this the more you will come to the solution.

I'm not an expert on the problem you are facing, and by just googling a little I came out with the fact that is hardware-software related.

Since you have networking - memory issues, I would advice you to check things at a time.

Are you using chrome browser? This is what I got from some of your errors... Could you switch and test another and see?

It would be better if you could rid off the wireless at that time and check out what is going.

Also what is the type of computer you have? 32 bit or 64 bit? Have you installed the right version of ubuntu for your computer?

These are some thoughts, while bumping your thread. Might someone who have faced the same or similar problem can help you better.

Regards!
Hope you will solve your problem soon!

---

### Post by P4man on 2010-04-21
Did you install the backports module to make the ath5k work? Just asking because I just did in an attempt to get an atheros 5001X wifi card to work on lucid, and it would almost  instantly throw me a kernel panic after installing the backport module. Removing the module (or even the card) I have no problems, and the card is detected (it just doesnt work).

Not sure if that helps, but I thought Id post anyway.

---

### Post by pedrogfrancisco on 2010-04-21
Hi :)
No, I'm not using linux-backport-modules...

---

### Post by iponeverything on 2010-04-21
First try it without the two wireless cards and the gps -- go into the bios -- reset it to defaults and turn off serial, usb, parallel, ir and anything else you can find with exception of graphics.  

If, panics stop -- isolate the device in question.

If not, switch from using device specific xorg driver to using the generic and framebuffer. 

If they still persist, upgrade the bios on the machine. 

If they still persist.. check your E-karma for past slights against electrons -- make a list.

---

### Post by pedrogfrancisco on 2010-04-21
> **Claus7 said:**
> Hello,
-snip

Since you have networking - memory issues, I would advice you to check things at a time.

-snip

Regards!
Hope you will solve your problem soon!

Yes, you're right. Will do it. It's just it's frustrating such random errors and I thought maybe someone would know the "thing" to fix them.

My next test will be just wireless, no X.

---

### Post by dino99 on 2010-04-21
i've tried 2.6.33 on my end and never be able to use it like you, i've no problem with actual 2.6.32 generic-pae

---

### Post by pedrogfrancisco on 2010-04-22
It's ath5k. I restarted the system, closed X, opened kismet and a few hours later had the system spewing console messages like hell. Can't get any trace of it in a log though.

Trying linux-backports-modules-wireless-lucid-generic now.

---

### Post by pedrogfrancisco on 2010-04-23
I left kismet running for a long time and when I got back everything seemed fine.

I closed kismet and started X, only to have a lock-up. A few minutes later and using Magic Keys I rebooted. I was able to find out this in syslog.

```
Apr 23 07:36:21 MY_HOSTNAME kernel: [23263.693005] BUG: soft lockup - CPU#1 stuck for 61s! [kcminit_startup:2172]
Apr 23 07:36:21 MY_HOSTNAME kernel: [23263.693005] Modules linked in: binfmt_misc fbcon tileblit font bitblit softcursor arc4 ath5k ath mac80211 i915 cfg80211 drm_kms_helper intel_ag
p led_class drm agpgart i2c_algo_bit video output ahci [last unloaded: compat_firmware_class]
Apr 23 07:36:21 MY_HOSTNAME kernel: [23263.693005] 
Apr 23 07:36:21 MY_HOSTNAME kernel: [23263.693005] Pid: 2172, comm: kcminit_startup Not tainted (2.6.32-21-generic #32-Ubuntu) HP Pavilion dv6500 Notebook PC    
Apr 23 07:36:21 MY_HOSTNAME kernel: [23263.693005] EIP: 0060:[<c012a3b3>] EFLAGS: 00200202 CPU: 1
Apr 23 07:36:21 MY_HOSTNAME kernel: [23263.693005] EIP is at __ticket_spin_lock+0x13/0x20
Apr 23 07:36:21 MY_HOSTNAME kernel: [23263.693005] EAX: f20f507c EBX: f20f4e40 ECX: 0000000c EDX: 0000012a
Apr 23 07:36:21 MY_HOSTNAME kernel: [23263.693005] ESI: f20f4ec8 EDI: f2765f5c EBP: f2765ee4 ESP: f2765ee4
Apr 23 07:36:21 MY_HOSTNAME kernel: [23263.693005]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Apr 23 07:36:21 MY_HOSTNAME kernel: [23263.693005] CR0: 80050033 CR2: 077553e8 CR3: 308aa000 CR4: 000006d0
Apr 23 07:36:21 MY_HOSTNAME kernel: [23263.693005] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Apr 23 07:36:21 MY_HOSTNAME kernel: [23263.693005] DR6: ffff0ff0 DR7: 00000400
Apr 23 07:36:21 MY_HOSTNAME kernel: [23263.693005] Call Trace:
Apr 23 07:36:21 MY_HOSTNAME kernel: [23263.693005]  [<c058b6ad>] _spin_lock+0xd/0x10
Apr 23 07:36:21 MY_HOSTNAME kernel: [23263.693005]  [<c0287a38>] ext4_getattr+0x38/0x70
Apr 23 07:36:21 MY_HOSTNAME kernel: [23263.693005]  [<c020bec5>] vfs_getattr+0x45/0x70
Apr 23 07:36:21 MY_HOSTNAME kernel: [23263.693005]  [<c0287a00>] ? ext4_getattr+0x0/0x70
Apr 23 07:36:21 MY_HOSTNAME kernel: [23263.693005]  [<c020bf4d>] vfs_fstatat+0x5d/0x70
Apr 23 07:36:21 MY_HOSTNAME kernel: [23263.693005]  [<c020c080>] vfs_stat+0x20/0x30
Apr 23 07:36:21 MY_HOSTNAME kernel: [23263.693005]  [<c020c0a9>] sys_stat64+0x19/0x30
Apr 23 07:36:21 MY_HOSTNAME kernel: [23263.693005]  [<c01033ec>] syscall_call+0x7/0xb

```

Notice the small number of modules loaded in.
My theory is: something seriously wrong happens with ath5k and other parts of the kernel suffer with it. I thought modules were nowadays isolated from one another but honestly it doesn't seem so.

---

### Post by pedrogfrancisco on 2010-04-24
I'm currently on LKML asking for help :)

I booted the kernel with `slub_debug' on GRUB and having cool errors which I'll post below. I'm waiting from the guys on LKML to know if they're significant.

```
[ 2658.663308] =============================================================================
[ 2658.663424] BUG kmalloc-4096: Poison overwritten
[ 2658.663483] -----------------------------------------------------------------------------
[ 2658.663486] 
[ 2658.663606] INFO: 0xed3db0c0-0xed3db0cf. First byte 0xc4 instead of 0x6b
[ 2658.663698] INFO: Allocated in ath_rxbuf_alloc+0x30/0xa0 [ath] age=7117 cpu=0 pid=0
[ 2658.663799] INFO: Freed in skb_release_data+0x70/0xa0 age=0 cpu=0 pid=0
[ 2658.663882] INFO: Slab 0xc15fbb00 objects=7 used=5 fp=0xed3db090 flags=0x400040c3
[ 2658.663975] INFO: Object 0xed3db090 @offset=12432 fp=0xed3da060
[ 2658.663977] 
[ 2658.664069] Bytes b4 0xed3db080:  00 00 00 00 61 ff 08 00 5a 5a 5a 5a 5a 5a 5a 5a ....a&#65533;..ZZZZZZZZ
[ 2658.664258]   Object 0xed3db090:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.664443]   Object 0xed3db0a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.664629]   Object 0xed3db0b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.664816]   Object 0xed3db0c0:  c4 00 84 00 00 22 43 89 42 69 4e 12 ca 6f 6f 6f &#65533;...."C.BiN.&#65533;ooo
[ 2658.665004]   Object 0xed3db0d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.665191]   Object 0xed3db0e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.665377]   Object 0xed3db0f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.665564]   Object 0xed3db100:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.665751]   Object 0xed3db110:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.665937]   Object 0xed3db120:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.666124]   Object 0xed3db130:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.666311]   Object 0xed3db140:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.666498]   Object 0xed3db150:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.666685]   Object 0xed3db160:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.666871]   Object 0xed3db170:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667059]   Object 0xed3db180:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667246]   Object 0xed3db190:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db1a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db1b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db1c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db1d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db1e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db1f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db200:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db210:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db220:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db230:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db240:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db250:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db260:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db270:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db280:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db290:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db2a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db2b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db2c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db2d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db2e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db2f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db300:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db310:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db320:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db330:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db340:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db350:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db360:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db370:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db380:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db390:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db3a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db3b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db3c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db3d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db3e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db3f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db400:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db410:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db420:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db430:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db440:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db450:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db460:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db470:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db480:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db490:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db4a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db4b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db4c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db4d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db4e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db4f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db500:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db510:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db520:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db530:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db540:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db550:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db560:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db570:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db580:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db590:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db5a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db5b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db5c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db5d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db5e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db5f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db600:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db610:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db620:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db630:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db640:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db650:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db660:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db670:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db680:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db690:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db6a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db6b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db6c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db6d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db6e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db6f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db700:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db710:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db720:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db730:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db740:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db750:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db760:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db770:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db780:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db790:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db7a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db7b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db7c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db7d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db7e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db7f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db800:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db810:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db820:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db830:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db840:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db850:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db860:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db870:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db880:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db890:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db8a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db8b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db8c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db8d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db8e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db8f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db900:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db910:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db920:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db930:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db940:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db950:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db960:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db970:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db980:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db990:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db9a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db9b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db9c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db9d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db9e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3db9f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dba00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dba10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dba20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dba30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dba40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dba50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dba60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dba70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dba80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dba90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbaa0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbab0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbac0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbad0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbae0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbaf0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbb00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbb10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbb20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbb30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbb40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbb50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbb60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbb70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbb80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbb90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbba0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbbb0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbbc0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbbd0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbbe0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbbf0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbc00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbc10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbc20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbc30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbc40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbc50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbc60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbc70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbc80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbc90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbca0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbcb0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbcc0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbcd0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbce0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbcf0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbd00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbd10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbd20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbd30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbd40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbd50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbd60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbd70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbd80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbd90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbda0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbdb0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbdc0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbdd0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbde0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbdf0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbe00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbe10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbe20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbe30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbe40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbe50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbe60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbe70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbe80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbe90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbea0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbeb0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbec0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbed0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbee0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbef0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbf00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbf10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbf20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbf30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbf40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbf50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbf60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbf70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbf80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbf90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbfa0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbfb0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbfc0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbfd0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbfe0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dbff0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dc000:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dc010:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dc020:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dc030:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dc040:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dc050:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dc060:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dc070:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 2658.667258]   Object 0xed3dc080:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b a5 kkkkkkkkkkkkkkk&#65533;
[ 2658.667258]  Redzone 0xed3dc090:  bb bb bb bb                                     &#65533;&#65533;&#65533;&#65533;            
[ 2658.667258]  Padding 0xed3dc0b8:  5a 5a 5a 5a 5a 5a 5a 5a                         ZZZZZZZZ        
[ 2658.667258] Pid: 0, comm: swapper Not tainted 2.6.32-21-generic #32-Ubuntu
[ 2658.667258] Call Trace:
[ 2658.667258]  [<c01faf63>] print_trailer+0xd3/0x120
[ 2658.667258]  [<c01fb07c>] check_bytes_and_report+0xcc/0xf0
[ 2658.667258]  [<c01fc021>] check_object+0x1a1/0x1e0
[ 2658.667258]  [<c01fcc98>] alloc_debug_processing+0xc8/0x190
[ 2658.667258]  [<c01fcf2a>] __slab_alloc+0x1ca/0x220
[ 2658.667258]  [<f847e030>] ? ath_rxbuf_alloc+0x30/0xa0 [ath]
[ 2658.667258]  [<c01fdf5d>] __kmalloc_track_caller+0xcd/0x170
[ 2658.667258]  [<f847e030>] ? ath_rxbuf_alloc+0x30/0xa0 [ath]
[ 2658.667258]  [<f847e030>] ? ath_rxbuf_alloc+0x30/0xa0 [ath]
[ 2658.667258]  [<c04b9782>] __alloc_skb+0x52/0x130
[ 2658.667258]  [<f847e030>] ath_rxbuf_alloc+0x30/0xa0 [ath]
[ 2658.667258]  [<f8b38539>] ath5k_rx_skb_alloc+0x29/0x150 [ath5k]
[ 2658.667258]  [<c04c2087>] ? netif_receive_skb+0x387/0x570
[ 2658.667258]  [<f8b38ce3>] ath5k_tasklet_rx+0xe3/0x580 [ath5k]
[ 2658.667258]  [<f8b33cad>] ? ath5k_hw_calibration_poll+0x1d/0x80 [ath5k]
[ 2658.667258]  [<c0151a77>] tasklet_action+0xa7/0xb0
[ 2658.667258]  [<c0153068>] __do_softirq+0x98/0x1b0
[ 2658.667258]  [<c012293b>] ? ack_apic_level+0x6b/0x170
[ 2658.667258]  [<c016d7de>] ? sched_clock_tick+0x5e/0xa0
[ 2658.667258]  [<c01531c5>] do_softirq+0x45/0x50
[ 2658.667258]  [<c0153315>] irq_exit+0x65/0x70
[ 2658.667258]  [<c058fa25>] do_IRQ+0x55/0xc0
[ 2658.667258]  [<c016d4f5>] ? sched_clock_local+0xa5/0x180
[ 2658.667258]  [<c0103a30>] common_interrupt+0x30/0x40
[ 2658.667258]  [<c016007b>] ? sys_setrlimit+0xcb/0x120
[ 2658.667258]  [<c039ccad>] ? acpi_idle_enter_bm+0x26b/0x29a
[ 2658.667258]  [<c04a076a>] cpuidle_idle_call+0x7a/0x100
[ 2658.667258]  [<c01021d4>] cpu_idle+0x94/0xd0
[ 2658.667258]  [<c0579168>] rest_init+0x58/0x60
[ 2658.667258]  [<c07a38ec>] start_kernel+0x351/0x357
[ 2658.667258]  [<c07a33c7>] ? unknown_bootoption+0x0/0x19e
[ 2658.667258]  [<c07a30aa>] i386_start_kernel+0xaa/0xb1
[ 2658.667258] FIX kmalloc-4096: Restoring 0xed3db0c0-0xed3db0cf=0x6b
[ 2658.667258] 
[ 2658.667258] FIX kmalloc-4096: Marking all objects used
[ 4689.941595] =============================================================================
[ 4689.942368] BUG kmalloc-4096: Poison overwritten
[ 4689.943165] -----------------------------------------------------------------------------
[ 4689.943167] 
[ 4689.944962] INFO: 0xed3d9080-0xed3d908f. First byte 0xc4 instead of 0x6b
[ 4689.945547] INFO: Allocated in ath_rxbuf_alloc+0x30/0xa0 [ath] age=8 cpu=0 pid=0
[ 4689.945547] INFO: Freed in skb_release_data+0x70/0xa0 age=0 cpu=0 pid=0
[ 4689.945547] INFO: Slab 0xc15fbb00 objects=7 used=6 fp=0xed3d9030 flags=0x400040c3
[ 4689.945547] INFO: Object 0xed3d9030 @offset=4144 fp=0x(null)
[ 4689.945547] 
[ 4689.945547] Bytes b4 0xed3d9020:  00 00 00 00 0d bf 10 00 5a 5a 5a 5a 5a 5a 5a 5a .....&#65533;..ZZZZZZZZ
[ 4689.945547]   Object 0xed3d9030:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9040:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9050:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9060:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9070:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9080:  c4 00 70 00 00 22 43 89 42 69 fe 08 eb 14 14 14 &#65533;.p.."C.Bi&#65533;.&#65533;...
[ 4689.945547]   Object 0xed3d9090:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d90a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d90b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d90c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d90d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d90e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d90f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9100:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9110:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9120:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9130:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9140:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9150:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9160:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9170:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9180:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9190:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d91a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d91b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d91c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d91d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d91e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d91f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9200:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9210:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9220:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9230:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9240:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9250:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9260:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9270:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9280:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9290:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d92a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d92b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d92c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d92d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d92e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d92f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9300:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9310:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9320:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9330:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9340:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9350:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9360:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9370:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9380:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9390:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d93a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d93b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d93c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d93d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d93e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d93f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9400:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9410:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9420:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9430:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9440:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9450:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9460:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9470:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9480:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9490:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d94a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d94b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d94c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d94d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d94e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d94f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9500:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9510:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9520:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9530:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9540:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9550:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9560:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9570:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9580:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9590:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d95a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d95b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d95c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d95d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d95e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d95f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9600:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9610:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9620:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9630:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9640:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9650:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9660:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9670:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9680:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9690:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d96a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d96b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d96c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d96d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d96e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d96f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9700:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9710:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9720:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9730:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9740:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9750:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9760:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9770:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9780:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9790:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d97a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d97b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d97c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d97d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d97e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d97f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9800:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9810:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9820:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9830:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9840:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9850:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9860:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9870:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9880:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9890:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d98a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d98b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d98c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d98d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d98e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d98f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9900:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9910:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9920:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9930:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9940:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9950:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9960:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9970:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9980:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9990:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d99a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d99b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d99c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d99d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d99e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d99f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9a00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9a10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9a20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9a30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9a40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9a50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9a60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9a70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9a80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9a90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9aa0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9ab0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9ac0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9ad0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9ae0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9af0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9b00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9b10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9b20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9b30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9b40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9b50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9b60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9b70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9b80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9b90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9ba0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9bb0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9bc0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9bd0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9be0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9bf0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9c00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9c10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9c20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9c30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9c40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9c50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9c60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9c70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9c80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9c90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9ca0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9cb0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9cc0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9cd0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9ce0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9cf0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9d00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9d10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9d20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9d30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9d40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9d50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9d60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9d70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9d80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9d90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9da0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9db0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9dc0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9dd0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9de0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9df0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9e00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9e10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9e20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9e30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9e40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9e50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9e60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9e70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9e80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9e90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9ea0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9eb0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9ec0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9ed0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9ee0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9ef0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9f00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9f10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9f20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9f30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9f40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9f50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9f60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9f70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9f80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9f90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9fa0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9fb0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9fc0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9fd0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9fe0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3d9ff0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3da000:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3da010:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[ 4689.945547]   Object 0xed3da020:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b a5 kkkkkkkkkkkkkkk&#65533;
[ 4689.945547]  Redzone 0xed3da030:  bb bb bb bb                                     &#65533;&#65533;&#65533;&#65533;            
[ 4689.945547]  Padding 0xed3da058:  5a 5a 5a 5a 5a 5a 5a 5a                         ZZZZZZZZ        
[ 4689.945547] Pid: 0, comm: swapper Not tainted 2.6.32-21-generic #32-Ubuntu
[ 4689.945547] Call Trace:
[ 4689.945547]  [<c01faf63>] print_trailer+0xd3/0x120
[ 4689.945547]  [<c01fb07c>] check_bytes_and_report+0xcc/0xf0
[ 4689.945547]  [<c01fc021>] check_object+0x1a1/0x1e0
[ 4689.945547]  [<c01fcc98>] alloc_debug_processing+0xc8/0x190
[ 4689.945547]  [<c01fcf2a>] __slab_alloc+0x1ca/0x220
[ 4689.945547]  [<f847e030>] ? ath_rxbuf_alloc+0x30/0xa0 [ath]
[ 4689.945547]  [<c01fdf5d>] __kmalloc_track_caller+0xcd/0x170
[ 4689.945547]  [<f847e030>] ? ath_rxbuf_alloc+0x30/0xa0 [ath]
[ 4689.945547]  [<f847e030>] ? ath_rxbuf_alloc+0x30/0xa0 [ath]
[ 4689.945547]  [<c04b9782>] __alloc_skb+0x52/0x130
[ 4689.945547]  [<f847e030>] ath_rxbuf_alloc+0x30/0xa0 [ath]
[ 4689.945547]  [<f8b38539>] ath5k_rx_skb_alloc+0x29/0x150 [ath5k]
[ 4689.945547]  [<c016ab98>] ? enqueue_hrtimer+0x78/0xb0
[ 4689.945547]  [<f8b38ce3>] ath5k_tasklet_rx+0xe3/0x580 [ath5k]
[ 4689.945547]  [<f8b33cad>] ? ath5k_hw_calibration_poll+0x1d/0x80 [ath5k]
[ 4689.945547]  [<c0151a77>] tasklet_action+0xa7/0xb0
[ 4689.945547]  [<c0153068>] __do_softirq+0x98/0x1b0
[ 4689.945547]  [<c012293b>] ? ack_apic_level+0x6b/0x170
[ 4689.945547]  [<c016d7de>] ? sched_clock_tick+0x5e/0xa0
[ 4689.945547]  [<c01531c5>] do_softirq+0x45/0x50
[ 4689.945547]  [<c0153315>] irq_exit+0x65/0x70
[ 4689.945547]  [<c058fa25>] do_IRQ+0x55/0xc0
[ 4689.945547]  [<c016d4f5>] ? sched_clock_local+0xa5/0x180
[ 4689.945547]  [<c0103a30>] common_interrupt+0x30/0x40
[ 4689.945547]  [<c016007b>] ? sys_setrlimit+0xcb/0x120
[ 4689.945547]  [<c039ccad>] ? acpi_idle_enter_bm+0x26b/0x29a
[ 4689.945547]  [<c04a076a>] cpuidle_idle_call+0x7a/0x100
[ 4689.945547]  [<c01021d4>] cpu_idle+0x94/0xd0
[ 4689.945547]  [<c0579168>] rest_init+0x58/0x60
[ 4689.945547]  [<c07a38ec>] start_kernel+0x351/0x357
[ 4689.945547]  [<c07a33c7>] ? unknown_bootoption+0x0/0x19e
[ 4689.945547]  [<c07a30aa>] i386_start_kernel+0xaa/0xb1
[ 4689.945547] FIX kmalloc-4096: Restoring 0xed3d9080-0xed3d908f=0x6b
[ 4689.945547] 
[ 4689.945547] FIX kmalloc-4096: Marking all objects used
[14487.161759] =============================================================================
[14487.162531] BUG kmalloc-4096: Poison overwritten
[14487.163319] -----------------------------------------------------------------------------
[14487.163322] 
[14487.165136] INFO: 0xed378040-0xed378087. First byte 0x80 instead of 0x6b
[14487.165341] INFO: Allocated in ath_rxbuf_alloc+0x30/0xa0 [ath] age=12696 cpu=0 pid=0
[14487.165341] INFO: Freed in skb_release_data+0x70/0xa0 age=1704 cpu=0 pid=806
[14487.165341] INFO: Slab 0xc15faf00 objects=7 used=6 fp=0xed378000 flags=0x400040c3
[14487.165341] INFO: Object 0xed378000 @offset=0 fp=0x(null)
[14487.165341] 
[14487.165341]   Object 0xed378000:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378010:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378020:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378030:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378040:  80 00 00 00 ff ff ff ff ff ff 00 1e 8c 0f 3e af ....&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;....>&#65533;
[14487.165341]   Object 0xed378050:  00 1e 8c 0f 3e af 90 36 85 b1 08 af 0b 00 00 00 ....>&#65533;.6.&#65533;.&#65533;....
[14487.165341]   Object 0xed378060:  64 00 11 00 00 04 43 41 53 41 01 04 82 84 8b 96 d.....CASA......
[14487.165341]   Object 0xed378070:  03 01 09 05 04 00 01 00 00 dd 09 00 10 18 02 00 .........&#65533;......
[14487.165341]   Object 0xed378080:  f0 00 00 00 b2 c4 d1 e4 6b 6b 6b 6b 6b 6b 6b 6b &#65533;...&#65533;&#65533;&#65533;&#65533;kkkkkkkk
[14487.165341]   Object 0xed378090:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3780a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3780b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3780c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3780d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3780e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3780f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378100:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378110:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378120:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378130:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378140:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378150:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378160:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378170:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378180:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378190:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3781a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3781b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3781c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3781d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3781e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3781f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378200:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378210:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378220:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378230:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378240:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378250:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378260:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378270:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378280:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378290:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3782a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3782b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3782c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3782d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3782e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3782f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378300:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378310:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378320:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378330:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378340:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378350:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378360:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378370:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378380:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378390:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3783a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3783b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3783c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3783d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3783e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3783f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378400:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378410:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378420:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378430:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378440:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378450:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378460:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378470:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378480:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378490:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3784a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3784b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3784c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3784d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3784e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3784f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378500:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378510:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378520:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378530:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378540:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378550:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378560:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378570:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378580:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378590:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3785a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3785b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3785c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3785d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3785e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3785f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378600:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378610:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378620:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378630:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378640:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378650:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378660:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378670:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378680:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378690:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3786a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3786b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3786c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3786d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3786e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3786f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378700:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378710:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378720:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378730:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378740:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378750:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378760:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378770:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378780:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378790:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3787a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3787b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3787c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3787d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3787e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3787f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378800:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378810:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378820:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378830:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378840:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378850:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378860:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378870:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378880:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378890:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3788a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3788b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3788c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3788d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3788e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3788f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378900:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378910:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378920:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378930:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378940:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378950:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378960:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378970:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378980:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378990:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3789a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3789b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3789c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3789d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3789e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed3789f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378a00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378a10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378a20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378a30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378a40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378a50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378a60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378a70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378a80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378a90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378aa0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378ab0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378ac0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378ad0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378ae0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378af0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378b00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378b10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378b20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378b30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378b40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378b50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378b60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378b70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378b80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378b90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378ba0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378bb0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378bc0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378bd0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378be0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378bf0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378c00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378c10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378c20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378c30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378c40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378c50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378c60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378c70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378c80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378c90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378ca0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378cb0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378cc0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378cd0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378ce0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378cf0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378d00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378d10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378d20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378d30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378d40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378d50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378d60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378d70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378d80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378d90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378da0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378db0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378dc0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378dd0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378de0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378df0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378e00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378e10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378e20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378e30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378e40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378e50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378e60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378e70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378e80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378e90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378ea0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378eb0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378ec0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378ed0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378ee0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378ef0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378f00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378f10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378f20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378f30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378f40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378f50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378f60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378f70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378f80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378f90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378fa0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378fb0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378fc0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378fd0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378fe0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[14487.165341]   Object 0xed378ff0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b a5 kkkkkkkkkkkkkkk&#65533;
[14487.165341]  Redzone 0xed379000:  bb bb bb bb                                     &#65533;&#65533;&#65533;&#65533;            
[14487.165341]  Padding 0xed379028:  5a 5a 5a 5a 5a 5a 5a 5a                         ZZZZZZZZ        
[14487.165341] Pid: 2011, comm: kismet_server Not tainted 2.6.32-21-generic #32-Ubuntu
[14487.165341] Call Trace:
[14487.165341]  [<c01faf63>] print_trailer+0xd3/0x120
[14487.165341]  [<c01fb07c>] check_bytes_and_report+0xcc/0xf0
[14487.165341]  [<c01fc021>] check_object+0x1a1/0x1e0
[14487.165341]  [<c01fcc98>] alloc_debug_processing+0xc8/0x190
[14487.165341]  [<c01fcf2a>] __slab_alloc+0x1ca/0x220
[14487.165341]  [<c0222f7e>] ? seq_read+0x27e/0x3a0
[14487.165341]  [<c01fd038>] kmem_cache_alloc+0xb8/0x120
[14487.165341]  [<c0222f7e>] ? seq_read+0x27e/0x3a0
[14487.165341]  [<c0222f7e>] ? seq_read+0x27e/0x3a0
[14487.165341]  [<c0222d00>] ? seq_read+0x0/0x3a0
[14487.165341]  [<c0222f7e>] seq_read+0x27e/0x3a0
[14487.165341]  [<c01ea4fb>] ? mmap_region+0x1fb/0x480
[14487.165341]  [<c0222d00>] ? seq_read+0x0/0x3a0
[14487.165341]  [<c024c497>] proc_reg_read+0x67/0xa0
[14487.165341]  [<c02083cf>] vfs_read+0x9f/0x1a0
[14487.165341]  [<c024c430>] ? proc_reg_read+0x0/0xa0
[14487.165341]  [<c0208582>] sys_read+0x42/0x70
[14487.165341]  [<c01033ec>] syscall_call+0x7/0xb
[14487.165341] FIX kmalloc-4096: Restoring 0xed378040-0xed378087=0x6b
[14487.165341] 
[14487.165341] FIX kmalloc-4096: Marking all objects used
[24370.458652] =============================================================================
[24370.459425] BUG kmalloc-4096: Poison overwritten
[24370.460011] -----------------------------------------------------------------------------
[24370.460011] 
[24370.460011] INFO: 0xed3dc100-0xed3dc147. First byte 0x80 instead of 0x6b
[24370.460011] INFO: Allocated in ath_rxbuf_alloc+0x30/0xa0 [ath] age=13242 cpu=0 pid=0
[24370.460011] INFO: Freed in skb_release_data+0x70/0xa0 age=2328 cpu=1 pid=806
[24370.460011] INFO: Slab 0xc15fbb00 objects=7 used=6 fp=0xed3dc0c0 flags=0x400040c3
[24370.460011] INFO: Object 0xed3dc0c0 @offset=16576 fp=0x(null)
[24370.460011] 
[24370.460011] Bytes b4 0xed3dc0b0:  00 00 00 00 61 ff 08 00 5a 5a 5a 5a 5a 5a 5a 5a ....a&#65533;..ZZZZZZZZ
[24370.460011]   Object 0xed3dc0c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc0d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc0e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc0f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc100:  80 00 00 00 ff ff ff ff ff ff 00 1e 8c 0f 3e af ....&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;....>&#65533;
[24370.460011]   Object 0xed3dc110:  00 1e 8c 0f 3e af 20 55 8b 31 f3 fb 0d 00 00 00 ....>&#65533;.U.1&#65533;&#65533;....
[24370.460011]   Object 0xed3dc120:  64 00 11 00 00 04 43 41 53 41 01 04 82 84 8b 96 d.....CASA......
[24370.460011]   Object 0xed3dc130:  03 01 09 05 04 00 01 00 00 dd 09 00 10 18 02 00 .........&#65533;......
[24370.460011]   Object 0xed3dc140:  f0 00 00 00 43 0e a0 28 6b 6b 6b 6b 6b 6b 6b 6b &#65533;...C..(kkkkkkkk
[24370.460011]   Object 0xed3dc150:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc160:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc170:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc180:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc190:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc1a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc1b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc1c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc1d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc1e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc1f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc200:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc210:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc220:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc230:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc240:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc250:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc260:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc270:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc280:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc290:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc2a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc2b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc2c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc2d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc2e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc2f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc300:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc310:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc320:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc330:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc340:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc350:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc360:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc370:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc380:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc390:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc3a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc3b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc3c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc3d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc3e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc3f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc400:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc410:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc420:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc430:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc440:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc450:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc460:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc470:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc480:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc490:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc4a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc4b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc4c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc4d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc4e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc4f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc500:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc510:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc520:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc530:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc540:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc550:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc560:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc570:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc580:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc590:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc5a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc5b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc5c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc5d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc5e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc5f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc600:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc610:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc620:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc630:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc640:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc650:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc660:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc670:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc680:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc690:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc6a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc6b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc6c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc6d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc6e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc6f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc700:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc710:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc720:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc730:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc740:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc750:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc760:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc770:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc780:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc790:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc7a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc7b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc7c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc7d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc7e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc7f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc800:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc810:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc820:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc830:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc840:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc850:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc860:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc870:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc880:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc890:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc8a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc8b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc8c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc8d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc8e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc8f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc900:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc910:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc920:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc930:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc940:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc950:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc960:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc970:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc980:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc990:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc9a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc9b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc9c0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc9d0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc9e0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dc9f0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dca00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dca10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dca20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dca30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dca40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dca50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dca60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dca70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dca80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dca90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcaa0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcab0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcac0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcad0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcae0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcaf0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcb00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcb10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcb20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcb30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcb40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcb50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcb60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcb70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcb80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcb90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcba0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcbb0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcbc0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcbd0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcbe0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcbf0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcc00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcc10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcc20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcc30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcc40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcc50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcc60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcc70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcc80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcc90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcca0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dccb0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dccc0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dccd0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcce0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dccf0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcd00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcd10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcd20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcd30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcd40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcd50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcd60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcd70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcd80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcd90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcda0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcdb0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcdc0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcdd0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcde0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcdf0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dce00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dce10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dce20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dce30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dce40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dce50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dce60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dce70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dce80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dce90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcea0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dceb0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcec0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dced0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcee0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcef0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcf00:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcf10:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcf20:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcf30:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcf40:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcf50:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcf60:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcf70:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcf80:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcf90:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcfa0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcfb0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcfc0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcfd0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcfe0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dcff0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dd000:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dd010:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dd020:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dd030:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dd040:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dd050:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dd060:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dd070:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dd080:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dd090:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dd0a0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b kkkkkkkkkkkkkkkk
[24370.460011]   Object 0xed3dd0b0:  6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b 6b a5 kkkkkkkkkkkkkkk&#65533;
[24370.460011]  Redzone 0xed3dd0c0:  bb bb bb bb                                     &#65533;&#65533;&#65533;&#65533;            
[24370.460011]  Padding 0xed3dd0e8:  5a 5a 5a 5a 5a 5a 5a 5a                         ZZZZZZZZ        
[24370.460011] Pid: 2011, comm: kismet_server Not tainted 2.6.32-21-generic #32-Ubuntu
[24370.460011] Call Trace:
[24370.460011]  [<c01faf63>] print_trailer+0xd3/0x120
[24370.460011]  [<c01fb07c>] check_bytes_and_report+0xcc/0xf0
[24370.460011]  [<c01fc021>] check_object+0x1a1/0x1e0
[24370.460011]  [<c01fcc98>] alloc_debug_processing+0xc8/0x190
[24370.460011]  [<c01fcf2a>] __slab_alloc+0x1ca/0x220
[24370.460011]  [<c0222f7e>] ? seq_read+0x27e/0x3a0
[24370.460011]  [<c01fd038>] kmem_cache_alloc+0xb8/0x120
[24370.460011]  [<c0222f7e>] ? seq_read+0x27e/0x3a0
[24370.460011]  [<c0222f7e>] ? seq_read+0x27e/0x3a0
[24370.460011]  [<c0222d00>] ? seq_read+0x0/0x3a0
[24370.460011]  [<c0222f7e>] seq_read+0x27e/0x3a0
[24370.460011]  [<c01ea4fb>] ? mmap_region+0x1fb/0x480
[24370.460011]  [<c0222d00>] ? seq_read+0x0/0x3a0
[24370.460011]  [<c024c497>] proc_reg_read+0x67/0xa0
[24370.460011]  [<c02083cf>] vfs_read+0x9f/0x1a0
[24370.460011]  [<c024c430>] ? proc_reg_read+0x0/0xa0
[24370.460011]  [<c0208582>] sys_read+0x42/0x70
[24370.460011]  [<c01033ec>] syscall_call+0x7/0xb
[24370.460011] FIX kmalloc-4096: Restoring 0xed3dc100-0xed3dc147=0x6b
[24370.460011] 
[24370.460011] FIX kmalloc-4096: Marking all objects used
```

---

