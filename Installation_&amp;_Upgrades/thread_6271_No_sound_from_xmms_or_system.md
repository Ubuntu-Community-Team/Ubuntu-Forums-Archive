---
title: "No sound from xmms or system"
date: 2004-11-26
forum: Installation &amp; Upgrades
---

### Post by dw5437 on 2004-11-26
I just installed Ubuntu today and everything works O:)  except sound :| 
I don't have any system sounds nor sound from any of the cd players.
Any help much appreciated.
By the way this is one of the most painless installs ever. The only other 2
that installed this easily was Mepis and Xandros.
Doug

---

### Post by p!=f on 2004-11-26
Run lsmod and lspci and post the outputs here please.

---

### Post by dw5437 on 2004-11-26
Module                  Size  Used by
radeon                115236  2
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
button                  6680  0
ac                      5132  0
battery                 9740  0
ds                     17796  0
yenta_socket           19328  0
pcmcia_core            63156  2 ds,yenta_socket
ipv6                  230020  8
af_packet              20872  2
e100                   30208  0
eepro100               28300  0
mii                     4864  2 e100,eepro100
ohci1394               32004  0
ieee1394              100536  1 ohci1394
snd_intel8x0           33068  2
snd_ac97_codec         59268  1 snd_intel8x0
snd_mpu401_uart         7296  1 snd_intel8x0
hw_random               5652  0
snd_usb_audio          65120  0
snd_rawmidi            23232  2 snd_mpu401_uart,snd_usb_audio
snd_seq_device          7944  1 snd_rawmidi
snd_pcm_oss            48168  0
snd_mixer_oss          16640  1 snd_pcm_oss
snd_pcm                85540  3 snd_intel8x0,snd_usb_audio,snd_pcm_oss
snd_page_alloc         11144  2 snd_intel8x0,snd_pcm
snd_timer              23172  1 snd_pcm
snd                    50660  14 snd_intel8x0,snd_ac97_codec,snd_mpu401_uart,snd_usb_audio,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
ehci_hcd               27780  0
audio                  42240  2
soundcore               9824  4 snd,audio
pwc                    48240  0
videodev                9856  1 pwc
uhci_hcd               29328  0
usbcore               104292  7 snd_usb_audio,ehci_hcd,audio,pwc,uhci_hcd
pciehp                 83948  0
shpchp                 87276  0
pci_hotplug            30640  2 pciehp,shpchp
intel_mch_agp          10000  0
intel_agp              20512  1
agpgart                31784  3 intel_mch_agp,intel_agp
analog                 10784  0
gameport                4736  2 snd_intel8x0,analog
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
tsdev                   7168  0
evdev                   9088  0
ide_cd                 38276  0
cdrom                  35872  1 ide_cd
mousedev               10124  1
psmouse                17800  0
xfs                   500184  0
reiserfs              207600  0
jfs                   157632  0
vfat                   13312  0
fat                    41792  1 vfat
isofs                  33976  0
ext3                  109544  1
jbd                    54552  1 ext3
ide_generic             1664  0
piix                   12576  1
ide_disk               16768  3
ide_core              125272  4 ide_cd,ide_generic,piix,ide_disk
unix                   25904  649
fan                     4236  0
thermal                12944  0
processor              17584  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb
is Lsmod

0000:00:00.0 Host bridge: Intel Corp. 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801BA/CA/DB/EB/ER Hub interface to PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 Storage Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
0000:02:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
0000:02:08.0 Ethernet controller: Intel Corp. 82562EZ 10/100 Ethernet Controller (rev 02)
d

---

