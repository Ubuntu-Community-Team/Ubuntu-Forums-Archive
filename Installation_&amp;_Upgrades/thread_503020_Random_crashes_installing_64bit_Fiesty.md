---
title: "Random crashes installing 64bit Fiesty"
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by zerocooltx on 2007-07-17
I'm having some difficulty installing 64 bit Feisty on my AMD system.  The 32 bit installation seems to work fine.  It's difficult to pin down the exact problem because the problem manifests itself as a random crash.

I have verified the CDROM I burned from the ISO image.  Thinking a random crash is a memory problem, I ran the memory test for 15-16 hours with no errors reported.

One consistent bug I noticed is that when booting the 64 bit install disk, I get static coming out of the speaker after the opening sound.  This happens while the screen outlining the drivers being started is running.  Once that screen is done, no static out of the speakers.

The output of lspci is identical between the 32 and 64 bit installations.

The output of lsmod is different but mostly in the size of the drivers installed.  There's a couple of different drivers and the "snd" line has the references in different order.  I'm listing them below.


When I boot into 64 bit, I've had trouble.  It didn't want to complete booting once.  Every other time, I get to the main screen.  One time, clicking on the install icon caused a hard crash.  Most of the time, I get a few screens into the install utility before I either get a hard lock up or it just reboots itself.

Here's  what I get from lspci:

[FONT="Courier New"]00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
[/FONT]


Here's from the 32 bit of lsmod:

[FONT="Courier New"]Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
lp                     12452  0 
radeon                124576  2 
drm                    81044  3 radeon
agpgart                35400  1 drm
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
video                  16388  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
dock                   10268  0 
container               5248  0 
button                  8720  0 
battery                10756  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
ac                      6020  0 
fuse                   46612  1 
ipv6                  268704  8 
snd_mpu401              9256  0 
snd_mpu401_uart         9472  1 snd_mpu401
snd_intel8x0           34204  1 
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
af_packet              23816  2 
snd                    54020  14 snd_mpu401,snd_mpu401_uart,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
analog                 12832  0 
gameport               16520  1 analog
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
i2c_nforce2             6784  0 
psmouse                38920  0 
pcspkr                  4224  0 
i2c_core               22784  2 i2c_ec,i2c_nforce2
shpchp                 34324  0 
serio_raw               7940  0 
k8temp                  6656  0 
pci_hotplug            32576  1 shpchp
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
evdev                  11008  3 
tsdev                   8768  0 
squashfs               49028  1 
loop                   17800  2 
unionfs                74020  1 
nls_cp437               6784  1 
isofs                  36284  1 
sg                     36252  0 
sd_mod                 23428  0 
ext3                  133128  0 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  1 
cdrom                  37664  1 ide_cd
ide_disk               17024  2 
sata_nv                20868  0 
ata_generic             9092  0 
libata                125720  2 sata_nv,ata_generic
usb_storage            72256  0 
scsi_mod              142348  4 sg,sd_mod,libata,usb_storage
libusual               17936  1 usb_storage
floppy                 59524  0 
forcedeth              46728  0 
ohci1394               36528  0 
ieee1394              299448  1 ohci1394
ohci_hcd               22532  0 
generic                 5124  0 [permanent]
amd74xx                15260  0 [permanent]
ehci_hcd               34188  0 
usbcore               134280  5 usb_storage,libusual,ohci_hcd,ehci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability[/FONT]


Here's from the 64 bit version of lsmod

[FONT="Courier New"]Module                  Size  Used by
binfmt_misc            14604  1 
rfcomm                 45352  0 
l2cap                  28160  5 rfcomm
bluetooth              62340  4 rfcomm,l2cap
ppdev                  11272  0 
lp                     15048  0 
radeon                126368  2 
drm                   103464  3 radeon
cpufreq_userspace       6176  0 
cpufreq_stats           8416  0 
cpufreq_powersave       3072  0 
cpufreq_ondemand       10640  0 
freq_table              6336  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     9736  0 
tc1100_wmi              9224  0 
sony_acpi               7064  0 
pcc_acpi               15616  0 
dev_acpi               17028  0 
video                  19080  0 
sbs                    17856  0 
i2c_ec                  6784  1 sbs
dock                   11992  0 
container               6144  0 
button                 10016  0 
battery                12040  0 
asus_acpi              19756  0 
backlight               8448  1 asus_acpi
ac                      6920  0 
fuse                   51888  1 
ipv6                  307072  10 
snd_mpu401             11560  0 
snd_mpu401_uart        10752  1 snd_mpu401
snd_seq_dummy           5380  0 
snd_seq_oss            36608  0 
snd_seq_midi           11008  0 
snd_rawmidi            29696  2 snd_mpu401_uart,snd_seq_midi
snd_intel8x0           38952  1 
snd_ac97_codec        117720  1 snd_intel8x0
ac97_bus                3968  1 snd_ac97_codec
snd_seq_midi_event      9856  2 snd_seq_oss,snd_seq_midi
snd_pcm_oss            49536  0 
analog                 13024  0 
parport_pc             40104  1 
snd_mixer_oss          19840  1 snd_pcm_oss
snd_pcm                92808  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
i2c_nforce2             7680  0 
snd_seq                61856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
af_packet              27020  2 
psmouse                43536  0 
gameport               18704  1 analog
parport                43404  3 ppdev,lp,parport_pc
i2c_core               26624  2 i2c_ec,i2c_nforce2
serio_raw               9092  0 
snd_timer              26632  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 37404  0 
snd                    68904  14 snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         11792  2 snd_intel8x0,snd_pcm
soundcore              10272  1 snd
k8temp                  7552  0 
pci_hotplug            36228  1 shpchp
pcspkr                  4736  0 
evdev                  13056  3 
tsdev                  10112  0 
squashfs               45448  1 
loop                   20368  2 
unionfs                83240  1 
nls_cp437               8192  1 
isofs                  38628  1 
sg                     40616  0 
sd_mod                 25092  0 
ext3                  143760  0 
jbd                    68208  1 ext3
mbcache                11400  1 ext3
ide_cd                 35104  1 
cdrom                  40744  1 ide_cd
ide_disk               18304  2 
sata_nv                24196  0 
ata_generic            10628  0 
libata                137000  2 sata_nv,ata_generic
usb_storage            80448  0 
scsi_mod              166968  4 sg,sd_mod,libata,usb_storage
libusual               22184  1 usb_storage
floppy                 67944  0 
forcedeth              48776  0 
ohci1394               38088  0 
ieee1394              369784  1 ohci1394
ohci_hcd               24196  0 
generic                 6532  0 [permanent]
amd74xx                16944  0 [permanent]
ehci_hcd               37004  0 
usbcore               154416  5 usb_storage,libusual,ohci_hcd,ehci_hcd
thermal                16912  0 
processor              34952  1 thermal
fan                     6536  0 
fbcon                  44416  0 
tileblit                4096  1 fbcon
font                    9856  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3712  1 bitblit
vesafb                 10376  0 
cfbcopyarea             5120  1 vesafb
cfbimgblt               4096  1 vesafb
cfbfillrect             5632  1 vesafb
capability              7048  0 
commoncap               9472  1 capability[/FONT]


Any input on what to try to resolve this issue will be much appreciated.

---

### Post by zerocooltx on 2007-07-17
It may be my ATI video card and/or driver.

I have two monitors.  I had my second monitor turned off since I was going to mess with getting that enabled after I had everything installed and running.  But it was still plugged into the DVI port on the ATI card.  I unplugged it and everything appears to be running just fine.

I have an nVidea card that I'm going to swap in if I can't get this ATI card to work.

---

