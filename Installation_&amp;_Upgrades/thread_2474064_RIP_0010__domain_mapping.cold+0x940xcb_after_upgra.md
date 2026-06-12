---
title: "RIP: 0010:__domain_mapping.cold+0x94/0xcb after upgrading to 22.04"
date: 2022-04-21
forum: Installation &amp; Upgrades
---

### Post by jimtim1169 on 2022-04-21
Hi Folks,

I recently upgraded my server to 22.04 and noticed  following in logs

```

[   17.488272] DMAR: ERROR: DMA PTE for vPFN 0xf1f80 already set (to f1f80003 not 12bea5803)
[   17.489005] ------------[ cut here ]------------
[   17.489007] WARNING: CPU: 1 PID: 1882 at drivers/iommu/intel/iommu.c:2391 __domain_mapping.cold+0x94/0xcb
[   17.489015] Modules linked in: overlay bridge stp llc ipmi_ssif zfs(PO) intel_rapl_msr zunicode(PO) zzstd(O) zlua(O) zavl(PO) icp(PO) intel_rapl_common zcommon(PO) x86_pkg_temp_thermal intel_powerclamp znvpair(PO) coretemp spl(O) kvm_intel kvm rapl intel_cstate serio_raw acpi_ipmi hpilo ipmi_si ie31200_edac mac_hid acpi_power_meter sch_fq_codel dm_multipath scsi_dh_rdac scsi_dh_emc scsi_dh_alua ipmi_devintf ipmi_msghandler msr ip_tables x_tables autofs4 btrfs blake2b_generic zstd_compress raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq libcrc32c raid1 raid0 multipath linear mgag200 i2c_algo_bit drm_kms_helper syscopyarea crct10dif_pclmul sysfillrect crc32_pclmul sysimgblt ghash_clmulni_intel fb_sys_fops cec xhci_pci gpio_ich aesni_intel rc_core crypto_simd ahci lpc_ich cryptd drm psmouse xhci_pci_renesas libahci tg3
[   17.489094] CPU: 1 PID: 1882 Comm: snmpd Tainted: P          IO      5.15.0-25-generic #25-Ubuntu
[   17.489097] Hardware name: HP ProLiant MicroServer Gen8, BIOS J06 04/04/2019
[   17.489098] RIP: 0010:__domain_mapping.cold+0x94/0xcb
[   17.489103] Code: 07 99 4c 89 4d b8 4c 89 45 c0 e8 03 c5 fa ff 8b 05 c3 e7 40 01 4c 8b 45 c0 4c 8b 4d b8 85 c0 74 09 83 e8 01 89 05 ae e7 40 01 <0f> 0b e9 0a b2 b1 ff 89 ca 48 83 ce ff 48 c7 c7 40 e8 b0 99 89 4d
[   17.489105] RSP: 0000:ffffb92543deb4b8 EFLAGS: 00010002
[   17.489108] RAX: 0000000000000004 RBX: ffff914e84f99c00 RCX: 0000000000000000
[   17.489109] RDX: 0000000000000000 RSI: ffff91517aa60980 RDI: ffff91517aa60980
[   17.489111] RBP: ffffb92543deb508 R08: 000000012bea5803 R09: 000000000012bea5
[   17.489113] R10: 00000000ffffffff R11: ffffffffc03c30e0 R12: 0000000000000002
[   17.489115] R13: 00000000000f1f80 R14: ffff914e8515d800 R15: ffff914e84f99c00
[   17.489117] FS:  00007f2ca2fda780(0000) GS:ffff91517aa40000(0000) knlGS:0000000000000000
[   17.489120] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[   17.489122] CR2: 00007f2ca3eb5104 CR3: 00000001020e8002 CR4: 00000000001706e0
[   17.489124] Call Trace:
[   17.489126]  <TASK>
[   17.489129]  intel_iommu_map_pages+0xdc/0x120
[   17.489135]  ? __alloc_and_insert_iova_range+0x203/0x240
[   17.489139]  __iommu_map+0xda/0x270
[   17.489143]  __iommu_map_sg+0x8e/0x120
[   17.489146]  iommu_map_sg_atomic+0x14/0x20
[   17.489150]  iommu_dma_map_sg+0x345/0x4d0
[   17.489153]  __dma_map_sg_attrs+0x68/0x70
[   17.489156]  dma_map_sg_attrs+0xe/0x20
[   17.489158]  ata_qc_issue+0x173/0x240
[   17.489162]  ata_scsi_translate+0xc0/0x1b0
[   17.489165]  __ata_scsi_queuecmd+0x87/0x250
[   17.489169]  ata_scsi_queuecmd+0x5d/0xa0
[   17.489172]  scsi_dispatch_cmd+0x93/0x1f0
[   17.489175]  scsi_queue_rq+0x2d1/0x690
[   17.489178]  blk_mq_dispatch_rq_list+0x126/0x600
[   17.489183]  ? sbitmap_get+0xa1/0xd0
[   17.489187]  __blk_mq_do_dispatch_sched+0xba/0x2d0
[   17.489191]  ? mempool_alloc_slab+0x17/0x20
[   17.489196]  __blk_mq_sched_dispatch_requests+0x104/0x150
[   17.489199]  blk_mq_sched_dispatch_requests+0x35/0x60
[   17.489203]  __blk_mq_run_hw_queue+0x34/0xb0
[   17.489206]  __blk_mq_delay_run_hw_queue+0x162/0x170
[   17.489209]  blk_mq_run_hw_queue+0x83/0x120
[   17.489212]  blk_mq_sched_insert_requests+0x69/0xf0
[   17.489216]  blk_mq_flush_plug_list+0x103/0x1c0
[   17.489220]  blk_flush_plug_list+0xdd/0x100
[   17.489224]  blk_finish_plug+0x29/0x40
[   17.489227]  read_pages+0x119/0x270
[   17.489231]  ? add_to_page_cache_lru+0x78/0xd0
[   17.489233]  page_cache_ra_unbounded+0x15d/0x210
[   17.489238]  ondemand_readahead+0x172/0x350
[   17.489241]  page_cache_async_ra+0xa2/0xd0
[   17.489245]  filemap_fault+0x315/0xab0
[   17.489248]  __do_fault+0x3c/0xe0
[   17.489252]  do_read_fault+0xeb/0x160
[   17.489255]  do_fault+0xa0/0x2e0
[   17.489258]  handle_pte_fault+0x1c5/0x230
[   17.489261]  __handle_mm_fault+0x3c7/0x700
[   17.489264]  handle_mm_fault+0xd8/0x2c0
[   17.489267]  do_user_addr_fault+0x1c5/0x670
[   17.489272]  exc_page_fault+0x77/0x160
[   17.489275]  ? asm_exc_page_fault+0x8/0x30
[   17.489279]  asm_exc_page_fault+0x1e/0x30
[   17.489282] RIP: 0033:0x7f2ca41d0424
[   17.489285] Code: 83 fe 25 0f 84 bd 06 00 00 4c 89 6d 88 49 83 fc 08 0f 84 d7 06 00 00 49 83 fc 26 0f 84 cd 06 00 00 4d 85 e4 0f 84 34 01 00 00 <41> 0f b6 45 04 89 c6 40 c0 ee 04 0f 84 7b 05 00 00 41 0f b6 55 05
[   17.489287] RSP: 002b:00007fffbd9094f0 EFLAGS: 00010206
[   17.489289] RAX: 00007f2ca2ff39e0 RBX: 00007f2ca3ed55d0 RCX: 00007f2ca3eb4908
[   17.489291] RDX: 0000000000000003 RSI: 00007f2ca3ec2900 RDI: 00007f2ca400fb30
[   17.489293] RBP: 00007fffbd9095f0 R08: 00007f2ca3ec2900 R09: 00007f2ca4013260
[   17.489295] R10: 00007f2ca2ff39f8 R11: 00007f2ca41bd690 R12: 0000000000000006
[   17.489296] R13: 00007f2ca3eb5100 R14: 0000005500000006 R15: 00007f2ca41bd690
[   17.489300]  </TASK>
[   17.489301] ---[ end trace f0bbbb5d8ec2c064 ]---

```

```

# dmesg | grep Tainted
[   17.489094] CPU: 1 PID: 1882 Comm: snmpd Tainted: P          IO      5.15.0-25-generic #25-Ubuntu
[   17.490156] CPU: 1 PID: 1882 Comm: snmpd Tainted: P        W IO      5.15.0-25-generic #25-Ubuntu
[   17.491196] CPU: 1 PID: 1882 Comm: snmpd Tainted: P        W IO      5.15.0-25-generic #25-Ubuntu
[   17.492215] CPU: 1 PID: 1882 Comm: snmpd Tainted: P        W IO      5.15.0-25-generic #25-Ubuntu
[   17.493222] CPU: 1 PID: 1882 Comm: snmpd Tainted: P        W IO      5.15.0-25-generic #25-Ubuntu
[   17.494221] CPU: 1 PID: 1882 Comm: snmpd Tainted: P        W IO      5.15.0-25-generic #25-Ubuntu
[   17.495209] CPU: 1 PID: 1882 Comm: snmpd Tainted: P        W IO      5.15.0-25-generic #25-Ubuntu
[   17.496185] CPU: 1 PID: 1882 Comm: snmpd Tainted: P        W IO      5.15.0-25-generic #25-Ubuntu
[   17.497140] CPU: 1 PID: 1882 Comm: snmpd Tainted: P        W IO      5.15.0-25-generic #25-Ubuntu
[   17.498145] CPU: 1 PID: 1882 Comm: snmpd Tainted: P        W IO      5.15.0-25-generic #25-Ubuntu
[   17.499074] CPU: 1 PID: 1882 Comm: snmpd Tainted: P        W IO      5.15.0-25-generic #25-Ubuntu
[   17.500012] CPU: 1 PID: 1882 Comm: snmpd Tainted: P        W IO      5.15.0-25-generic #25-Ubuntu
[   17.500930] CPU: 1 PID: 1882 Comm: snmpd Tainted: P        W IO      5.15.0-25-generic #25-Ubuntu
[   17.501841] CPU: 1 PID: 1882 Comm: snmpd Tainted: P        W IO      5.15.0-25-generic #25-Ubuntu
[   17.502739] CPU: 1 PID: 1882 Comm: snmpd Tainted: P        W IO      5.15.0-25-generic #25-Ubuntu
[   17.503626] CPU: 1 PID: 1882 Comm: snmpd Tainted: P        W IO      5.15.0-25-generic #25-Ubuntu
[   17.504510] CPU: 1 PID: 1882 Comm: snmpd Tainted: P        W IO      5.15.0-25-generic #25-Ubuntu
[   17.505366] CPU: 1 PID: 1882 Comm: snmpd Tainted: P        W IO      5.15.0-25-generic #25-Ubuntu
[   17.506223] CPU: 1 PID: 1882 Comm: snmpd Tainted: P        W IO      5.15.0-25-generic #25-Ubuntu
[   17.507074] CPU: 1 PID: 1882 Comm: snmpd Tainted: P        W IO      5.15.0-25-generic #25-Ubuntu
[   17.507923] CPU: 6 PID: 1765 Comm: prometheus-node Tainted: P        W IO      5.15.0-25-generic #25-Ubuntu
[   17.508775] CPU: 6 PID: 1765 Comm: prometheus-node Tainted: P        W IO      5.15.0-25-generic #25-Ubuntu
[   17.518890] CPU: 3 PID: 1890 Comm: containerd Tainted: P        W IO      5.15.0-25-generic #25-Ubuntu

```

```

# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04 LTS
Release:    22.04
Codename:    jammy

```

Any ideas what could be causing this ?

---

