---
title: "TechniSat Skystar S2 problom"
date: 2013-12-22
forum: Installation &amp; Upgrades
---

### Post by chand2006 on 2013-12-22
Hi I am New In Linux

i have skystar s2 pci card

Linux gama-desktop 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 GNU/Linux

i try this link

[http://ubuntuforums.org/showthread.php?t=1888847&highlight=skystar+s2](http://ubuntuforums.org/showthread.php?t=1888847&highlight=skystar+s2)



sudo add-apt-repository ppa:yavdr/stable-vdr
sudo apt-get update
sudo apt-get install v4l-dvb-dkms
sudo reboot
*lspci &#8211;v* gives me the following output:

```
04:00.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02)
        Subsystem: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card
        Flags: slow devsel, IRQ 16
        Memory at fe2f0000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at dce0 [size=32]
        Kernel modules: b2c2-flexcop-pci
```

*lspci &#8211;vv* gives me the following output:

```
04:00.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02)
        Subsystem: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at fe2f0000 (32-bit, non-prefetchable) [size=64K]
        Region 1: I/O ports at dce0 [size=32]
        Kernel modules: b2c2-flexcop-pci
```


*lsmod* gives me the following output:

```
Module                  Size  Used by
nls_iso8859_1           3249  1
nls_cp437               4919  1
vfat                    8933  1
fat                    47767  1 vfat
binfmt_misc             6587  1
snd_hda_codec_analog    58598  1
mt312                   6801  0
stv0297                 6390  0
bcm3510                 8210  0
lgdt330x                7538  0
nxt200x                12217  0
mt352                   5466  0
fbcon                  35102  71
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0
vgastate                8961  1 vga16fb
snd_hda_intel          22069  2
snd_hda_codec          74201  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0
snd_seq_oss            26722  0
snd_seq_midi            4557  0
snd_rawmidi            19056  1 snd_seq_midi
stv0299                 8786  0
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i915                  289715  3
drm_kms_helper         29329  1 i915
ppdev                   5259  0
snd_timer              19130  2 snd_pcm,snd_seq
b2c2_flexcop_pci        5171  0
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi                1793  0
drm                   163747  4 i915,drm_kms_helper
psmouse                63677  0
parport_pc             25962  1
dcdbas                  5422  0
b2c2_flexcop           26368  1 b2c2_flexcop_pci
dvb_core               73304  3 lgdt330x,stv0299,b2c2_flexcop
cx24123                12626  1 b2c2_flexcop
cx24113                 7123  1 b2c2_flexcop
serio_raw               3978  0
snd                    54244  16 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
s5h1420                10588  1 b2c2_flexcop
intel_agp              24375  2 i915
agpgart                31724  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0
hid                    67288  1 usbhid
usb_storage            40033  1
e1000e                119888  0
```

what i did wrong 

thanks

---

### Post by chand2006 on 2013-12-22
heloo experts help me thanks

---

### Post by Iowan on 2013-12-22
From the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):
> Do not bump your thread more than once in any 24 hour period. Consider waiting longer than that before bumping - this may help to catch the attention of users outside of your timezone.

---

### Post by chand2006 on 2013-12-23
root@gama-desktop:~# dmesg |grep flex
[   12.191954] b2c2-flexcop: B2C2 FlexcopII/II(b)/III digital TV receiver chip loaded successfully
[   12.242013] flexcop-pci: will use the HW PID filter.
[   12.242015] flexcop-pci: card revision 2
[   12.242022] b2c2_flexcop_pci 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.257644] b2c2-flexcop: MAC address = 00:08:c9:e1:7b:42
[   13.126086] b2c2-flexcop: no frontend driver found for this B2C2/FlexCop adapter
[   13.126315] b2c2_flexcop_pci 0000:04:00.0: PCI INT A disabled


what is problom

---

