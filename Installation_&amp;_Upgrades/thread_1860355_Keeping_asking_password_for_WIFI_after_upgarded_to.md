---
title: "Keeping asking password for WIFI after upgarded to 11.10"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by fei on 2011-10-14
Just upgrade from 11.04 to 11.10. Everything works fine except the wifi. The system keeps asking me password even though I type the correct password. The wifi network worked fine on 11.04. Any idea what caused this problem?

The wifi hardware is RT2860. I compared the loaded kernel modules in kernel 3.0 (ubuntu 11.10) and in kernel 2.6.38 (ubuntu 11.04). It seems the same modules are loaded. However the wifi is not working anymore. Weired :(

Below is a list of the loaded modules in kernel 3.0 (ubuntu 11.10)

```

Module                  Size  Used by
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61475  1 vfat
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  1 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
usb_storage            57901  0 
uas                    18027  0 
joydev                 17693  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
usbhid                 47198  0 
hid                    95463  1 usbhid
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12529  2 
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13166  0 
rt2800pci              18715  0 
rt2800lib              54306  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14578  1 rt2800pci
rt2x00lib              50325  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              310872  3 rt2800lib,rt2x00pci,rt2x00lib
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i915                  566711  3 
cfg80211              199587  2 rt2x00lib,mac80211
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
mei                    41480  0 
i2c_algo_bit           13423  1 i915
eeprom_93cx6           12725  1 rt2800pci
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
xhci_hcd               78641  0 
r8169                  52788  0 
ahci                   26002  0 
libahci                26861  1 ahci

```

---

### Post by filiatra on 2011-10-15
Hello,

same problem here. After some search I saw that one should blacklist rt2800, rt2x00. But I cannot find the right module, rt2860, that used to exist before in the kernel.

see also
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/874289](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/874289)

---

