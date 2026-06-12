---
title: "No audio card detected on Ubuntu 19.10"
date: 2019-12-19
forum: Installation &amp; Upgrades
---

### Post by mono-love on 2019-12-19
Hello 

Kindly I can't play any video or record a music in Ubuntu 19.10



```
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Fri Dec 20 01:47:10 UTC 2019


!!Linux Distribution
!!------------------

Ubuntu 19.10 n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 19.10" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 19.10" HOME_URL="https://www.ubuntu.com/" SUPPORT_URL="https://help.ubuntu.com/" BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/" PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy" UBUNTU_CODENAME=eoan


!!DMI Information
!!---------------

Manufacturer:      HP
Product Name:      HP EliteBook 840 G6
Product Version:   
Firmware Version:  R70 Ver. 01.02.00
Board Vendor:      HP
Board Name:        8549


!!ACPI Device Status Information
!!---------------

/sys/bus/acpi/devices/HPIC000C:00/status 	 15
/sys/bus/acpi/devices/IFX0785:00/status 	 15
/sys/bus/acpi/devices/INT3400:00/status 	 15
/sys/bus/acpi/devices/INT3403:00/status 	 15
/sys/bus/acpi/devices/INT3403:01/status 	 15
/sys/bus/acpi/devices/INT340E:00/status 	 15
/sys/bus/acpi/devices/INT34BB:00/status 	 15
/sys/bus/acpi/devices/INT3F0D:00/status 	 15
/sys/bus/acpi/devices/LNXPOWER:00/status 	 15
/sys/bus/acpi/devices/LNXPOWER:02/status 	 1
/sys/bus/acpi/devices/LNXPOWER:03/status 	 1
/sys/bus/acpi/devices/LNXPOWER:04/status 	 1
/sys/bus/acpi/devices/LNXPOWER:05/status 	 1
/sys/bus/acpi/devices/LNXPOWER:06/status 	 1
/sys/bus/acpi/devices/LNXPOWER:07/status 	 1
/sys/bus/acpi/devices/PNP0103:00/status 	 15
/sys/bus/acpi/devices/PNP0B00:00/status 	 15
/sys/bus/acpi/devices/PNP0C02:00/status 	 3
/sys/bus/acpi/devices/PNP0C02:01/status 	 3
/sys/bus/acpi/devices/PNP0C02:05/status 	 3
/sys/bus/acpi/devices/PNP0C09:00/status 	 15
/sys/bus/acpi/devices/PNP0C0A:00/status 	 31
/sys/bus/acpi/devices/PNP0C0C:00/status 	 11
/sys/bus/acpi/devices/PRP00001:00/status 	 11
/sys/bus/acpi/devices/SYNA3091:00/status 	 15
/sys/bus/acpi/devices/USBC000:00/status 	 15
/sys/bus/acpi/devices/device:04/status 	 15
/sys/bus/acpi/devices/device:27/status 	 15
/sys/bus/acpi/devices/device:28/status 	 15


!!Kernel Information
!!------------------

Kernel release:    5.3.0-24-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.1.9
Utilities version:  1.1.9


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

00:1f.3 Multimedia audio controller: Intel Corporation Cannon Point-LP High Definition Audio Controller (rev 11)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

	Prefetchable memory behind bridge: 0000004000000000-0000004021ffffff [size=544M]
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort  <SERR- <PERR-
--
00:1f.3 0401: 8086:9dc8 (rev 11)
	Subsystem: 103c:8549
--
	Prefetchable memory behind bridge: 0000004000000000-0000004021ffffff [size=544M]
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
--
	Prefetchable memory behind bridge: 0000004000000000-0000004021ffffff [size=544M]
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-


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



!!Aplay/Arecord output
!!--------------------

APLAY

aplay: device_list:272: no soundcards found...

ARECORD

arecord: device_list:272: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!--------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
rfcomm
ccm
cmac
bnep
uvcvideo
videobuf2_vmalloc
btusb
videobuf2_memops
btrtl
videobuf2_v4l2
btbcm
videobuf2_common
btintel
bluetooth
videodev
mc
cdc_ether
usbnet
ecdh_generic
mii
ecc
x86_pkg_temp_thermal
intel_powerclamp
coretemp
kvm_intel
kvm
irqbypass
joydev
nls_iso8859_1
crct10dif_pclmul
crc32_pclmul
ghash_clmulni_intel
mei_hdcp
iwlmvm
intel_rapl_msr
mac80211
libarc4
i915
aesni_intel
iwlwifi
drm_kms_helper
hid_sensor_als
aes_x86_64
hid_sensor_trigger
crypto_simd
drm
industrialio_triggered_buffer
cryptd
kfifo_buf
glue_helper
processor_thermal_device
intel_cstate
hid_sensor_iio_common
intel_rapl_perf
industrialio
mei_me
i2c_algo_bit
input_leds
hp_wmi
intel_rapl_common
intel_wmi_thunderbolt
sparse_keymap
serio_raw
wmi_bmof
intel_soc_dts_iosf
cfg80211
mei
fb_sys_fops
syscopyarea
idma64
ucsi_acpi
cros_ec_ishtp
sysfillrect
virt_dma
cros_ec_core
typec_ucsi
sysimgblt
intel_pch_thermal
typec
int3403_thermal
int340x_thermal_zone
mac_hid
int3400_thermal
acpi_thermal_rel
acpi_pad
sch_fq_codel
parport_pc
ppdev
lp
parport
ip_tables
x_tables
autofs4
hid_sensor_hub
hid_generic
intel_ishtp_loader
intel_ishtp_hid
nvme
psmouse
e1000e
nvme_core
intel_ish_ipc
thunderbolt
i2c_i801
intel_ishtp
intel_lpss_pci
i2c_hid
intel_lpss
hid
wmi
pinctrl_cannonlake
video
pinctrl_intel


!!ALSA/HDA dmesg
!!--------------

[    0.290393] ACPI: Added _OSI(Linux-Dell-Video)
[    0.290394] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.290395] ACPI: Added _OSI(Linux-HPI-Hybrid-Graphics)
--
[    2.909481] sof_pci_dev: Unknown symbol tng_chip_info (err -2)
[    2.909485] sof_pci_dev: Unknown symbol snd_sof_runtime_idle (err -2)
[    2.909491] sof_pci_dev: Unknown symbol sof_cnl_ops (err -2)
[    2.909496] sof_pci_dev: Unknown symbol snd_sof_runtime_resume (err -2)
[    2.909500] sof_pci_dev: Unknown symbol snd_soc_acpi_intel_bxt_machines (err -2)
[    2.909507] sof_pci_dev: Unknown symbol apl_chip_info (err -2)
[    2.909511] sof_pci_dev: Unknown symbol snd_soc_acpi_find_machine (err -2)
[    2.909516] sof_pci_dev: Unknown symbol snd_sof_device_remove (err -2)
[    2.909521] sof_pci_dev: Unknown symbol snd_soc_acpi_intel_glk_machines (err -2)
[    2.909526] sof_pci_dev: Unknown symbol snd_sof_runtime_suspend (err -2)
[    2.909531] sof_pci_dev: Unknown symbol snd_sof_resume (err -2)
[    2.909546] sof_pci_dev: Unknown symbol cnl_chip_info (err -2)
[    2.909551] sof_pci_dev: Unknown symbol snd_soc_acpi_intel_icl_machines (err -2)
[    2.909557] sof_pci_dev: Unknown symbol sof_tng_ops (err -2)
[    2.909561] sof_pci_dev: Unknown symbol snd_sof_device_probe (err -2)
[    2.909567] sof_pci_dev: Unknown symbol snd_soc_acpi_intel_cnl_machines (err -2)
[    2.909571] sof_pci_dev: Unknown symbol snd_sof_suspend (err -2)
[    2.909577] sof_pci_dev: Unknown symbol sof_apl_ops (err -2) 
```
I would appreciate if someone can help me

---

