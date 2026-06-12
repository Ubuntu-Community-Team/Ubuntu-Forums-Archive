---
title: "Gutsy update broke sound on gateway laptop"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by yoblin on 2007-11-28
I recently updated from feisty to gutsy on my gateway ML3109 and now my sound won't work, hopefully someone has some ideas.

I previously had to compile alsa from source with a patch to get sound to work, which I did successfully in Gutsy after I ran 'sudo apt-get install linux-backports-modules-generic'
([http://ubuntuforums.org/showthread.php?t=511876](http://ubuntuforums.org/showthread.php?t=511876))

however, the sound card is now detected but there's no sound still. I think maybe OSS is taking preference over ALSA even though alsa is selected in gnome..

---

### Post by yoblin on 2007-11-28
Heres my lsmod output:

```
Module                  Size  Used by
af_packet              24840  4 
binfmt_misc            12936  1 
ipv6                  273892  14 
nfsd                  220912  13 
exportfs                7040  1 nfsd
lockd                  67592  2 nfsd
sunrpc                172412  8 nfsd,lockd
ppdev                  10244  0 
fglrx                 656352  30 
cpufreq_ondemand        9612  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
sbs                    19592  0 
bay                     6912  0 
dock                   10656  1 bay
ac                      6148  0 
button                  8976  0 
battery                11012  0 
video                  18060  0 
container               5504  0 
ndiswrapper           185240  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
snd_hda_intel         291488  1 
snd_pcm_oss            43008  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80004  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10244  1 snd_hda_intel
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53360  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                39952  0 
serio_raw               8068  0 
snd                    54788  12 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                  4224  0 
soundcore               8800  1 snd
i2c_piix4               9740  0 
i2c_core               26112  1 i2c_piix4
sky2                   46852  0 
ati_agp                10124  0 
agpgart                35016  2 fglrx,ati_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  6 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
ide_disk               18560  3 
ata_generic             8452  0 
libata                125168  1 ata_generic
scsi_mod              147084  1 libata
atiixp                  7056  0 [permanent]
ide_core              116804  3 ide_cd,ide_disk,atiixp
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  4 ndiswrapper,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

---

