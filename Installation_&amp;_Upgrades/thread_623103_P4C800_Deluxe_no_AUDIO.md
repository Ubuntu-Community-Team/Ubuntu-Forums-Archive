---
title: "P4C800 Deluxe no AUDIO"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by Leopizzo on 2007-11-25
Hi all,

I have a "small" problem with my fresh Gutsy installation.
I simply can't hear any sound.
The device is correctly recognized, or at least it seems (82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller).
Device is correctly connected and working in Windows XP, with 4 speaker configuration.

I already tried all configurations in System->Preferences->Sound, but noone is working.
I also tried with alsamixer from terminal, and I already unchecked the Headphone jack sense.

Below you can find  some commands output I see tipically asked, just to speed up.


Thanks in advance

Leopizzo



lspci -n | grep `lspci | grep -i audio | awk '{print $1}'` 
00:1f.5 0401: 8086:24d5 (rev 02)

ls /proc/asound/
card0  cards    ICH5     oss  seq     UART
card1  devices  modules  pcm  timers  version

aplay -l
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: ICH5 [Intel ICH5], dispositivo 0: Intel ICH [Intel ICH5]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: ICH5 [Intel ICH5], dispositivo 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0


lsmod
Module                  Size  Used by
nls_cp437               6784  1 
isofs                  36412  1 
udf                    87204  0 
ipv6                  273892  10 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
button                  8976  0 
ac                      6148  0 
sbs                    19592  0 
container               5504  0 
dock                   10656  0 
video                  18060  0 
battery                11012  0 
af_packet              24840  4 
ndiswrapper           185240  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_mpu401              9640  0 
snd_mpu401_uart         9600  1 snd_mpu401
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               6221648  34 
usbhid                 29536  0 
hid                    28928  1 usbhid
usblp                  15104  0 
analog                 13344  0 
gameport               16776  1 analog
i2c_core               26112  1 nvidia
snd                    54660  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                  4224  0 
psmouse                39952  0 
soundcore               8800  1 snd
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
serio_raw               8068  0 
i82875p_edac            7172  0 
edac_mc                25808  1 i82875p_edac
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  1 
agpgart                35016  2 nvidia,intel_agp
evdev                  11136  3 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  4 
sr_mod                 17828  1 
cdrom                  37536  1 sr_mod
ata_generic             8452  0 
floppy                 60004  0 
ehci_hcd               36492  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
skge                   43152  0 
ata_piix               17540  4 
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  5 sbp2,sg,sd_mod,sr_mod,libata
uhci_hcd               26640  0 
usbcore               138632  6 ndiswrapper,usbhid,usblp,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor

---

