---
title: "No WiFi since installing Mint"
date: 2017-04-09
forum: MINT
---

### Post by oldmanlearning on 2017-04-09
I'm running an HP 2000 notebook. I'm sure you've heard the story of getting tired of windows and wanted to try Linux. I installed Linux Mint 18, Sarah, haven't been able to use WiFi since then, It doesn't recognize that there is WiFi and there is. I surely do like Linux, makes Windows look like a turtle. I did try downloading it again and burned it to a different disk and tried re-installing it but that didn't help. Any ideas out there. I tried different things I saw on PC World and a couple others but they didn't work either, went through the forum and also tried a few but nothing so far has worked. It's like it's missing code or something.

---

### Post by praseodym on 2017-04-09
Hi,

please open a terminal and show the outputs of these 5 commands
```

lspci -nnk
lsusb
lsmod
rfkill list
iwconfig
```Lets have a look at the hardware. Does LAN work?

---

### Post by howefield on 2017-04-09
Moved to the "[S]*Ubuntu/Debian BASED*[/S]" "*MINT*" forum.

---

### Post by kc1di on 2017-04-09
Hello oldmanlearning  and welcome to Ubuntu Forums,
We need to know what wifi card/chipset is in your machine.  

Please go to a terminal and type the following commands and post the output here.
```
lspci
rfkill
lsmod
```

---

### Post by oldmanlearning on 2017-04-09
```
Subsystem: Hewlett-Packard Company 6 Series/C200 Series Chipset Family SMBus Controller [103c:3672]
	Kernel modules: i2c_i801
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
	DeviceName: Realtek PCIe FE Family Controller
	Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:3672]
	Kernel driver in use: r8169
	Kernel modules: r8169
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	DeviceName: Realtek RTL8188CE 802.11b/g/n WiFi Adapter
	Subsystem: Hewlett-Packard Company RTL8188CE 802.11b/g/n WiFi Adapter [103c:1629]
	Kernel driver in use: rtl8192ce
	Kernel modules: rtl8192ce
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)
	Subsystem: Hewlett-Packard Company RTS5209 PCI Express Card Reader [103c:3672]
	Kernel driver in use: rtsx_pci
	Kernel modules: rtsx_pci
```

```
Bus 002 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05c8:021e Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
Module                  Size  Used by
appletalk              36864  0
ipx                    28672  0
p8023                  16384  1 ipx
p8022                  16384  1 ipx
psnap                  16384  2 ipx,appletalk
llc                    16384  2 p8022,psnap
binfmt_misc            20480  1
uvcvideo               90112  0
arc4                   16384  2
rtl8192ce              57344  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         28672  1 uvcvideo
videobuf2_core         36864  2 uvcvideo,videobuf2_v4l2
v4l2_common            16384  1 videobuf2_v4l2
rtl_pci                28672  1 rtl8192ce
rtl8192c_common        53248  1 rtl8192ce
rtlwifi                77824  3 rtl_pci,rtl8192c_common,rtl8192ce
videodev              176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
mac80211              737280  3 rtl_pci,rtlwifi,rtl8192ce
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
snd_hda_intel          40960  3
media                  24576  2 uvcvideo,videodev
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
snd_hda_codec         135168  3 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           73728  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
intel_rapl             20480  0
snd_hwdep              16384  1 snd_hda_codec
cfg80211              565248  2 mac80211,rtlwifi
snd_pcm               106496  3 snd_hda_codec,snd_hda_intel,snd_hda_core
x86_pkg_temp_thermal    16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
intel_powerclamp       16384  0
snd_rawmidi            32768  1 snd_seq_midi
coretemp               16384  0
kvm                   544768  0
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
rtsx_pci_ms            20480  0
input_leds             16384  0
joydev                 20480  0
irqbypass              16384  1 kvm
serio_raw              16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
memstick               20480  1 rtsx_pci_ms
mei_me                 36864  0
snd                    81920  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
mei                    98304  1 mei_me
soundcore              16384  1 snd
shpchp                 36864  0
lpc_ich                24576  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
btrfs                 987136  0
xor                    24576  1 btrfs
raid6_pq              102400  1 btrfs
drbg                   32768  1
ansi_cprng             16384  0
xts                    16384  1
gf128mul               16384  1 xts
algif_skcipher         20480  0
af_alg                 16384  1 algif_skcipher
dm_crypt               28672  1
dm_mirror              24576  0
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  3 hid_generic,usbhid
rtsx_pci_sdmmc         24576  0
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
cryptd                 20480  1 ghash_clmulni_intel
i915                 1208320  4
psmouse               131072  0
i2c_algo_bit           16384  1 i915
drm_kms_helper        155648  1 i915
r8169                  81920  0
ahci                   36864  2
syscopyarea            16384  1 drm_kms_helper
libahci                32768  1 ahci
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
rtsx_pci               53248  2 rtsx_pci_ms,rtsx_pci_sdmmc
drm                   364544  6 i915,drm_kms_helper
mii                    16384  1 r8169
wmi                    20480  1 hp_wmi
video                  40960  1 i915
fjes                   28672  0
```

```
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

```
lo        no wireless extensions.


wlo1      IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          
eno1      no wireless extensions.
```

---

### Post by praseodym on 2017-04-09
As you can see from "rfkill list" and from "Tx-Power=off " the card is turned off. Any button, switch, key or key combination to turn it on? The driver is there (rtl8192ce)

---

### Post by oldmanlearning on 2017-04-09
It is the F12 button and I've hit it several times and it still doesn't come on. Doing that without ethernet cable plugged in.

---

### Post by robbie 348 on 2017-04-09
Which DE are you using, Mate, KDE, XFCE or Cinnamon?

---

### Post by oldmanlearning on 2017-04-09
Cinnamon

---

### Post by robbie 348 on 2017-04-09
Have you looked at the network controller in system settings, there's an on/off switch for wi-fi?

---

### Post by jeremy31 on 2017-04-09
I would shutdown the laptop, remove battery and power cable, then press the power button for 20 seconds.  Connect battery and power cable and see if wireless works

---

### Post by kc1di on 2017-04-09
check in your bios there is wifi /network card on/off there also.

---

### Post by oldmanlearning on 2017-04-09
Good thought but it's on.

---

### Post by oldmanlearning on 2017-04-09
It is cinnamon 64 bit if that makes a difference.

---

### Post by oldmanlearning on 2017-04-09
I thought you said network manager for there is one there and it is on. I'm not sure how to check in the bios

---

### Post by kc1di on 2017-04-09
most computers have a key or combination of key that will cause you to enter into a setup of some sort just as you begin to boot the machine and
I'm not sure which key or keys it may be on your machine.

---

### Post by mc4man on 2017-04-09
don't know if Mint uses but here in Ubuntu at the bottom of grub2 selection screen is "System Setup" which will open the bios or setup.

---

### Post by oldmanlearning on 2017-04-22
Sorry for the long time, been rather busy. I did the escape button and booted it that way and did a repair and the WiFi button is now turned on but when I go to set it up it comes up with this.
unavailable -802.1x supplicant failed.

---

### Post by oldmanlearning on 2017-04-22
Figured it out, it is now working, thanks for all the help, I am now wireless.

---

