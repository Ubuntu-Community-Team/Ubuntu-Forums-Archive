---
title: "Mint 18.1 No Sound Device"
date: 2017-01-13
forum: MINT
---

### Post by M.D.G. on 2017-01-13
I have just put Mint 18.1 on a Dell XPS 9360 and cannot get any audio to work. The output from inxi -Fxz is as follows

```

$inxi -Fxz


System:    Host: xps Kernel: 4.4.0-59-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Cinnamon 3.2.7 (Gtk 3.18.9-1ubuntu3.1)
           Distro: Linux Mint 18.1 Serena
Machine:   System: Dell (portable) product: XPS 13 9360
           Mobo: Dell model: 0T3FTF v: A00
           Bios: Dell v: 1.0.7 date: 09/13/2016
CPU:       Dual core Intel Core i7-7500U (-HT-MCP-) cache: 4096 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 11615
           clock speeds: max: 2701 MHz 1: 1600 MHz 2: 800 MHz 3: 400 MHz
           4: 1100 MHz
Graphics:  Card: Intel Device 5916 bus-ID: 00:02.0
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1920x1080@59.93hz
           GLX Renderer: Mesa DRI Intel Kabylake GT2
           GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes
Network:   Card-1: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter
           driver: ath10k_pci bus-ID: 3a:00.0
           IF: wlp58s0 state: up mac: <filter>
           Card-2: Atheros usb-ID: 001-002
           IF: null-if-id state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: NA (-) ID-1: /dev/nvme0n1 model: N/A size: 256.1GB
Partition: ID-1: / size: 226G used: 15G (7%) fs: ext4 dev: /dev/dm-1
           ID-2: /boot size: 473M used: 114M (26%) fs: ext2 dev: /dev/nvme0n1p2
           ID-3: swap-1 size: 8.46GB used: 0.00GB (0%) fs: swap dev: /dev/dm-2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 25.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 224 Uptime: 14 min Memory: 1283.3/7865.1MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.461) inxi: 2.2.35 

```

Unsure if this is relevant, but the output from the alsa diagnostic script available [here]("https://wiki.ubuntu.com/Audio/AlsaInfo") was 

```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################


!!Script ran on: Fri Jan 13 18:07:37 UTC 2017




!!Linux Distribution
!!------------------


Linux Mint 18.1 Serena \n \l DISTRIB_ID=LinuxMint DISTRIB_DESCRIPTION="Linux Mint 18.1 Serena" NAME="Linux Mint" ID=linuxmint ID_LIKE=ubuntu PRETTY_NAME="Linux Mint 18.1" HOME_URL="http://www.linuxmint.com/" SUPPORT_URL="http://forums.linuxmint.com/" BUG_REPORT_URL="http://bugs.launchpad.net/linuxmint/" UBUNTU_CODENAME=xenial




!!DMI Information
!!---------------


Manufacturer:      Dell Inc.
Product Name:      XPS 13 9360
Product Version:   
Firmware Version:  1.0.7




!!Kernel Information
!!------------------


Kernel release:    4.4.0-59-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes




!!ALSA Version
!!------------


Driver version:     
Library version:    
Utilities version:  1.1.0




!!Loaded ALSA modules
!!-------------------






!!Sound Servers on this system
!!----------------------------


Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes




!!Soundcards recognised by ALSA
!!-----------------------------






!!PCI Soundcards installed in the system
!!--------------------------------------






!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------






!!Modprobe options (Sound related)
!!--------------------------------


snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2




!!Loaded sound module options
!!---------------------------




!!ALSA Device nodes
!!-----------------


crw-rw----+ 1 root audio 116,  1 Jan 13 12:49 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Jan 13 12:49 /dev/snd/timer




!!Aplay/Arecord output
!!--------------------


APLAY


aplay: device_list:268: no soundcards found...


ARECORD


arecord: device_list:268: no soundcards found...


!!Amixer output
!!-------------




!!Alsactl output
!!--------------


--startcollapse--
--endcollapse--




!!All Loaded Modules
!!------------------


Module
ctr
ccm
arc4
bnep
binfmt_misc
nls_iso8859_1
hid_multitouch
dell_laptop
dcdbas
i2c_designware_platform
i2c_designware_core
dell_wmi
ath10k_pci
ath10k_core
ath
mac80211
x86_pkg_temp_thermal
coretemp
uvcvideo
kvm_intel
kvm
cfg80211
irqbypass
rtsx_pci_ms
videobuf2_vmalloc
memstick
videobuf2_memops
videobuf2_v4l2
videobuf2_core
v4l2_common
videodev
joydev
input_leds
serio_raw
media
btusb
btrtl
idma64
virt_dma
mei_me
processor_thermal_device
mei
intel_soc_dts_iosf
shpchp
intel_lpss_pci
hci_uart
btbcm
btqca
btintel
intel_vbtn
soc_button_array
bluetooth
intel_lpss_acpi
intel_lpss
int3403_thermal
intel_hid
int340x_thermal_zone
sparse_keymap
tpm_crb
int3400_thermal
acpi_thermal_rel
acpi_pad
acpi_als
kfifo_buf
mac_hid
industrialio
parport_pc
ppdev
lp
parport
autofs4
btrfs
xor
raid6_pq
jitterentropy_rng
drbg
ansi_cprng
algif_skcipher
af_alg
dm_crypt
dm_mirror
dm_region_hash
dm_log
rtsx_pci_sdmmc
crct10dif_pclmul
crc32_pclmul
ghash_clmulni_intel
aesni_intel
i915_bpo
aes_x86_64
lrw
gf128mul
glue_helper
ablk_helper
cryptd
intel_ips
i2c_algo_bit
drm_kms_helper
psmouse
syscopyarea
sysfillrect
sysimgblt
fb_sys_fops
nvme
rtsx_pci
drm
wmi
i2c_hid
hid
pinctrl_sunrisepoint
pinctrl_intel
video
fjes




!!ALSA/HDA dmesg
!!--------------

```

I have been fumbling around with attempting to reinstall alsa however have no made any progress. Any help is much appreciated.

---

### Post by SuperFreak on 2017-01-13
Not sure if this helps but I had no sound with HDMI in Mint

I solved in this way:
sudo gedit /etc/pulse/default.pa
commented this line --> load-module module-switch-on-port-available
Saved
Switched my headphone jack from front-panel to back motherboard port and then reboot. Now it works fine.
[https://ubuntuforums.org/archive/index.php/t-2321631.html](https://ubuntuforums.org/archive/index.php/t-2321631.html)

---

### Post by flutterboy on 2017-03-15
Hi M.D.G.
Did you solve your problem?
I have the same issue with my xps13: Output Dummy in sound devices list with mint 18.1

Thanks

---

