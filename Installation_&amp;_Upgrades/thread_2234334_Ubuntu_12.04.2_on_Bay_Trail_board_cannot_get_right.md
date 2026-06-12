---
title: "Ubuntu 12.04.2 on Bay Trail board cannot get right screen resolution"
date: 2014-07-14
forum: Installation &amp; Upgrades
---

### Post by lyhtsm on 2014-07-14
I installed Ubuntu 12.04.2 server on a Bay Trail board, and installed X manually, but can't get right resolution.
I updated the drivers following ubuntu tutorial, mods changed in lsmod but didn't fix the problem.

I installed 14.04 and solved the problem, but 14.04 is way too large and boots slower than 12.04.2,
So can I fix the problem on 12.04.2?

Here are the different lsmod logs and lspci logs between 14.04 and 12.04.2.

1404serverlsmod
```
Module                  Size  Used by
snd_hda_codec_hdmi     45303  1 
snd_hda_codec_realtek    51029  1 
intel_rapl             18301  0 
coretemp               13195  0 
kvm_intel             132549  0 
kvm                   388083  1 kvm_intel
crc32_pclmul           12967  0 
snd_hda_intel          42730  0 
snd_hda_codec         164067  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
serio_raw              13230  0 
snd_timer              28584  1 snd_pcm
snd                    60871  7 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_hda_codec,snd_hda_intel
soundcore              12600  1 snd
joydev                 17101  0 
i915                  705396  2 
drm_kms_helper         46907  1 i915
drm                   243792  3 i915,drm_kms_helper
video                  18903  1 i915
i2c_algo_bit           13197  1 i915
mac_hid                13037  0 
lp                     13299  0 
parport                40836  1 lp
hid_generic            12492  0 
usbhid                 47035  0 
hid                    87604  2 hid_generic,usbhid
usb_storage            48417  0 
r8169                  61562  0 
mii                    13654  1 r8169
ahci                   25579  2 
libahci                26754  1 ahci



```

12.04.2 lsmod
```
Module                  Size  Used bycoretemp               13362  0 
kvm_intel             127736  0 
snd_hda_codec_realtek    64876  1 
kvm                   365556  1 kvm_intel
snd_hda_intel          33029  3 
snd_hda_codec         116477  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
snd_pcm                81124  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
xt_hl                  12466  0 
ip6t_rt                12474  0 
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
nf_conntrack_ipv6      13750  0 
nf_defrag_ipv6         13176  1 nf_conntrack_ipv6
ipt_REJECT             12513  0 
xt_LOG                 17238  0 
xt_multiport           12534  0 
xt_limit               12542  0 
xt_tcpudp              12532  0 
xt_addrtype            12597  0 
dm_multipath           22755  0 
xt_state               12515  0 
scsi_dh                14205  1 dm_multipath
microcode              18396  0 
ip6table_filter        12712  1 
ip6_tables             22382  2 ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12586  0 
nf_conntrack_broadcast    12542  1 nf_conntrack_netbios_ns
nf_nat_ftp             12596  0 
snd_timer              28932  2 snd_pcm,snd_seq
nf_nat                 24741  1 nf_nat_ftp
nf_conntrack_ipv4      14123  2 nf_nat
nf_defrag_ipv4         12650  1 nf_conntrack_ipv4
nf_conntrack_ftp       13184  1 nf_nat_ftp
nf_conntrack           66862  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12707  1 
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              18107  1 iptable_filter
x_tables               22012  13 xt_hl,ip6t_rt,ipt_REJECT,xt_LOG,xt_multiport,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
serio_raw              13032  0 
snd                    62675  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nfsd                  214706  2 
soundcore              14636  1 snd
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
nfs                   267817  0 
lockd                  66069  2 nfsd,nfs
fscache                50643  1 nfs
auth_rpcgss            35602  2 nfsd,nfs
nfs_acl                12772  2 nfsd,nfs
sunrpc                199304  6 nfsd,nfs,lockd,auth_rpcgss,nfs_acl
joydev                 17394  0 
mac_hid                13078  0 
lp                     17456  0 
parport                40931  1 lp
dm_raid45              76509  0 
xor                    26091  1 dm_raid45
dm_mirror              21862  0 
dm_region_hash         16101  1 dm_mirror
dm_log                 18194  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 749989  0 
zlib_deflate           26623  1 btrfs
libcrc32c              12544  1 btrfs
hid_generic            12485  0 
uas                    17745  0 
r8169                  56853  0 
usbhid                 46054  0 
hid                    82511  2 hid_generic,usbhid
video                  19070  0 
zram                   18244  1 



```

1404serverlspci
```

00:00.0 Host bridge: Intel Corporation ValleyView SSA-CUnit (rev 0e)
00:02.0 VGA compatible controller: Intel Corporation ValleyView Gen7 (rev 0e)
00:13.0 SATA controller: Intel Corporation ValleyView 6-Port SATA AHCI Controller (rev 0e)
00:14.0 USB controller: Intel Corporation ValleyView USB xHCI Host Controller (rev 0e)
00:1a.0 Encryption controller: Intel Corporation ValleyView SEC (rev 0e)
00:1b.0 Audio device: Intel Corporation ValleyView High Definition Audio Controller (rev 0e)
00:1c.0 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1c.1 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1c.2 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1c.3 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1f.0 ISA bridge: Intel Corporation ValleyView Power Control Unit (rev 0e)
00:1f.3 SMBus: Intel Corporation ValleyView SMBus Controller (rev 0e)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)



```

12042serverlspci
```

00:00.0 Host bridge: Intel Corporation Device 0f00 (rev 0e)
00:02.0 VGA compatible controller: Intel Corporation Device 0f31 (rev 0e)
00:13.0 SATA controller: Intel Corporation Device 0f23 (rev 0e)
00:14.0 USB controller: Intel Corporation Device 0f35 (rev 0e)
00:1a.0 Encryption controller: Intel Corporation Device 0f18 (rev 0e)
00:1b.0 Audio device: Intel Corporation Device 0f04 (rev 0e)
00:1c.0 PCI bridge: Intel Corporation Device 0f48 (rev 0e)
00:1c.1 PCI bridge: Intel Corporation Device 0f4a (rev 0e)
00:1c.2 PCI bridge: Intel Corporation Device 0f4c (rev 0e)
00:1c.3 PCI bridge: Intel Corporation Device 0f4e (rev 0e)
00:1f.0 ISA bridge: Intel Corporation Device 0f1c (rev 0e)
00:1f.3 SMBus: Intel Corporation Device 0f12 (rev 0e)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 0c)



```

---

