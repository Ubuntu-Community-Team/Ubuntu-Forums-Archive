---
title: "Ubuntu 16.04.1 on Dell Insprion 1521 - 260GB SSD drive doesn't recognize Wifi or NIC"
date: 2018-06-15
forum: Installation &amp; Upgrades
---

### Post by mbw4359 on 2018-06-15
Hello,

The original drive was a TOSHIBA MK8037GSX which crashed and I had original installed Ubuntu 16.04.1 on this Laptop. I found out that the Dell Insrion 1521 will only support a 750GB drive. I assumed that it would support this. I installed on the drive but there's no network now! 

I really would like to resolve this with the SSD drive the machine seems to be much faster with this drive. I have attached the dmesg output maybe this will tell someone how to help me!

Thanks in advance

Michael

BTW I'm assuming the RIP in the dmesg is NOT Good but I don't know what it's telling me!

RIP  [<ffffffffc0547673>] wl_cfg80211_detach+0xf3/0x100 [wl]
[   10.632010]  RSP <ffff880034467968>
[   10.658739] ---[ end trace 0dfb03a267c03ed8 ]---
[   10.830104] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x10c0, revision 0
[   10.830333] piix4_smbus 0000:00:14.0: Auxiliary SMBus Host Controller at 0x10d0
[   11.002192] EDAC MC: Ver: 3.0.0
[   11.013298] r592: driver successfully loaded
[   11.013618] MCE: In-kernel MCE decoding enabled.
[   11.022494] AMD64 EDAC driver v3.4.0
[   11.022581] EDAC amd64: DRAM ECC disabled.
[   11.022593] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
                Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
                (Note that use of the override may cause unknown side effects.)
[   11.057490] Adding 1963004k swap on /dev/sda5.  Priority:-1 extents:1 across:1963004k SSFS
[   11.058484] r852: driver loaded successfully
[   11.206285] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   11.377159] random: nonblocking pool is initialized
[   12.404142] kvm: Nested Virtualization enabled
[   12.500189] snd_hda_codec_idt hdaudioC0D0: autoconfig for STAC9205: line_outs=1 (0xd/0x0/0x0/0x0/0x0) type:speaker
[   12.500206] snd_hda_codec_idt hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.500210] snd_hda_codec_idt hdaudioC0D0:    hp_outs=1 (0xa/0x0/0x0/0x0/0x0)
[   12.500213] snd_hda_codec_idt hdaudioC0D0:    mono: mono_out=0x0
[   12.500216] snd_hda_codec_idt hdaudioC0D0:    dig-out=0x21/0x0
[   12.500219] snd_hda_codec_idt hdaudioC0D0:    inputs:
[   12.500223] snd_hda_codec_idt hdaudioC0D0:      Internal Mic=0x17
[   12.500226] snd_hda_codec_idt hdaudioC0D0:      Mic=0xb
[   12.532514] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[   12.532645] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
[   12.610094] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   12.983432] input: Dell WMI hotkeys as /devices/virtual/input/input10
[   13.311851] cfg80211: World regulatory domain updated:
[   13.311862] cfg80211:  DFS Master region: unset
[   13.311865] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   13.311869] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   13.311872] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   13.311874] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   13.311877] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   13.311881] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   13.311884] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   13.311887] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   13.311889] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[  785.368066] usb 1-1: new high-speed USB device number 2 using ehci-pci
[  785.947134] usb 1-1: New USB device found, idVendor=154b, idProduct=0059
[  785.947153] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  785.947161] usb 1-1: Product: USB 2.0 FD
[  785.947168] usb 1-1: Manufacturer: PNY Technologies
[  785.947174] usb 1-1: SerialNumber: AABA08CC00000022
[  786.031658] usb-storage 1-1:1.0: USB Mass Storage device detected
[  786.036138] scsi host6: usb-storage 1-1:1.0
[  786.039764] usbcore: registered new interface driver usb-storage
[  786.059986] usbcore: registered new interface driver uas
[  789.098427] scsi 6:0:0:0: Direct-Access     PNY      USB 2.0 FD       8192 PQ: 0 ANSI: 0 CCS
[  789.101140] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  789.101614] sd 6:0:0:0: [sdb] 15826944 512-byte logical blocks: (8.10 GB/7.55 GiB)
[  789.108094] sd 6:0:0:0: [sdb] Write Protect is off
[  789.108120] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00
[  789.109524] sd 6:0:0:0: [sdb] No Caching mode page found
[  789.109545] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  789.116803]  sdb: sdb1
[  789.121396] sd 6:0:0:0: [sdb] Attached SCSI removable disk

---

