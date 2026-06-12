---
title: "disable touchpad while typing"
date: 2017-10-24
forum: Installation &amp; Upgrades
---

### Post by yazdzik-k on 2017-10-24
Dear friends,


Surprisingly,  the upgrade from 17.04 to 17.10 produced only one or two issues,  other than the woeful unconfigurability of Gnome.


I am left at GDM with only two choices,  Ubuntu on XOrg and Unity.   Unity works perfectly,  as always,  nothing has changed,  other than the the personalation issues that result from gnome and unity living together.


The serious issue is that typing,  I have the unbearably return of the jumping cursor issue,  that is to say,  serious typing in the gnome desktop is impossible,  while in Unity,  it is fine.


I have set up a hotkey to enable and disable the xinput as a kludge,  as none of the gui settings do anything about it,  for some reason,  neither tweaks nor settings.


(I would use Mate but need real HiDPI support.....)


The only related thing I see is that the FN plus F9,  which disables touchpad,  works in Unity,  not Gnome,  although in Unity I do not need it as the issue does not exist.
```

Module                  Size  Used by
ccm                    20480  9
rfcomm                 77824  2
snd_hrtimer            16384  1
bbswitch               16384  0
cmac                   16384  1
bnep                   20480  2
binfmt_misc            20480  1
nls_iso8859_1          16384  1
joydev                 20480  0
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
hid_multitouch         20480  0
videodev              176128  3 uvcvideo,videobuf2_core,videobuf2_v4l2
usbhid                 49152  0
media                  40960  2 uvcvideo,videodev
arc4                   16384  2
btusb                  45056  0
btrtl                  16384  1 btusb
snd_hda_codec_hdmi     49152  1
asus_nb_wmi            28672  0
snd_hda_codec_realtek    94208  1
asus_wmi               28672  1 asus_nb_wmi
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  0
iwlmvm                385024  0
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
snd_hda_intel          40960  6
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
coretemp               16384  0
mac80211              778240  1 iwlmvm
kvm                   581632  0
snd_pcm                98304  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
snd_seq_midi           16384  0
crc32_pclmul           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
iwlwifi               249856  1 iwlmvm
ghash_clmulni_intel    16384  0
cryptd                 24576  1 ghash_clmulni_intel
snd_rawmidi            32768  1 snd_seq_midi
intel_cstate           20480  0
intel_rapl_perf        16384  0
cfg80211              610304  3 iwlmvm,iwlwifi,mac80211
snd_seq                65536  3 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
input_leds             16384  0
snd_timer              32768  3 snd_seq,snd_hrtimer,snd_pcm
serio_raw              16384  0
snd                    81920  24 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
nvidia_uvm            663552  0
soundcore              16384  1 snd
hci_uart              106496  0
idma64                 20480  0
btbcm                  16384  2 hci_uart,btusb
virt_dma               16384  1 idma64
mei_me                 40960  0
serdev                 20480  1 hci_uart
mei                    98304  1 mei_me
btqca                  16384  1 hci_uart
processor_thermal_device    16384  0
btintel                16384  2 hci_uart,btusb
intel_pch_thermal      16384  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
shpchp                 36864  0
intel_lpss_pci         20480  0
elan_i2c               36864  0
int3403_thermal        16384  0
bluetooth             540672  33 btrtl,hci_uart,btintel,btqca,bnep,btbcm,rfcomm,btusb
ecdh_generic           24576  1 bluetooth
wmi                    24576  2 asus_wmi,mxm_wmi
intel_lpss_acpi        16384  0
intel_lpss             16384  2 intel_lpss_pci,intel_lpss_acpi
int3406_thermal        16384  0
int3402_thermal        16384  0
int340x_thermal_zone    16384  3 int3402_thermal,int3403_thermal,processor_thermal_device
tpm_crb                16384  0
int3400_thermal        16384  0
asus_wireless          16384  0
acpi_thermal_rel       16384  1 int3400_thermal
mac_hid                16384  0
acpi_pad              180224  0
cuse                   16384  3
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  0
x_tables               40960  1 ip_tables
autofs4                40960  2
i915                 1798144  6
nvidia_drm             45056  7
nvidia_modeset        843776  5 nvidia_drm
nvidia              13004800  388 nvidia_modeset,nvidia_uvm
i2c_algo_bit           16384  1 i915
drm_kms_helper        167936  2 i915,nvidia_drm
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
ahci                   36864  0
fb_sys_fops            16384  1 drm_kms_helper
nvme                   32768  2
nvme_core              53248  4 nvme
drm                   356352  13 i915,nvidia_drm,drm_kms_helper
libahci                32768  1 ahci
i2c_hid                20480  0
hid                   118784  3 i2c_hid,usbhid,hid_multitouch
pinctrl_sunrisepoint    28672  0
video                  40960  3 asus_wmi,int3406_thermal,i915
pinctrl_intel          20480  1 pinctrl_sunrisepoint

```

This provides me with no clue as to why the two desktops behave differently.  Any ideas?  

Best,

Martin

---

