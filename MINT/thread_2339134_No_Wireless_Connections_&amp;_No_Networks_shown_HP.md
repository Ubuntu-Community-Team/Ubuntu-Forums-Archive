---
title: "No Wireless Connections &amp; No Networks shown HP EliteBook 8440P"
date: 2016-10-05
forum: MINT
---

### Post by emox on 2016-10-05
Hello everyone,

I am new in the forum and i need some help assistance about how to fix my Wireless Connection on my girlfriend's Laptop.
I have installed the latest Linux Mint 18 Sarah (64bit) (I am posting this here because i have noticed that Linux Mint it's like an Ubuntu-it uses apt-get & debian package manager)  and the Wireless is showing no connections.
The Wireless adapter is Intel Corporation Centrino Advanced-N 6200 (rev 35) (this is what i got from the lspci command output).

lspci output
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 05)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation QM57 Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
43:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
44:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 06)
44:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 25)
44:06.2 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev bb)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation 1st Generation Core i3/5/7 Processor Reserved (rev 02)

```

The Wireless is not blocked i can turn it off /on and it's lighting (on->blue/ off->red)

rfkill list output when the WIFI is ON (indicator is blue)
```

0: phy0: Wireless LAN
   Soft blocked: no
   Hard blocked: yes
1: hp-wifi: Wireless LAN
   Soft blocked: no
   Hard blocked: no
2: hp-bluetooth: Bluetooth
   Soft blocked: no
   Hard blocked: no
5: hci0: Bluetooth
   Soft blocked: no
   Hard blocked: no

```

rfkill output when WIFI is OFF (indicator is red)
```

0: phy0: Wireless LAN
   Soft blocked: no
   Hard blocked: yes
1: hp-wifi: Wireless LAN
   Soft blocked: no
   Hard blocked: yes
2: hp-bluetooth: Bluetooth
   Soft blocked: no
   Hard blocked: yes

```

lsmod output
```

Module                  Size  Used by
rfcomm                 69632  0
bnep                   20480  2
binfmt_misc            20480  1
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
snd_hda_codec_hdmi     53248  2
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                  24576  2 uvcvideo,videodev
pata_pcmcia            20480  1
intel_powerclamp       16384  0
btusb                  45056  0
btrtl                  16384  1 btusb
coretemp               16384  0
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             520192  12 bnep,btbcm,btrtl,btusb,rfcomm,btintel
kvm_intel             172032  0
hp_wmi                 16384  0
arc4                   16384  2
sparse_keymap          16384  1 hp_wmi
kvm                   536576  1 kvm_intel
iwldvm                233472  0
irqbypass              16384  1 kvm
mac80211              737280  1 iwldvm
snd_hda_codec_idt      57344  1
snd_hda_codec_generic    77824  1 snd_hda_codec_idt
snd_hda_intel          36864  3
snd_hda_codec         135168  4 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel
crct10dif_pclmul       16384  0
snd_hda_core           73728  5 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
crc32_pclmul           16384  0
snd_hwdep              16384  1 snd_hda_codec
aesni_intel           167936  0
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
aes_x86_64             20480  1 aesni_intel
iwlwifi               200704  1 iwldvm
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
lrw                    16384  1 aesni_intel
pcmcia                 61440  1 pata_pcmcia
gf128mul               16384  1 lrw
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
cfg80211              565248  3 iwlwifi,mac80211,iwldvm
glue_helper            16384  1 aesni_intel
snd_timer              32768  2 snd_pcm,snd_seq
snd                     81920  17  snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
soundcore              16384  1 snd
yenta_socket           45056  0
pcmcia_rsrc            20480  1 yenta_socket
joydev                 20480  0
pcmcia_core            24576  3 pcmcia,pcmcia_rsrc,yenta_socket
input_leds             16384  0
serio_raw              16384  0
8250_fintek            16384  0
shpchp                 36864  0
tpm_infineon           20480  0
hp_accel               28672  0
mei_me                 36864  0
mei                    98304  1 mei_me
lis3lv02d              20480  1 hp_accel
lpc_ich                24576  0
input_polldev          16384  1 lis3lv02d
mac_hid                16384  0
ip6t_REJECT            16384  1
nf_reject_ipv6         16384  1 ip6t_REJECT
nf_log_ipv6            16384  5
xt_hl                  16384  22
ip6t_rt                16384  3
nf_conntrack_ipv6      20480  8
nf_defrag_ipv6         36864  1 nf_conntrack_ipv6
ipt_REJECT             16384  1
nf_reject_ipv4         16384  1 ipt_REJECT
nf_log_ipv4            16384  5
nf_log_common          16384  2 nf_log_ipv4,nf_log_ipv6
xt_LOG                 16384  10
xt_limit               16384  13
xt_tcpudp              16384  18
xt_addrtype            16384  4
nf_conntrack_ipv4      16384  8
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  16
ip6table_filter        16384  1
ip6_tables             28672  1 ip6table_filter
nf_conntrack_netbios_ns    16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_nat_ftp             16384  0
nf_nat                 24576  1 nf_nat_ftp
nf_conntrack_ftp       20480  1 nf_nat_ftp
nf_conntrack           106496  8  nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         16384  1
ip_tables              28672  1 iptable_filter
x_tables                36864  13  ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT
parport_pc             32768  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
btrfs                 987136  0
xor                    24576  1 btrfs
raid6_pq              102400  1 btrfs
dm_mirror              24576  0
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
i915                 1208320  10
psmouse               126976  0
i2c_algo_bit           16384  1 i915
intel_ips              20480  0
ahci                   36864  2
drm_kms_helper        139264  1 i915
libahci                32768  1 ahci
sdhci_pci              28672  0
syscopyarea            16384  1 drm_kms_helper
sdhci                  45056  1 sdhci_pci
sysfillrect            16384  1 drm_kms_helper
firewire_ohci          40960  0
e1000e                237568  0
sysimgblt              16384  1 drm_kms_helper
firewire_core          65536  1 firewire_ohci
fb_sys_fops            16384  1 drm_kms_helper
drm                   360448  7 i915,drm_kms_helper
crc_itu_t              16384  1 firewire_core
ptp                    20480  1 e1000e
pps_core               20480  1 ptp
wmi                    20480  1 hp_wmi
video                  40960  1 i915
fjes                   28672  0

```

I would apprciate your help. Meanwhile i will be digging in Google for a solution.
Thank you in advance.

Regards,
Emil Tsvetanov

---

### Post by howefield on 2016-10-05
Thread moved to the "*MINT*" sub forum.

---

