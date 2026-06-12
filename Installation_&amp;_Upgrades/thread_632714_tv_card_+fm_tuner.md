---
title: "tv card +fm tuner"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by nzadLithium on 2007-12-05
hey

I have a pixelview playtv pro2 card.

i use this to get the modules in place.
modprobe --remove bt878 bttv
modprobe bttv radio=1 card=70 tuner=38 automute=0 audiomux=33,32,35,40 bttv_verbose=0 gbuffers=8 gpiomask=0x3F
modprobe btaudio

my dmesg:

```
[   70.142012] bttv0: unloading
[   70.218312] Linux video capture interface: v2.00
[   70.254645] bttv: driver version 0.9.16 loaded
[   70.256507] bttv: Bt8xx card found (0).
[   70.256702] bttv0: Bt878 (rev 17) at 0000:05:07.0, irq: 17, latency: 32, mmio: 0xc3100000
[   70.256880] bttv0: using: Prolink Pixelview PV-BT878P+ (Rev.4C,8E) [card=70,insmod option]
[   70.256883] bttv0: gpio config override: mask=0x3f, mux=0x21,0x20,0x23,0x28,0xd
[   70.259860] bttv0: using tuner=38
[   70.474433] tuner 0-0060: All bytes are equal. It is not a TEA5767
[   70.474438] tuner 0-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   70.474462] tuner 0-0060: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   70.474465] tuner 0-0060: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   70.474630] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   70.487816] bttv0: registered device video0
[   70.488129] bttv0: registered device vbi0
[   70.488381] bttv0: registered device radio0
[   70.560280] input: bttv IR (card=70) as /class/input/input7
[   70.686870] btaudio: driver version 0.7 loaded [digital+analog]
[   70.687419] ACPI: PCI Interrupt 0000:05:07.1[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 17
[   70.687599] btaudio: Bt878 (rev 17) at 05:07.1, irq: 17, latency: 32, mmio: 0xc3101000
[   70.687603] btaudio: using card config "default"
[   70.688252] btaudio: registered device dsp1 [digital]
[   70.688721] btaudio: registered device dsp2 [analog]
[   70.689116] btaudio: registered device mixer2

```

lsmod:
```
Module                  Size  Used by
btaudio                20116  0 
tuner                  67368  0 
tvaudio                27804  0 
bttv                  213748  0 
video_buf              29700  1 bttv
ir_common              34308  1 bttv
compat_ioctl32         11136  1 bttv
i2c_algo_bit            9608  1 bttv
btcx_risc               6664  1 bttv
tveeprom               19216  1 bttv
videodev               29824  1 bttv
v4l2_common            28800  4 tuner,bttv,compat_ioctl32,videodev
v4l1_compat            14980  1 videodev
binfmt_misc            14604  1 
nfs                   263384  0 
nfsd                  266920  17 
exportfs                7808  1 nfsd
lockd                  73136  3 nfs,nfsd
sunrpc                184392  12 nfs,nfsd,lockd
ppdev                  11272  0 
cpufreq_userspace       6176  0 
cpufreq_stats           8416  0 
cpufreq_powersave       3072  0 
cpufreq_ondemand       10640  0 
freq_table              6336  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     9736  0 
tc1100_wmi              9224  0 
pcc_acpi               15616  0 
dev_acpi               17028  0 
sony_acpi               7064  0 
video                  19080  0 
sbs                    17856  0 
i2c_ec                  6912  1 sbs
dock                   11992  0 
button                 10016  0 
battery                12040  0 
container               6144  0 
ac                      6920  0 
asus_acpi              19756  0 
backlight               8448  1 asus_acpi
af_packet              27020  2 
nls_utf8                3456  1 
ntfs                  101960  1 
lp                     15048  0 
snd_emu10k1_synth       9216  0 
snd_emux_synth         39936  1 snd_emu10k1_synth
snd_seq_virmidi         9216  1 snd_emux_synth
snd_seq_midi_emul       8960  1 snd_emux_synth
snd_emu10k1           133024  5 snd_emu10k1_synth
snd_ac97_codec        117848  1 snd_emu10k1
ac97_bus                3968  1 snd_ac97_codec
snd_pcm_oss            49408  1 
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  5 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11792  2 snd_emu10k1,snd_pcm
snd_util_mem            6656  2 snd_emux_synth,snd_emu10k1
joydev                 12928  0 
snd_hwdep              12168  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           5380  0 
snd_seq_oss            36608  0 
snd_seq_midi           11008  0 
snd_seq_midi_event      9856  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
analog                 13024  0 
snd_mpu401             11560  0 
snd_mpu401_uart        10752  1 snd_mpu401
nvidia               5659736  34 
parport_pc             40104  1 
parport                43404  3 ppdev,lp,parport_pc
pcspkr                  4736  0 
psmouse                43536  0 
serio_raw               9092  0 
snd_rawmidi            29696  4 snd_seq_virmidi,snd_emu10k1,snd_seq_midi,snd_mpu401_uart
acx                   104580  0 
snd_seq                61856  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26632  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         10260  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
usbhid                 29088  0 
hid                    34048  1 usbhid
xpad                   11272  0 
i2c_nforce2             7680  0 
snd                    68904  23 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  3 btaudio,snd
k8temp                  7552  0 
emu10k1_gp              5632  0 
i2c_core               26496  8 tuner,tvaudio,bttv,i2c_algo_bit,tveeprom,i2c_ec,nvidia,i2c_nforce2
shpchp                 37404  0 
pci_hotplug            36228  1 shpchp
gameport               18704  3 analog,emu10k1_gp
ipv6                  307456  22 
evdev                  13056  4 
tsdev                  10112  0 
ipt_MASQUERADE          5248  2 
xt_mark                 3840  1 
xt_tcpudp               4992  1 
xt_MARK                 4224  1 
iptable_mangle          4352  1 
iptable_nat             9476  1 
nf_nat                 22828  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      22160  2 iptable_nat
nf_conntrack           73180  4 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink               9160  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
ip_tables              23080  2 iptable_mangle,iptable_nat
x_tables               23688  6 ipt_MASQUERADE,xt_mark,xt_tcpudp,xt_MARK,iptable_nat,ip_tables
ext3                  143760  1 
jbd                    68208  1 ext3
mbcache                11400  1 ext3
ide_cd                 35104  0 
cdrom                  40744  1 ide_cd
ide_disk               18304  3 
sata_nv                24196  0 
ata_generic            10628  0 
libata                137000  2 sata_nv,ata_generic
scsi_mod              166968  1 libata
floppy                 67944  0 
ohci_hcd               24196  0 
ohci1394               38088  0 
ieee1394              369784  1 ohci1394
forcedeth              48776  0 
generic                 6532  0 [permanent]
amd74xx                16944  0 [permanent]
ehci_hcd               37004  0 
usbcore               154416  6 acx,usbhid,xpad,ohci_hcd,ehci_hcd
thermal                16912  0 
processor              34952  1 thermal
fan                     6536  0 
capability              7048  0 
commoncap               9472  1 capability
vesafb                 10376  0 
cfbcopyarea             5120  1 vesafb
cfbimgblt               4096  1 vesafb
cfbfillrect             5632  1 vesafb
fbcon                  44416  0 
tileblit                4096  1 fbcon
font                    9856  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3712  1 bitblit

```

relevant sections from lspci:
```
05:06.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
05:06.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
05:06.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
05:07.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
05:07.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

```

ok so i have the tv part of my card going properly i think. Recording sound works too. It looks like i aint got a hope in getting the remote to go. I have seen many posts that say how to get it going. I have done the exact same things and it doesnt go. I think the lirc driver for my card might have got broke with newer versions of lirc? i duno.
would be nice to get remote going but thats not my main concern.

The thing i most want to get going is my radio.
I can go into the radio program (i have both the radio program provided with xawtv and gnome radio). I can use the radio but i have to use the video0 device because the radio0 device does not produce sound output. When i use radio0 i get stereo sound but no sound when i use video0 i get sound most of the time with alot of static and only mono sound. Atm i am using video0 but it seems the static is coming from a second radio station??? In the background i get what sounds like another radio station underneath the station im listening too so i'm hoping that all the static im getting is coming from that station and im hoping someone knows how to get rid of this second radio station? There is only about two stations i can listen to relatively clearly compared to on xp where i have about 30 i can listen to clearly. 

and is there anyway i can schedule a recording in xawtv? I could probably write a program to send xawtv xevents but it seems like a rather hacky way to do it. there must be a simple way to schedule a tv recording. I'd be happy to use a different program if anyone knows of one that can schedule recordings but i would prefer not to use myth tv.

Any help with any of these problems is much appreciated. And sry for the long post :S

---

