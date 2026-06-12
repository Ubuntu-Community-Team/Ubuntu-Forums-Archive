---
title: "upgrate from 8.04 can't scan wireless network"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Guradian on 2008-10-25
i recently upgrade my system from 8.04 to 8.10, everything work fine. but the network manager won't show me the wireless network when i click the tray icon.

and even i set the wireless manually(use wep), it can't get ip address.

my wireless card is iwl3945, work fine in 8.04.

can anyone help me?

---

### Post by inertz on 2008-10-25
Can you try type
```
sudo lsmod
```

and 

```
sudo iwconfig
```

and post the output here?

---

### Post by Guradian on 2008-10-25
ken@ken-laptop ~ $ lsmod
Module                  Size  Used by
binfmt_misc            16904  1 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
rfcomm                 44432  0 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 bnep,sco,rfcomm,l2cap
ipv6                  263972  14 
af_packet              25728  4 
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  2 
cpufreq_userspace      11396  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
pci_slot               12552  0 
wmi                    14504  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
pcmcia                 43052  0 
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
iTCO_wdt               18596  0 
snd_seq_dummy          10884  0 
iwl3945                95224  0 
sr_mod                 22212  0 
serio_raw              13444  0 
iTCO_vendor_support    11652  1 iTCO_wdt
cdrom                  43168  1 sr_mod
snd_seq_oss            38528  0 
sdhci_pci              15360  0 
rfkill                 17176  2 iwl3945
evdev                  17696  11 
sdhci                  23940  1 sdhci_pci
pcspkr                 10624  0 
psmouse                45200  0 
mac80211              208172  1 iwl3945
mmc_core               58268  1 sdhci
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
led_class              12164  1 iwl3945
yenta_socket           31756  1 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
rsrc_nonstatic         19072  1 yenta_socket
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cfg80211               39700  2 iwl3945,mac80211
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
video                  25104  0 
snd_timer              29960  2 snd_pcm,snd_seq
tpm_infineon           17064  0 
output                 11008  1 video
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tpm                    22848  1 tpm_infineon
container              11520  0 
tpm_bios               14080  1 tpm
battery                18436  0 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ac                     12292  0 
button                 14224  0 
intel_agp              33724  1 
agpgart                42184  2 intel_agp
soundcore              15328  1 snd
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133256  2 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
usb_storage            81728  0 
sd_mod                 42264  4 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
libusual               27156  1 usb_storage
usbhid                 35840  0 
hid                    50560  1 usbhid
ahci                   37132  3 
ohci1394               37936  0 
libata                177312  1 ahci
ehci_hcd               43276  0 
ieee1394               96324  2 sbp2,ohci1394
scsi_mod              155212  6 sbp2,sr_mod,usb_storage,sd_mod,sg,libata
e1000e                112680  0 
uhci_hcd               30736  0 
usbcore               148848  6 usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
dock                   16656  1 libata
dm_mirror              26880  0 
dm_log                 17924  1 dm_mirror
dm_snapshot            26276  0 
dm_mod                 63432  3 dm_mirror,dm_log,dm_snapshot
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 


ken@ken-laptop ~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=12 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


any help?

---

