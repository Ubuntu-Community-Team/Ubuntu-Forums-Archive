---
title: "kernel modules not loading"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by byorgey on 2006-06-10
Hi all,  

I've spent a while looking around to see if anyone else has had the same problem but haven't found anything.  Anyway, I just upgraded from breezy -> dapper, I had a little trouble with lvm2 but other than that the upgrade seemed to go fine.  The problem is, now when I boot up it seems that certain kernel modules are not getting loaded.  For example, on bootup networking does not work, but after a little poking around I realized that the module for my ethernet card wasn't loaded -- so I did a modprobe 3c59x and then ifup eth0 and it worked great.  Same thing with sound.  But there are lots of other modules which aren't loaded too (USB doesn't work, etc.) and obviously I don't want to have to insert a bunch of kernel modules by hand every time I reboot.  Any ideas would be appreciated.  Here's some additional info:

```

$ lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0d.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
0000:00:0e.0 VGA compatible controller: Matrox Graphics, Inc. MGA 2164W [Millennium II]
0000:00:10.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
0000:00:10.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
0000:00:11.0 Communication controller: Conexant HCF 56k Data/Fax/Voice/Spkp Modem (rev 08)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

```

(Note any modules having to do with sound, USB, or networking I loaded myself)
```

$ lsmod
Module                  Size  Used by
usb_storage            64064  0
scsi_mod              119936  1 usb_storage
usbhid                 29376  0
floppy                 54864  0
uhci_hcd               30224  0
usbcore               107384  4 usb_storage,usbhid,uhci_hcd
emu10k1                71940  0
sound                  74028  1 emu10k1
ac97_codec             16780  1 emu10k1
snd_pcm_oss            47652  0
snd_pcm                84872  1 snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  1 snd_pcm
rfcomm                 36252  0
l2cap                  24324  5 rfcomm
bluetooth              46340  4 rfcomm,l2cap
nfsd                  190752  9
exportfs                5888  1 nfsd
lockd                  58152  2 nfsd
sunrpc                137188  12 nfsd,lockd
ppdev                   9348  0
3c59x                  37160  0
snd_mixer_oss          16768  1 snd_pcm_oss
ipv6                  229504  14
snd                    50276  4 snd_pcm_oss,snd_pcm,snd_timer,snd_mixer_oss
soundcore               9824  3 emu10k1,sound,snd
speedstep_lib           4228  0
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
rtc                    12216  0
md                     43856  0
dm_mod                 53116  1
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  3 ppdev,parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  3
ide_core              118988  5 usb_storage,ide_cd,ide_generic,piix,ide_disk
unix                   26164  733
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

```

---

### Post by byorgey on 2006-06-17
Problem solved -- it seems the problem was that for some reason it didn't automatically update to the newest version of the kernel, it was still running 2.6.10 and I guess it didn't play nice with some of the newer packages.  Once I figured this out, I installed 2.6.15 and it works just dandy.

---

