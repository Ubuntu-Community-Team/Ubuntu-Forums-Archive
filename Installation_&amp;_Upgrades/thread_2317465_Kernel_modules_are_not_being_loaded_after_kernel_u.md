---
title: "Kernel modules are not being loaded after kernel upgrade"
date: 2016-03-16
forum: Installation &amp; Upgrades
---

### Post by petwri on 2016-03-16
I installed a driver for a DVB-S tuner, which gets loaded just fine on every boot. lspci -v shows the device with the correct kernel driver in use. However, after every dist-upgrade, where the kernel gets upgraded, the kernel driver is no longer loaded. How can I achieve that?

---

### Post by deadflowr on 2016-03-16
How's it being added?

---

### Post by petwri on 2016-03-16
I installed it with a make install. To be precise, it is this one: [http://www.tbsdtv.com/download/document/common/tbs-linux-drivers_v160219.zip](http://www.tbsdtv.com/download/document/common/tbs-linux-drivers_v160219.zip)

After building and installing it, it gets automatically loaded, until i do a kernel upgrade.

---

### Post by ajgreeny on 2016-03-16
Do you have the **dkms** package installed?  If not, and I am not sure that it is default in all versions of *ubuntu, install it and you may find the module is loaded automatically even after an update.

---

### Post by petwri on 2016-03-17
> **ajgreeny said:**
> Do you have the **dkms** package installed?  If not, and I am not sure that it is default in all versions of *ubuntu, install it and you may find the module is loaded automatically even after an update.

Thanks! Will try asap. I for sure have not installed dkms by hand. I expected such a thing to be already installed in a standard ubuntu.

---

### Post by petwri on 2016-04-20
Ok, I installed dkms, it worked for some time, but the driver now vanished again. When the device worked, I got something like this:

```

main@htpc:~$ lspci -v
01:00.0Multimedia controller: Philips Semiconductors SAA7160 (rev 03)
   Subsystem: Device 6928:0002
   Flags: bus master, fast devsel, latency 0, IRQ 16
   Memory at df200000 (64-bit, non-prefetchable) [size=1M]
   Capabilities: <access denied>
   Kernel driver in use: SAA716x TBS

```

Now, the entry is

```

main@htpc:~$ lspci -v
01:00.0Multimedia controller: Philips Semiconductors SAA7160 (rev 03)
   Subsystem: Device 6928:0002
   Flags: bus master, fast devsel, latency 0, IRQ 16
   Memory at df200000 (64-bit, non-prefetchable) [size=1M]
   Capabilities: <access denied>

```

The driver just seems to have disappeared.

```

main@htpc:~$ lsmod
Module                  Size  Used by
rfcomm                 69632  0
rc_dib0700_rc5         16384  0
dib7000p               36864  1
dvb_usb_dib0700       147456  2
dib7000m               24576  1 dvb_usb_dib0700
dib0090                40960  1 dvb_usb_dib0700
dib0070                20480  2 dvb_usb_dib0700
dib3000mc              20480  1 dvb_usb_dib0700
dibx000_common         20480  4 dvb_usb_dib0700,dib3000mc,dib7000m,dib7000p
dvb_usb                24576  1 dvb_usb_dib0700
dvb_core              122880  2 dvb_usb,dib7000p
rc_core                28672  4 dvb_usb,dvb_usb_dib0700,rc_dib0700_rc5
bnep                   20480  2
binfmt_misc            20480  1
snd_hda_codec_hdmi     49152  1
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
arc4                   16384  2
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_hda_intel          36864  1
kvm_intel             167936  0
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
kvm                   516096  1 kvm_intel
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
crct10dif_pclmul       16384  0
snd_seq_midi           16384  0
crc32_pclmul           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
iwlmvm                294912  0
cryptd                 20480  2 aesni_intel,ablk_helper
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
mac80211              745472  1 iwlmvm
serio_raw              16384  0
snd                    81920  13 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
iwlwifi               204800  1 iwlmvm
soundcore              16384  1 snd
cfg80211              557056  3 iwlwifi,mac80211,iwlmvm
joydev                 20480  0
input_leds             16384  0
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             516096  27 bnep,btbcm,btrtl,btusb,rfcomm,btintel
mei_me                 36864  0
shpchp                 36864  0
mei                    98304  1 mei_me
acpi_als               16384  0
mac_hid                16384  0
kfifo_buf              16384  1 acpi_als
intel_lpss_acpi        16384  0
intel_lpss             16384  1 intel_lpss_acpi
acpi_pad               20480  0
tpm_infineon           20480  0
industrialio           65536  2 acpi_als,kfifo_buf
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
raid10                 49152  0
raid1                  36864  0
raid0                  20480  0
multipath              16384  0
linear                 16384  0
raid456                98304  1
async_raid6_recov      20480  1 raid456
async_memcpy           16384  2 raid456,async_raid6_recov
async_pq               16384  2 raid456,async_raid6_recov
async_xor              16384  3 async_pq,raid456,async_raid6_recov
async_tx               16384  5 async_pq,raid456,async_xor,async_memcpy,async_raid6_recov
hid_logitech_hidpp     20480  0
xor                    24576  1 async_xor
hid_logitech_dj        20480  0
usbhid                 49152  0
raid6_pq              102400  3 async_pq,raid456,async_raid6_recov
uas                    24576  0
usb_storage            69632  1 uas
i915                 1134592  9
psmouse               126976  0
e1000e                237568  0
ahci                   36864  5
drm_kms_helper        131072  1 i915
igb                   188416  0
drm                   356352  10 i915,drm_kms_helper
dca                    16384  1 igb
ptp                    20480  2 igb,e1000e
libahci                32768  1 ahci
pps_core               20480  1 ptp
i2c_algo_bit           16384  2 igb,i915
wmi                    20480  0
pinctrl_sunrisepoint    28672  0
video                  40960  1 i915
pinctrl_intel          20480  1 pinctrl_sunrisepoint
i2c_hid                20480  0
hid                   118784  6 i2c_hid,hid_generic,usbhid,hid_logitech_dj,hid_logitech_hidpp


```

Ideas?

---

