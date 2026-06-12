---
title: "pointer and keyboard freeze upon entering user session"
date: 2018-10-29
forum: Installation &amp; Upgrades
---

### Post by yazdzik-k on 2018-10-29
Dear friends,


Odd freeze.  At appearance of desktop,  pointer moves,  but beither touchpad nor keyboard input have any effect.  After about  30 seconds the pointer freezes in position. 
 (for the record, same issue with debian buster installer, ubuntu-mate,  debian buster live works fine.  I cannot run an xlog comparison,  of course,  since I cannot use the keyboard!)


Currently running 18.10, upgrade from 18.04 ubuntu,  running mate desktop  Libinput instead of synaptics due to configuration issues)


```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; USBest Technology SiS HID Touch Controller	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Elan Touchpad                           	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Asus Wireless Radio Control             	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=9	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=10	[slave  keyboard (3)]
    &#8627; USB2.0 HD UVC WebCam: USB2.0 HD         	id=12	[slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                        	id=14	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]

```


```

Module                  Size  Used by
msr                    16384  0
ccm                    20480  6
cmac                   16384  1
bnep                   20480  2
uvcvideo               98304  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
btusb                  45056  0
videobuf2_v4l2         24576  1 uvcvideo
btrtl                  16384  1 btusb
videobuf2_common       45056  2 videobuf2_v4l2,uvcvideo
btbcm                  16384  1 btusb
btintel                20480  1 btusb
videodev              188416  3 videobuf2_v4l2,uvcvideo,videobuf2_common
bluetooth             548864  26 btrtl,btintel,btbcm,bnep,btusb
media                  40960  2 videodev,uvcvideo
hid_multitouch         20480  0
ecdh_generic           24576  2 bluetooth
joydev                 20480  0
snd_hda_codec_hdmi     49152  1
nls_iso8859_1          16384  1
snd_hda_codec_realtek   106496  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
nvidia_uvm            786432  0
nvidia_drm             40960  2
nvidia_modeset       1110016  3 nvidia_drm
arc4                   16384  2
intel_rapl             20480  0
nvidia              14368768  198 nvidia_uvm,nvidia_modeset
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
asus_nb_wmi            28672  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
intel_wmi_thunderbolt    16384  0
mxm_wmi                16384  0
snd_hda_intel          40960  3
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           16384  0
iwlmvm                368640  0
coretemp               16384  0
mac80211              794624  1 iwlmvm
snd_seq_midi_event     16384  1 snd_seq_midi
i915                 1740800  3
snd_rawmidi            32768  1 snd_seq_midi
kvm                   622592  0
irqbypass              16384  1 kvm
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
ghash_clmulni_intel    16384  0
iwlwifi               294912  1 iwlmvm
cryptd                 24576  1 ghash_clmulni_intel
drm_kms_helper        172032  2 nvidia_drm,i915
input_leds             16384  0
intel_cstate           20480  0
snd_timer              32768  2 snd_seq,snd_pcm
intel_rapl_perf        16384  0
serio_raw              16384  0
mei_me                 40960  0
drm                   458752  6 drm_kms_helper,nvidia_drm,i915
cfg80211              663552  3 iwlmvm,iwlwifi,mac80211
ipmi_devintf           20480  0
snd                    81920  17 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
ipmi_msghandler       102400  2 ipmi_devintf,nvidia
i2c_algo_bit           16384  1 i915
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
mei                    98304  1 mei_me
sysimgblt              16384  1 drm_kms_helper
idma64                 20480  0
soundcore              16384  1 snd
processor_thermal_device    16384  0
virt_dma               16384  1 idma64
intel_pch_thermal      16384  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
elan_i2c               36864  0
int3400_thermal        16384  0
mac_hid                16384  0
int3403_thermal        16384  0
acpi_thermal_rel       16384  1 int3400_thermal
int340x_thermal_zone    16384  2 int3403_thermal,processor_thermal_device
wmi                    24576  3 intel_wmi_thunderbolt,asus_wmi,mxm_wmi
acpi_pad              180224  0
video                  45056  2 asus_wmi,i915
asus_wireless          16384  0
sch_fq_codel           20480  5
cuse                   16384  3
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              24576  0
x_tables               40960  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
nvme                   32768  2
ahci                   40960  0
nvme_core              81920  4 nvme
intel_lpss_pci         20480  0
i2c_hid                20480  0
libahci                32768  1 ahci
intel_lpss             16384  1 intel_lpss_pci
hid                   126976  4 i2c_hid,usbhid,hid_multitouch,hid_generic

```


```

00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Host Bridge/DRAM Registers (rev 07)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 530 (rev 06)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 07)
00:14.0 USB controller: Intel Corporation 100 Series/C230 Series Chipset Family USB 3.0 xHCI Controller (rev 31)
00:14.2 Signal processing controller: Intel Corporation 100 Series/C230 Series Chipset Family Thermal Subsystem (rev 31)
00:15.0 Signal processing controller: Intel Corporation 100 Series/C230 Series Chipset Family Serial IO I2C Controller #0 (rev 31)
00:15.1 Signal processing controller: Intel Corporation 100 Series/C230 Series Chipset Family Serial IO I2C Controller #1 (rev 31)
00:16.0 Communication controller: Intel Corporation 100 Series/C230 Series Chipset Family MEI Controller #1 (rev 31)
00:17.0 SATA controller: Intel Corporation HM170/QM170 Chipset SATA Controller [AHCI Mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #2 (rev f1)
00:1c.2 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #3 (rev f1)
00:1c.4 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #5 (rev f1)
00:1d.0 PCI bridge: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #9 (rev f1)
00:1f.0 ISA bridge: Intel Corporation HM170 Chipset LPC/eSPI Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation 100 Series/C230 Series Chipset Family Power Management Controller (rev 31)
00:1f.3 Audio device: Intel Corporation 100 Series/C230 Series Chipset Family HD Audio Controller (rev 31)
00:1f.4 SMBus: Intel Corporation 100 Series/C230 Series Chipset Family SMBus (rev 31)
01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 960M] (rev a2)
02:00.0 Unassigned class [ff00]: Alcor Micro Device 6621
03:00.0 Network controller: Intel Corporation Wireless 7265 (rev 59)
3d:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller SM951/PM951 (rev 01)

```


Since 18.10 works flawlessly, after a bit of massaging,  but is an upgrade stemming all the way back to 15.10,  on notoriously cranky asus ux501v,  the inability to install 18.10 fresh is not truly unexpected,  but I would like to try a fresh install for obvious reasons.   


Also, personally, the need to keep evolution dead current,  to avoid the eternal google token issue,  prompts the set of what would otherwise be pointless upgrades.  (used it since Ximian days.......)


Thank you very much for all the work and help.




Best,
M

---

