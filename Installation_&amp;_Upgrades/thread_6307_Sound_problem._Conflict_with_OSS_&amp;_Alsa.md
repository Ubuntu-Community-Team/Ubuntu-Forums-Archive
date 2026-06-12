---
title: "Sound problem. Conflict with OSS &amp; Alsa?"
date: 2004-11-27
forum: Installation &amp; Upgrades
---

### Post by macewan on 2004-11-27
Sound is scratchy and echos. The Volume Control has both a TriTech TR28602 [OSS Mixer] and an Ensoniq AudioPCI [Alsa Mixer]. The output from lsmod and lspci are listed below. Any suggestions would be greatly appreciated.


macewan@pigglywiggly:~ $ lsmod

Module                  Size  Used by
r128                   92836  2
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
binfmt_misc            11272  1
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  229764  10
af_packet              20872  2
snd_ens1371            23012  4
snd_rawmidi            23232  1 snd_ens1371
snd_seq_device          7944  1 snd_rawmidi
snd_ac97_codec         59268  1 snd_ens1371
gameport                4736  1 snd_ens1371
snd_bt87x              13640  0
snd_pcm_oss            48168  0
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85412  4 snd_ens1371,snd_bt87x,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd                    50660  12 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97 _codec,snd_bt87x,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         11144  2 snd_bt87x,snd_pcm
bt878                  11184  0
tuner                  18320  0
tvaudio                20748  0
bttv                  143020  1 bt878
video_buf              20356  1 bttv
i2c_algo_bit            8968  1 bttv
v4l2_common             6400  1 bttv
btcx_risc               4744  1 bttv
i2c_core               22416  4 tuner,tvaudio,bttv,i2c_algo_bit
videodev                9856  1 bttv
soundcore               9824  4 snd,bttv
eepro100               28300  0
e100                   30080  0
mii                     4864  2 eepro100,e100
uhci_hcd               29328  0
usbcore               104164  3 uhci_hcd
pci_hotplug            30640  0
via_agp                 8832  1
agpgart                31784  2 via_agp
floppy                 54996  0
pcspkr                  3816  0
rtc                    12088  0
md                     44744  0
dm_mod                 51068  1
parport_pc             31936  1
lp                     10436  0
parport                37320  2 parport_pc,lp
tsdev                   7168  0
evdev                   9088  0
ide_cd                 38148  0
cdrom                  35744  1 ide_cd
mousedev                9996  1
psmouse                17800  0
sd_mod                 20480  0
scsi_mod              115148  1 sd_mod
ext3                  109544  1
jbd                    54552  1 ext3
ide_generic             1664  0
via82cxxx              12956  1
ide_disk               16768  3
ide_core              125144  4 ide_cd,ide_generic,via82cxxx,ide_disk
unix                   25904  867
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal




macewan@pigglywiggly:~ $ lspci

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:09.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 0c)
0000:00:0d.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:0d.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:00:11.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP

---

### Post by macewan on 2004-11-27
[QUOTE=macewan]Sound is scratchy and echos. The Volume Control has both a TriTech TR28602 [OSS Mixer] and an Ensoniq AudioPCI [Alsa Mixer]. The output from lsmod and lspci are listed below. Any suggestions would be greatly appreciated.


macewan@pigglywiggly:~ $ lsmod

Module                  Size  Used by
r128                   92836  2
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
binfmt_misc            11272  1
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  229764  10
af_packet              20872  2
snd_ens1371            23012  4
snd_rawmidi            23232  1 snd_ens1371
snd_seq_device          7944  1 snd_rawmidi
snd_ac97_codec         59268  1 snd_ens1371
gameport                4736  1 snd_ens1371
snd_bt87x              13640  0
snd_pcm_oss            48168  0
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85412  4 snd_ens1371,snd_bt87x,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd                    50660  12 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97 _codec,snd_bt87x,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         11144  2 snd_bt87x,snd_pcm
bt878                  11184  0
tuner                  18320  0
tvaudio                20748  0
bttv                  143020  1 bt878
video_buf              20356  1 bttv
i2c_algo_bit            8968  1 bttv
v4l2_common             6400  1 bttv
btcx_risc               4744  1 bttv
i2c_core               22416  4 tuner,tvaudio,bttv,i2c_algo_bit
videodev                9856  1 bttv
soundcore               9824  4 snd,bttv
eepro100               28300  0
e100                   30080  0
mii                     4864  2 eepro100,e100
uhci_hcd               29328  0
usbcore               104164  3 uhci_hcd
pci_hotplug            30640  0
via_agp                 8832  1
agpgart                31784  2 via_agp
floppy                 54996  0
pcspkr                  3816  0
rtc                    12088  0
md                     44744  0
dm_mod                 51068  1
parport_pc             31936  1
lp                     10436  0
parport                37320  2 parport_pc,lp
tsdev                   7168  0
evdev                   9088  0
ide_cd                 38148  0
cdrom                  35744  1 ide_cd
mousedev                9996  1
psmouse                17800  0
sd_mod                 20480  0
scsi_mod              115148  1 sd_mod
ext3                  109544  1
jbd                    54552  1 ext3
ide_generic             1664  0
via82cxxx              12956  1
ide_disk               16768  3
ide_core              125144  4 ide_cd,ide_generic,via82cxxx,ide_disk
unix                   25904  867
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal




macewan@pigglywiggly:~ $ lspci

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:09.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 0c)
0000:00:0d.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:0d.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:00:11.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP[/QUOTE]
 hrm, would this be a kernel prob?

---

### Post by macewan on 2004-12-02
[QUOTE=macewan]hrm, would this be a kernel prob?[/QUOTE]
 I apologize for bumping but this problem still exist.

---

### Post by brousch on 2004-12-03
It is probably not the case here, but I had a similar situation to the one you originally described because I had a microphone plugged in and turned on.

The mic picked up normal sound and echoed them back through the speakers, and scratching was due to picking up normal noises in the room.

Could also be due to a speaker plugged into the microphone port instead of the speaker port. A speaker acts as a crube microphone in this situation.

---

### Post by fvantoor on 2004-12-03
I had the same problem in Ubuntu, while Kanotix gave a good sound.
In multimedia/ sound control / preferences I switched off: IEC958 input monitor and IEC958 Playback AC-97 -SPSA. This solved the problem for me

---

### Post by macewan on 2004-12-04
[QUOTE=fvantoor]I had the same problem in Ubuntu, while Kanotix gave a good sound.
In multimedia/ sound control / preferences I switched off: IEC958 input monitor and IEC958 Playback AC-97 -SPSA. This solved the problem for me[/QUOTE]
 The thing is that a CD will play fine - as does TV. So the hardware is fine. Tried your suggestions but no luck yet.

---

