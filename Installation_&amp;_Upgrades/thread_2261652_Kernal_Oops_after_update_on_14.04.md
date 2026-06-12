---
title: "Kernal Oops after update on 14.04"
date: 2015-01-20
forum: Installation &amp; Upgrades
---

### Post by mikenh on 2015-01-20
I have sporadic errors after updating two days ago. The most consistent are Firefox and Chrome crashes. 
Details in error message: Package 3.13.0-44 Generic 44.73 **** Bug: Bad Page State in Progress  oneconf-service pfn:117541 ***  Alsainfo  *** Apport 2.14.1 Oubuntu 3.6

After the update I had a Boot partition size warning and I used apt-get to remove 4 old kernals, but I got no warnings during that process.

Pre-gratitude.

---

### Post by mikenh on 2015-01-21
I executed the recommended repair option with boot repair as the problem persisted and I could find no solutions or advice. The crashes have stopped at least for the last 2 sessions.

 Now I can't run the Software Updater. It begins and the progress message says, 'configuring grub-pc' but then it goes dark and I have to force quit.  Anyone?

---

### Post by MAFoElffen on 2015-01-21
I guess if I could see what modules are loaded, we could try to match that to the error you say is being reported
```

Test1=$(awk '{ print $1 }' $(lsmod)) | modinfo $Test1 | tee ~/Test1.txt

```


What that does is it extracts a list of loaded kernel modules, pipe them info another utility to get info on each of those loaded modules and prints them to a file.

Attach that text file to a post.

---

### Post by mikenh on 2015-01-22
Couldn't get that command line to work. Usually get the error return: > modinfo: ERROR: missing module or filename.
The txt file was created it seems, but it had no content.
 I tried kmod and mod instead of modinfo, and adding sudo and changing to the root directory, but no luck.

When I entered lsmod by itself, it listed:

Module                  Size  Used by
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391136  10 bnep,rfcomm
binfmt_misc            17468  1 
snd_hda_codec_hdmi     46368  1 
usblp                  22891  0 
gpio_ich               13476  0 
snd_hda_codec_realtek    65580  1 
snd_hda_intel          56451  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
coretemp               13435  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
kvm_intel             143187  0 
kvm                   455835  1 kvm_intel
snd_timer              29482  2 snd_pcm,snd_seq
radeon               1522640  4 
serio_raw              13462  0 
lpc_ich                21080  0 
ttm                    85150  1 radeon
drm_kms_helper         55071  1 radeon
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mac_hid                13205  0 
drm                   303102  6 ttm,drm_kms_helper,radeon
soundcore              12680  1 snd
i2c_algo_bit           13413  1 radeon
parport_pc             32701  1 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid
firewire_ohci          40409  0 
firewire_core          68769  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
floppy                 69418  0 
r8169                  67581  0 
mii                    13934  1 r8169
ahci                   25819  3 
pata_jmicron           12758  0 
libahci                32716  1 ahci

---

