---
title: "Wifi doesn't work after kernel update"
date: 2018-01-06
forum: MINT
---

### Post by hippo1685 on 2018-01-06
Hello!

I recently updated kernel to [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14.11/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14.11/), after that operation my wifi stopped working (there is no wlan0 interface)

I'm using **linux mint 17.3** which is based on [B]ubuntu 14.04

[/B]My system is 64 bit

Previous kerenl was: 3.19.0-32-generic newest is: 4.14.11-041411-generic

lshw output:

```
*-network UNCLAIMED
             description: Network controller
             product: BCM43142 802.11b/g/n
             vendor: Broadcom Corporation
             physical id: 0
             bus info: pci@0000:06:00.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress cap_list
             configuration: latency=0
             resources: memory:f7900000-f7907fff
```

iwconfig output:

```
eth0      no wireless extensions.

lo        no wireless extensions.
```

lsmod output:

```
Module                  Size  Used by
pci_stub               16384  1 
vboxpci                28672  0 
vboxnetadp             28672  0 
vboxnetflt             32768  0 
vboxdrv               507904  3 vboxnetadp,vboxnetflt,vboxpci
cmac                   16384  1 
rfcomm                 86016  12 
bnep                   24576  2 
binfmt_misc            20480  1 
jfs                   217088  1 
nls_iso8859_1          16384  1 
joydev                 24576  0 
hid_rmi                20480  0 
uvcvideo              102400  0 
rmi_core               86016  1 hid_rmi
videobuf2_vmalloc      16384  2 uvcvideo,rmi_core
btusb                  53248  0 
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
cmdlinepart            16384  0 
videobuf2_memops       16384  1 videobuf2_vmalloc
bluetooth             626688  25 btrtl,btintel,bnep,btbcm,rfcomm,btusb
ecdh_generic           24576  1 bluetooth
rtsx_usb_ms            20480  0 
memstick               16384  1 rtsx_usb_ms
intel_spi_platform     16384  0 
intel_rapl             24576  0 
x86_pkg_temp_thermal    16384  0 
intel_spi              16384  1 intel_spi_platform
videobuf2_v4l2         28672  2 uvcvideo,rmi_core
intel_powerclamp       16384  0 
videobuf2_core         40960  3 uvcvideo,videobuf2_v4l2,rmi_core
mxm_wmi                16384  0 
spi_nor                36864  1 intel_spi
dell_wmi               16384  0 
videodev              204800  4 uvcvideo,videobuf2_core,videobuf2_v4l2,rmi_core
wmi_bmof               16384  0 
coretemp               16384  0 
media                  45056  2 uvcvideo,videodev
mtd                    69632  4 spi_nor,intel_spi,cmdlinepart
sparse_keymap          16384  1 dell_wmi
kvm_intel             229376  0 
kvm                   696320  1 kvm_intel
irqbypass              16384  1 kvm
dell_laptop            24576  0 
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
snd_hda_codec_realtek   102400  1 
snd_hda_codec_hdmi     57344  1 
snd_hda_codec_generic    86016  1 snd_hda_codec_realtek
dell_smbios            16384  2 dell_wmi,dell_laptop
snd_hda_intel          45056  5 
snd_hda_codec         151552  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           90112  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              16384  1 snd_hda_codec
snd_soc_rt5640        118784  0 
dcdbas                 16384  1 dell_smbios
ghash_clmulni_intel    16384  0 
dell_smm_hwmon         16384  0 
pcbc                   16384  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          266240  1 snd_soc_rt5640
snd_compress           24576  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
aesni_intel           188416  2 
snd_pcm               118784  7 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_core,snd_soc_rt5640,snd_hda_codec_hdmi,snd_soc_core
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 28672  3 crypto_simd,ghash_clmulni_intel,aesni_intel
snd_rawmidi            36864  1 snd_seq_midi
snd_seq                81920  2 snd_seq_midi_event,snd_seq_midi
input_leds             16384  0 
intel_cstate           20480  0 
dm_multipath           36864  0 
intel_rapl_perf        16384  0 
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
serio_raw              16384  0 
snd_timer              36864  2 snd_seq,snd_pcm
snd                    94208  23 snd_compress,snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_soc_core,snd_pcm
elan_i2c               45056  0 
soundcore              16384  1 snd
snd_soc_sst_acpi       16384  0 
shpchp                 40960  0 
snd_soc_sst_match      16384  1 snd_soc_sst_acpi
wmi                    28672  3 dell_wmi,wmi_bmof,mxm_wmi
spi_pxa2xx_platform    28672  0 
dw_dmac                16384  0 
dw_dmac_core           28672  1 dw_dmac
8250_dw                16384  0 
lpc_ich                28672  0 
mac_hid                16384  0 
mei_me                 45056  0 
dell_rbtn              16384  0 
mei                   114688  1 mei_me
i2c_hid                24576  0 
parport_pc             36864  0 
ppdev                  20480  0 
lp                     20480  0 
parport                57344  3 lp,parport_pc,ppdev
dm_mirror              28672  0 
dm_region_hash         16384  1 dm_mirror
dm_log                 20480  2 dm_mirror,dm_region_hash
rtsx_usb_sdmmc         32768  0 
rtsx_usb               20480  2 rtsx_usb_sdmmc,rtsx_usb_ms
hid_generic            16384  0 
usbhid                 57344  0 
hid                   126976  4 i2c_hid,hid_generic,usbhid,hid_rmi
i915                 1888256  3 
i2c_algo_bit           16384  1 i915
drm_kms_helper        204800  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   438272  4 i915,drm_kms_helper
ahci                   40960  4 
libahci                40960  1 ahci
r8169                  90112  0 
mii                    16384  1 r8169
sdhci_acpi             16384  0 
video                  45056  3 dell_wmi,dell_laptop,i915
sdhci                  53248  1 sdhci_acpi
```



I tried to install many "compatible" drivers but result was:
 doesn't work / wl module is missing / CFG80211 API is missing
(I was autoremove'ing with --purge flag when I tried to reinstall one by one but maybe I screwed something up)

I got similar issue with graphic card driver (i uninstaled nvidia X server then instaled normal driver but still it's UNCLAIMED).There is a list of all UNCLAIMED hardware:

```
*-display UNCLAIMED
             description: 3D controller
             product: GM108M [GeForce 840M]
             vendor: NVIDIA Corporation
             physical id: 0
             bus info: pci@0000:08:00.0
             version: a2
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: latency=0
             resources: memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:d000(size=128) memory:f7000000-f707ffff

*-serial UNCLAIMED
          description: SMBus
          product: 8 Series SMBus Controller
          vendor: Intel Corporation
          physical id: 1f.3
          bus info: pci@0000:00:1f.3
          version: 04
          width: 64 bits
          clock: 33MHz
          configuration: latency=0
          resources: memory:f7a19000-f7a190ff ioport:f040(size=32)
```

I'm opened for all suggestions!

---

### Post by chili555 on 2018-01-06
Is this helpful? [https://askubuntu.com/questions/992543/wifi-issues-on-17-10-kernel-package-linux-headers-4-14-11-041411-generic-is-no](https://askubuntu.com/questions/992543/wifi-issues-on-17-10-kernel-package-linux-headers-4-14-11-041411-generic-is-no)

---

### Post by hippo1685 on 2018-01-07
Yes! This is it!      ```
Building initial module for 4.14.11-041411-generic  Error! Bad return status for module build on kernel: 4.14.11-041411-generic (x86_64)  Consult /var/lib/dkms/bcmwl/6.30.223.248+bdcom/build/make.log for more information.  modprobe: FATAL: Module wl not found. update-initramfs: deferring update (trigger activated)
```     But linux-generic for my distro is 3.13.0-137-generic, there is any way to have at least 4.11 (actually is all about Kernel Page Table Isolation)?

---

### Post by chili555 on 2018-01-07
I don't know what's available for Mint. However, it is quite clear that the Ubuntu developers make certain that bcmwl-kernel-source works as expected with official kernels. This is not an official kernel, it is experimental.> 4.14.11-041411-genericI assume you need to install a later Mint version. I believe this may be useful: [https://askubuntu.com/questions/517136/list-of-ubuntu-versions-with-corresponding-linux-kernel-version](https://askubuntu.com/questions/517136/list-of-ubuntu-versions-with-corresponding-linux-kernel-version)

---

### Post by jeremy31 on 2018-01-07
*Thread moved to **MINT**.*

---

