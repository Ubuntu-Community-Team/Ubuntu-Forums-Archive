---
title: "does not detect hard drive"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by Alex Gadhus on 2008-09-06
Hi folks!

I tried to install the latest Ubuntu on my old desktop computer (from around 1999). During the installation process I got the error-message: no disk drive detected. I would then have to choose from a list of drivers. I have no idea which one would work.
My Disk Controller is an Intel 82801BA Ultra ATA Storage controller – 244B.
I tried to google to find the driver which would work without success.
I also tried a driver "genericIDE" or something
Could anyone please help me with this issue?
I am completely new to Linux, so please be patient.

My machine is an Intel Pentium III with 384 MB RAM and 2 Maxtor disks with each about 20 GBs.
Is there any chance at all to make that machine running? Is it too old?

Thanks for your help and a nice Sunday,

Alexander
PS: I tried to install Opensuse 11 with the same result...

---

### Post by Alex Gadhus on 2008-09-07
Hi Folks again!

I did a lsmod command with kanotix. Then I tried to install Ubuntu with the alternate cd. Then I get stuck with the error: cannot find disk driver. I get a whole list of drivers. I hoped one of the lsmod list would match the ubuntu proposal. But I did not find any (although I admit that I did not try out every driver). Does anyone of you know from the list below which driver I have to use. Or where can I find a driver for

Intel 82801BA Ultra ATA Storage controller – 244B

?

Thanks, Folks!

Alexander


radeon                125216  2
drm                    81684  3 radeon
af_packet              23812  2
cryptoloop              4224  0
aes_i586               34560  0
aes_generic            29120  0
geode_aes               7048  0
blkcipher               8196  1 geode_aes
dm_mod                 62660  0
fuse                   50708  0
joydev                 12992  0
pcmcia                 41132  0
yenta_socket           27532  0
rsrc_nonstatic         13824  1 yenta_socket
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_emu10k1_synth       8064  0
snd_emux_synth         35840  1 snd_emu10k1_synth
snd_seq_virmidi         7936  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           140448  2 snd_emu10k1_synth
snd_seq_dummy           4612  0
snd_seq_oss            33152  0
snd_seq_midi            9472  0
snd_seq_midi_event      8320  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                53488  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq
_oss,snd_seq_midi,snd_seq_midi_event
snd_rawmidi            25600  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_ac97_codec        101156  1 snd_emu10k1
ac97_bus                2944  1 snd_ac97_codec
snd_pcm_oss            42752  0
snd_mixer_oss          17536  1 snd_pcm_oss
snd_pcm                80132  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_seq_device          9228  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss
,snd_seq_midi,snd_seq,snd_rawmidi
snd_timer              24452  3 snd_emu10k1,snd_seq,snd_pcm
snd_page_alloc         11272  2 snd_emu10k1,snd_pcm
snd_util_mem            5632  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10116  2 snd_emux_synth,snd_emu10k1
snd                    54532  15 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_seq_oss,snd_seq,snd_ra
wmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
emu10k1_gp              4608  0
serio_raw               7812  0
floppy                 60228  0
e100                   37772  0
mii                     6400  1 e100
soundcore               8672  1 snd
gameport               16648  2 emu10k1_gp
i2c_i801               10640  0
pcspkr                  4096  0
evdev                  12800  1
psmouse                40464  0
iTCO_wdt               13092  0
i2c_core               24960  1 i2c_i801
iTCO_vendor_support     4740  1 iTCO_wdt
intel_agp              25492  1
agpgart                34888  2 drm,intel_agp
shpchp                 34708  0
pci_hotplug            31008  1 shpchp
squashfs               47624  1
loop                   18948  3 cryptoloop
usb_storage            73408  0
libusual               18980  1 usb_storage
sg                     36880  0
uhci_hcd               27024  0
ehci_hcd               37516  0
usbcore               146668  5 usb_storage,libusual,uhci_hcd,ehci_hcd

---

