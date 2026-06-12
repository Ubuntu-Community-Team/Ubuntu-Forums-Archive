---
title: "How to troubleshoot hibernate / reboot problem"
date: 2012-06-20
forum: Installation &amp; Upgrades
---

### Post by johnfrith on 2012-06-20
Hi,

Since fresh installing 12.04,system sometimes (about 1 in 4) cold boots after previously hibernating, causing any open application to have to recover. Could someone advise of a way to troubleshoot this? I don't know where to start. I can just about use terminal, but would appreciate line by line instructions.

Thanks, John

---

### Post by dixonstalbert on 2012-06-21
hello

ubuntu.com wiki has some good info on hibernate troubleshooting

here are some other things:

open synaptic package manager and make sure pm-utils is installed.

if it is, open log file viewer. open pm-suspend.log and see what error messages are there.

hibernate problems are usually due to graphic cards and 'periperals' that misbehave. see if you can figure out from error message who is the trouble maker, then go on  internet and search for solutions.

 you can also try unplugging all cards and usbs and see if that helps, then add them back one by one

I use  "tuxonice" a special package you can find on google, because my hardware would not hibernate properly. the fellow who developed it is very knowledgable and has a good mailing list. I believe he is at tuxonice.net

good luck

---

### Post by johnfrith on 2012-06-22
Thanks dixonstalbert, that gives me a start. Never spotted the wiki before!

Hibernate worked with the same hardware using Ubuntu 10.04, so I hadn't considered that.

---

### Post by johnfrith on 2012-06-24
Ok, so following a failed hibernate, I've listed more info below. 

My home directory is not encrypted, and my swap is nearly twice my ram. Deck is a Clevo M76T.

This is the last bit of output of pm-suspend.log. The last bit sounds to me like it's successfully hibernating, but there's no thaw - so it must be a resume failure? Can anyone help me make sense of this? TIA.

```

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/15sl-modem-daemon hibernate hibernate:
Shutting down SmartLink Modem driver normally.
Unloading modem driver from kernel ... none found.

/usr/lib/pm-utils/sleep.d/15sl-modem-daemon hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Sat Jun 23 23:10:23 BST 2012: performing hibernate
Sun Jun 24 12:12:34 BST 2012: Awake.
Sun Jun 24 12:12:34 BST 2012: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/15sl-modem-daemon thaw hibernate:
Starting SmartLink Modem driver for: hw:0,6.
Creating /dev/modem symlink, pointing to: /dev/ttySL0.

/usr/lib/pm-utils/sleep.d/15sl-modem-daemon thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Sun Jun 24 12:12:56 BST 2012: Finished.
Initial commandline parameters: 
Sun Jun 24 19:13:04 BST 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux jf-laptop 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
nls_utf8               12557  0 
udf                    94317  0 
crc_itu_t              12707  1 udf
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61512  1 vfat
uas                    18180  0 
usb_storage            49198  0 
bnep                   18281  2 
rfcomm                 47604  0 
parport_pc             32866  0 
bluetooth             180104  10 bnep,rfcomm
ppdev                  17113  0 
joydev                 17693  0 
snd_hda_codec_si3054    13008  1 
snd_hda_codec_realtek   223867  1 
arc4                   12529  2 
rtl8187                57035  0 
mac80211              506816  1 rtl8187
cfg80211              205544  2 rtl8187,mac80211
eeprom_93cx6           12725  1 rtl8187
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_hda_intel          33773  6 
snd_hda_codec         127706  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  5 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  468745  3 
drm_kms_helper         46978  1 i915
snd                    78855  20 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   242038  4 i915,drm_kms_helper
psmouse                87692  0 
serio_raw              13211  0 
jmb38x_ms              17646  0 
memstick               16569  1 jmb38x_ms
i2c_algo_bit           13423  1 i915
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
wmi                    19256  0 
video                  19596  1 i915
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
r8169                  62099  0 
             total       used       free     shared    buffers     cached
Mem:       3981584    1545492    2436092          0      43184     660844
-/+ buffers/cache:     841464    3140120
Swap:      7811068     425704    7385364

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/15sl-modem-daemon hibernate hibernate:
Shutting down SmartLink Modem driver normally.
Unloading modem driver from kernel ... none found.

/usr/lib/pm-utils/sleep.d/15sl-modem-daemon hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Sun Jun 24 19:13:07 BST 2012: performing hibernate
```Here is dmesg:

```
[    1.457239] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.457266] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.457404] mousedev: PS/2 mouse device common for all mice
[    1.457745] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.457776] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.457859] device-mapper: uevent: version 1.0.3
[    1.457930] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.457995] cpuidle: using governor ladder
[    1.458085] cpuidle: using governor menu
[    1.458087] EFI Variables Facility v0.08 2004-May-17
[    1.458327] TCP cubic registered
[    1.458443] NET: Registered protocol family 10
[    1.458902] NET: Registered protocol family 17
[    1.458916] Registering the dns_resolver key type
[    1.459096] PM: Hibernation image not present or could not be loaded.
[    1.459110] registered taskstats version 1
[    1.478051]   Magic number: 0:513:452
[    1.478182] rtc_cmos 00:07: setting system clock to 2012-06-24 22:25:39 UTC (1340576739)
[    1.478649] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.478651] EDD information not available.
[    1.492466] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.743190] ata4: SATA link down (SStatus 0 SControl 300)
[    1.754310] ata3: SATA link down (SStatus 0 SControl 300)
[    1.796105] usb 2-5: new high-speed USB device number 2 using ehci_hcd
[    1.884150] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.888246] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.896277] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T50N, RQ01, max UDMA/133
[    1.912251] ata2.00: configured for UDMA/133
[    1.940552] ata1.00: ATA-8: TOSHIBA MK2555GSX, FG001A, max UDMA/100
[    1.940558] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.948448] ata1.00: configured for UDMA/100
[    1.948643] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK2555GS FG00 PQ: 0 ANSI: 5
[    1.948779] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.948794] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.948830] sd 0:0:0:0: [sda] Write Protect is off
[    1.948833] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.948873] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.025749] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T50N  RQ01 PQ: 0 ANSI: 5
[    2.042315]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    2.042934] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.048105] usb 2-6: new high-speed USB device number 3 using ehci_hcd
[    2.135866] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.135871] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.136052] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.136181] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.137976] Freeing unused kernel memory: 920k freed
[    2.138279] Write protecting the kernel read-only data: 12288k
[    2.143940] Freeing unused kernel memory: 1604k freed
[    2.148757] Freeing unused kernel memory: 1196k freed
[    2.165764] udevd[149]: starting version 175
[    2.622559] sdhci: Secure Digital Host Controller Interface driver
[    2.622562] sdhci: Copyright(c) Pierre Ossman
[    2.622870] sdhci-pci 0000:09:00.0: SDHCI controller found [197b:2382] (rev 20)
[    2.622895] sdhci-pci 0000:09:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.622946] sdhci-pci 0000:09:00.0: setting latency timer to 64
[    2.622961] mmc0: no vmmc regulator found
[    2.623022] Registered led device: mmc0::
[    2.624998] mmc0: SDHCI controller on PCI [0000:09:00.0] using DMA
[    2.625015] sdhci-pci 0000:09:00.2: SDHCI controller found [197b:2381] (rev 20)
[    2.625036] sdhci-pci 0000:09:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.625044] sdhci-pci 0000:09:00.2: Refusing to bind to secondary interface.
[    2.625052] sdhci-pci 0000:09:00.2: PCI INT A disabled
[    2.626517] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.626539] r8169 0000:08:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.626578] r8169 0000:08:00.0: setting latency timer to 64
[    2.626742] r8169 0000:08:00.0: irq 45 for MSI/MSI-X
[    2.628156] r8169 0000:08:00.0: eth0: RTL8168c/8111c at 0xffffc90000656000, 00:90:f5:97:68:09, XID 1c4000c0 IRQ 45
[    2.628160] r8169 0000:08:00.0: eth0: jumbo features [frames: 6128 bytes, tx checksumming: ko]
[    2.636043] usb 5-2: new low-speed USB device number 2 using uhci_hcd
[    2.854680] input: Microsoft Microsoft Optical Mouse with Tilt Wheel as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input5
[    2.854804] generic-usb 0003:045E:00D1.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Optical Mouse with Tilt Wheel] on usb-0000:00:1a.2-2/input0
[    2.854819] usbcore: registered new interface driver usbhid
[    2.854820] usbhid: USB HID core driver
[    7.610982] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    7.610985] EXT4-fs (sda5): write access will be enabled during recovery
[   10.103447] EXT4-fs (sda5): orphan cleanup on readonly fs
[   10.103457] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1576789
[   10.103532] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1576801
[   10.125849] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 264127
[   10.135040] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1977394
[   10.157859] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1972186
[   10.157921] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1972184
[   10.170850] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1975324
[   10.192579] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1838724
[   10.192632] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1576245
[   10.192706] EXT4-fs (sda5): 9 orphan inodes deleted
[   10.192708] EXT4-fs (sda5): recovery complete
[   10.286263] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   23.486229] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.517891] udevd[576]: starting version 175
[   23.558944] Adding 7811068k swap on /dev/sda6.  Priority:-1 extents:1 across:7811068k 
[   23.567687] lp: driver loaded but no devices found
[   24.003860] wmi: Mapper loaded
[   24.008710] [drm] Initialized drm 1.1.0 20060810
[   24.057129] i915 0000:00:02.0: power state changed by ACPI to D0
[   24.057135] i915 0000:00:02.0: power state changed by ACPI to D0
[   24.057143] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   24.057147] i915 0000:00:02.0: setting latency timer to 64
[   24.078134] type=1400 audit(1340576762.097:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=812 comm="apparmor_parser"
[   24.078521] type=1400 audit(1340576762.097:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=812 comm="apparmor_parser"
[   24.078745] type=1400 audit(1340576762.097:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=812 comm="apparmor_parser"
[   24.079321] jmb38x_ms 0000:09:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   24.079330] jmb38x_ms 0000:09:00.3: setting latency timer to 64
[   24.168786] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[   24.168793] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   24.168795] [drm] Driver supports precise vblank timestamp query.
[   24.224182] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   24.279031] fixme: max PWM is zero.
[   24.414093] cfg80211: Calling CRDA to update world regulatory domain
[   24.421432] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   24.465451] Linux video capture interface: v2.00
[   24.466175] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:0241)
[   24.472191] input: BisonCam, NB Pro as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input6
[   24.473602] usbcore: registered new interface driver uvcvideo
[   24.473606] USB Video Class driver (1.1.1)
[   24.476317] cfg80211: World regulatory domain updated:
[   24.476321] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   24.476324] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.476326] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.476329] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.476332] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.476335] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.636209] fbcon: inteldrmfb (fb0) is primary device
[   24.636425] Console: switching to colour frame buffer device 180x56
[   24.636453] fb0: inteldrmfb frame buffer device
[   24.636455] drm: registered panic notifier
[   24.647536] acpi device:05: registered as cooling_device2
[   24.647627] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   24.647688] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   24.647781] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   24.647838] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   24.647922] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   24.647956] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   24.708775] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   24.708929] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   24.761779] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   24.761784] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.761787] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   24.761790] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.761792] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   24.761795] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.761797] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   24.761800] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.761802] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   24.761805] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.761808] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   24.761811] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.761813] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   24.761816] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.761818] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   24.761821] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.761823] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   24.761826] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.761828] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   24.761831] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.761833] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   24.761836] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.761839] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   24.761842] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.761844] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   24.761847] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.761849] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   24.761852] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.767528] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   24.768098] ieee80211 phy0: hwaddr 00:01:38:fd:9c:ad, RTL8187BvE V0 + rtl8225z2, rfkill mask 2
[   24.790721] rtl8187: Customer ID is 0x00
[   24.790794] Registered led device: rtl8187-phy0::radio
[   24.790830] Registered led device: rtl8187-phy0::tx
[   24.791002] Registered led device: rtl8187-phy0::rx
[   24.792464] rtl8187: wireless switch is on
[   24.792527] usbcore: registered new interface driver rtl8187
[   24.844857] psmouse serio4: synaptics: Touchpad model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04711/0x202000/0x0
[   24.881211] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10
[   25.573229] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   26.765604] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   27.785714] init: failsafe main process (1210) killed by TERM signal
[   27.831493] Bluetooth: Core ver 2.16
[   27.831535] NET: Registered protocol family 31
[   27.831538] Bluetooth: HCI device and connection manager initialized
[   27.831541] Bluetooth: HCI socket layer initialized
[   27.831543] Bluetooth: L2CAP socket layer initialized
[   27.831914] Bluetooth: SCO socket layer initialized
[   27.834813] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.834817] Bluetooth: BNEP filters: protocol multicast
[   27.852372] Bluetooth: RFCOMM TTY layer initialized
[   27.852381] Bluetooth: RFCOMM socket layer initialized
[   27.852383] Bluetooth: RFCOMM ver 1.11
[   27.882491] r8169 0000:08:00.0: eth0: link down
[   27.882974] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.883256] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.643452] type=1400 audit(1340576766.661:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1295 comm="apparmor_parser"
[   28.644360] type=1400 audit(1340576766.665:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1295 comm="apparmor_parser"
[   28.644864] type=1400 audit(1340576766.665:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1295 comm="apparmor_parser"
[   28.645013] type=1400 audit(1340576766.665:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1294 comm="apparmor_parser"
[   28.657989] ppdev: user-space parallel port driver
[   28.663018] type=1400 audit(1340576766.681:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1301 comm="apparmor_parser"
[   28.663506] type=1400 audit(1340576766.681:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1301 comm="apparmor_parser"
[   28.677745] type=1400 audit(1340576766.697:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1298 comm="apparmor_parser"
[   29.464686] init: plymouth-stop pre-start process (1708) terminated with status 1
[   31.994942] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.997262] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.393464] wlan0: authenticate with 5c:d9:98:ca:c6:60 (try 1)
[   37.395759] wlan0: authenticated
[   37.677336] wlan0: associate with 5c:d9:98:ca:c6:60 (try 1)
[   37.679981] wlan0: RX AssocResp from 5c:d9:98:ca:c6:60 (capab=0xc31 status=0 aid=3)
[   37.679985] wlan0: associated
[   37.685775] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   37.685856] cfg80211: Calling CRDA for country: GB
[   37.690609] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   37.690613] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   37.690616] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   37.690619] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   37.690621] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   37.690624] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   37.690626] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   37.690629] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   37.690631] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   37.690634] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   37.690636] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   37.690639] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   37.690642] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   37.690644] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   37.690647] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   37.690650] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   37.690652] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   37.690655] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   37.690657] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   37.690660] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   37.690662] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   37.690665] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   37.690667] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   37.690670] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   37.690672] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   37.690675] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   37.690677] cfg80211: Disabling freq 2484 MHz
[   37.690680] cfg80211: Regulatory domain changed to country: GB
[   37.690682] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   37.690685] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   37.690687] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   37.690690] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   37.690692] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   47.832030] wlan0: no IPv6 routers present
[  882.556643] wlan0: deauthenticated from 5c:d9:98:ca:c6:60 (Reason: 3)
[  882.658694] cfg80211: All devices are disconnected, going to restore regulatory settings
[  882.658704] cfg80211: Restoring regulatory settings
[  882.658717] cfg80211: Calling CRDA to update world regulatory domain
[  882.665727] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  882.665734] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  882.665739] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  882.665745] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  882.665749] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  882.665754] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  882.665759] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  882.665764] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  882.665768] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  882.665773] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  882.665778] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  882.665783] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  882.665787] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  882.665793] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  882.665797] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  882.665802] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  882.665806] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  882.665811] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  882.665815] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  882.665821] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  882.665825] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  882.665831] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  882.665835] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  882.665840] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  882.665844] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  882.665850] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  882.665854] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  882.665859] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  882.665865] cfg80211: World regulatory domain updated:
[  882.665868] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  882.665873] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  882.665878] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  882.665883] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  882.665887] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  882.665892] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  885.149400] wlan0: authenticate with 5c:d9:98:ca:c6:60 (try 1)
[  885.151149] wlan0: authenticated
[  885.289860] wlan0: associate with 5c:d9:98:ca:c6:60 (try 1)
[  885.292887] wlan0: RX ReassocResp from 5c:d9:98:ca:c6:60 (capab=0xc31 status=0 aid=1)
[  885.292893] wlan0: associated
[  885.299579] cfg80211: Calling CRDA for country: GB
[  885.306780] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  885.306789] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  885.306794] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  885.306799] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  885.306803] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  885.306809] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  885.306813] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  885.306818] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  885.306822] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  885.306827] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  885.306831] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  885.306837] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  885.306841] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  885.306846] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  885.306850] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  885.306855] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  885.306859] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  885.306865] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  885.306869] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  885.306874] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  885.306878] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  885.306884] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  885.306888] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  885.306893] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  885.306897] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  885.306902] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  885.306906] cfg80211: Disabling freq 2484 MHz
[  885.306911] cfg80211: Regulatory domain changed to country: GB
[  885.306914] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  885.306919] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  885.306924] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  885.306928] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  885.306933] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)

```Here is cat /proc/cmdline:

```
BOOT_IMAGE=/boot/vmlinuz-3.2.0-25-generic root=UUID=974292ee-24d1-47c1-86d6-cf98c55fa49e ro quiet splash acpi_sleep=nonvs vt.handoff=7

```Here is cat /etc/initramfs-tools/conf.d/resume:

```
RESUME=UUID=9e6948d5-f0d1-402e-b6cb-e96363c1d1fa

```

---

### Post by johnfrith on 2012-07-01
My issue also arises if I use pm-hibernate from the terminal, just like if I close the lid of my laptop, or hibernate from the menu.

Any wise words from anyone?

The dmesg line: ```
 PM: Hibernation image not present or could not be loaded.
```would seem to indicate this a resume failure, but I don't know where to go from there. Doesn't seem to be any one else having this problem after jumping from 10.04.

---

