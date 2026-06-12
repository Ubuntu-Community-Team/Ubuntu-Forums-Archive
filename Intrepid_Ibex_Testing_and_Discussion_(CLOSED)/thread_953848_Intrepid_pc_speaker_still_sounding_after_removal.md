---
title: "Intrepid pc speaker still sounding after removal"
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by PinkFloyd102489 on 2008-10-20
Instead of playing the sound I set for new mail notification, the pc speaker beeps. Problem is, I removed the pcspkr module. Is this a known problem?

```

brandon@ubuntu-laptop:~$ sudo rmmod pcspkr
ERROR: Module pcspkr does not exist in /proc/modules

```


Output of lsmod:
```

brandon@ubuntu-laptop:~$ sudo lsmod
Module                  Size  Used by
hidp                   25216  1 
nls_cp437              15232  0 
nls_utf8               10240  1 
cifs                  279696  1 
michael_mic            11008  4 
arc4                   10368  4 
ecb                    11520  4 
crypto_blkcipher       27780  1 ecb
usbhid                 39776  0 
hid                    59072  2 hidp,usbhid
btusb                  21912  4 
af_packet              29568  4 
b44                    41872  0 
ssb                    46340  1 b44
ieee80211_crypt_tkip    18048  0 
wl                   1085520  0 
rfcomm                 51104  6 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
sco                    20612  2 
l2cap                  33280  21 hidp,rfcomm,bnep
bluetooth              70820  16 hidp,btusb,rfcomm,bnep,sco,l2cap
ipv6                  314312  16 
ppdev                  16904  0 
acpi_cpufreq           16400  1 
cpufreq_powersave      10368  1 
cpufreq_stats          14468  0 
cpufreq_ondemand       16400  0 
freq_table             13568  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    16392  0 
cpufreq_userspace      12420  0 
pci_slot               13704  0 
container              12288  0 
sbs                    22288  0 
sbshc                  14592  1 sbs
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
hwmon_vid              12288  0 
eeprom                 14864  0 
i2c_viapro             17560  0 
coretemp               15488  0 
sbp2                   32652  0 
parport_pc             44200  0 
lp                     19588  0 
parport                50096  3 ppdev,parport_pc,lp
joydev                 20736  0 
snd_hda_intel         489264  3 
snd_pcsp               19836  1 
snd_pcm_oss            52608  0 
snd_seq_dummy          11524  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  3 snd_hda_intel,snd_pcsp,snd_pcm_oss
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               68616  0 
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
compat_ioctl32         18176  1 uvcvideo
serio_raw              14596  0 
snd                    79432  18 snd_hda_intel,snd_pcsp,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               46720  2 uvcvideo,compat_ioctl32
dcdbas                 16688  0 
soundcore              16800  1 snd
psmouse                51612  0 
evdev                  20512  19 
v4l1_compat            24580  2 uvcvideo,videodev
nvidia               7804864  42 
sdhci_pci              17024  0 
video                  28948  10 
ieee80211_crypt        14596  2 ieee80211_crypt_tkip,wl
sdhci                  27396  1 sdhci_pci
ricoh_mmc              12672  0 
output                 11776  1 video
i2c_core               36128  3 eeprom,i2c_viapro,nvidia
mmc_core               67168  1 sdhci
wmi                    15808  0 
ac                     13448  0 
intel_agp              39280  0 
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
iTCO_wdt               21072  0 
button                 15904  0 
battery                21128  0 
iTCO_vendor_support    12420  1 iTCO_wdt
shpchp                 42140  0 
pci_hotplug            39472  1 shpchp
ext3                  150544  1 
jbd                    66472  1 ext3
mbcache                17924  1 ext3
sr_mod                 24644  0 
cdrom                  47784  1 sr_mod
pata_acpi              13568  0 
sd_mod                 45864  4 
crc_t10dif             10240  1 sd_mod
sg                     45408  0 
ata_generic            14212  0 
ahci                   43148  3 
ata_piix               29444  0 
ohci1394               41524  0 
libata                200160  4 pata_acpi,ata_generic,ahci,ata_piix
ieee1394              110592  2 sbp2,ohci1394
scsi_mod              183160  5 sbp2,sr_mod,sd_mod,sg,libata
mii                    14592  1 b44
dock                   18464  1 libata
ehci_hcd               48908  0 
uhci_hcd               34336  0 
usbcore               175376  6 usbhid,btusb,uvcvideo,ehci_hcd,uhci_hcd
thermal                27424  0 
processor              47800  4 acpi_cpufreq,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  5

```

Thanks nanog, forgot to mention my setup.

Dell Inspiron 1720 Vista Home Premium SP1/Intrepid Ibex dual boot.
Intel Core 2 Duo T8300 2.4Ghz 800Mhz FSB
4GB Shared dual channel DDR RAM @ 667Mhz
Nvidia GeForce 8600M GT 256MB
SoundBlaster Audigy HD SE

---

### Post by nanog on 2008-10-20
I can confirm this on a laptop.

---

### Post by PinkFloyd102489 on 2008-10-23
Still doing it. My laptop had a spastic fit in class today (which was horrible) and beep about 50 times in rapid succession, paused, and did so again. I had to pull the battery on it real quick in order for it to stop.

pcspkr module is still unloaded and is in fact blacklisted.

---

