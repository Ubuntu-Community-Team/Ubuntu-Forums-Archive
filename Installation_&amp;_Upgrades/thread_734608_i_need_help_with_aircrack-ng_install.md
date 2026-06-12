---
title: "i need help with aircrack-ng install"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by thesteve151 on 2008-03-24
ok so i tried to install aircrack-ng, and when i go to use it it displays this message "This program requires root privileges."
i am new to linux, am am willing to to do the research on how to use the program, but i just can't get it to work, and need some help to get back on track.

why is this message coming up? did i install it wrong?
thanks for the advice.

---

### Post by reyhan on 2008-03-24
you must be in root privileges by typing su on your terminal

---

### Post by thesteve151 on 2008-03-24
thanks i just figured that out, but now when i use sudo it says that no such device, i think i still need to install madwifi, even though it should be installed already...

---

### Post by thesteve151 on 2008-03-25
ok when i use iwconfig i get this:
toshiba@Satellite:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Carmike Cinemas"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:19:60:28   
          Bit Rate:2 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/100  Signal level=-82 dBm  Noise level=-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7302   Missed beacon:0

toshiba@Satellite:~$ 


it should look like this:
eth0      no wireless extensions.

lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:0 kb/s   Tx-Power:20 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

why doesn't mine say ath0?
and how to i get it to change to the ath0?

---

### Post by CrimsoniteX on 2008-03-25
You already patched your wireless drivers right?

---

### Post by thesteve151 on 2008-03-25
i have been trying to, but can't seem to ever get anywhere. all the how-to's are old, and half the links don't work: but the wireless card works to get on the internet, so do i even need to patch the drivers?

---

### Post by thesteve151 on 2008-03-25
ok i found out what i need to do for now...
there is a bunch of softwhere i need to install, like apache 2, and some other stuff, i will post back when i get stuck again.

---

### Post by thesteve151 on 2008-03-26
ok so i am having some trouble, i still can't get the names to change for my devices under iwconfig. what should they be?
mine come up as:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Carmike Cinemas"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:19:60:28   
          Bit Rate:2 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/100  Signal level=-83 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6517   Missed beacon:0

but like i posted earlier, they are not the same as the guides i am trying to follow...

---

### Post by croto on 2008-03-26
Hey,

The guide you're following assumes you have an atheros wireless card. That's why the wireless device shows up as "ath0" (also note the "wifi0" device. That's the real atheros device, ath0 is just a virtual wireless device created by the madwifi driver). So I guess your card does not have an atheros chipset. If you have another wireless card, you have to make sure it can be set in monitor mode. Some drivers need to be patched to accomplish that, and that's why a previous poster asked whether you patched the drivers. Check the aircrack website for a compatibility list.

---

### Post by thesteve151 on 2008-03-26
here is the info on my wireless card, in my Toshiba satellite  A135-S4427  
Intel 802.11a/b/g/n, a/b/g, b/g PCIe Mini Card driver

Atheros Mini PCI/PCIe Wireless Lan (802.11 a/b/g, b/g) Driver

Atheros AR5006EG

---

### Post by croto on 2008-03-26
Ok, if that's the case, you have an atheros card. What drivers are you using right now? Can you please post the output of:
```

lspci

```

```

lsmod

```
and
```

modinfo ath_pci

```

You may have to install a newer or patched version of madwifi-ng.

---

### Post by thesteve151 on 2008-03-26
i am trying to reconfigure my wireless card via this guide so i can get madwifi working with aircrack-ng
[http://madwifi.org/wiki/Requirements](http://madwifi.org/wiki/Requirements)


so i am trying to configure the kernel setting to match the requirements in the guide, and i can't figure out how...

this is what i want it to be, but i can't figure out how to change it.
Kernel ¶

    * Linux Kernel 2.4.23+ and 2.6.x series
          o Others may work, but are unsupported; also, beware if using the very latest release candidate (RC#) kernel as it may not yet be supported 
    * Kernel Source and Headers of running kernel
    * No module versioning support
          o option CONFIG_MODVERSIONS 
    * Wireless Extensions support in kernel
          o v14+ required, v17+ recommended; option CONFIG_NET_RADIO (kernel 2.6.22 and later: CONFIG_WLAN_80211) 
    * Sysctl support in kernel
          o option CONFIG_SYSCTL 
    * Crypto API support in kernel
          o option CONFIG_CRYPTO 
    * HMAC support
          o option CONFIG_CRYPTO_HMAC 
    * AES support (for WPA networks)
          o option CONFIG_CRYPTO_AES

---

### Post by thesteve151 on 2008-03-26
toshiba@Satellite:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
toshiba@Satellite:~$ 



toshiba@Satellite:~$ lsmod
Module                  Size  Used by
battery                11012  0 
ac                      6148  0 
thermal                14344  0 
fan                     5764  0 
button                  8976  0 
ipw3945               119840  1 
ieee80211              35656  1 ipw3945
ieee80211_crypt         7040  1 ieee80211
r8169                  32260  0 
usbhid                 29536  0 
hid                    28928  1 usbhid
ipv6                  273892  10 
af_packet              24840  4 
i915                   25856  2 
drm                    83348  3 i915
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
acpi_cpufreq           10568  1 
cpufreq_ondemand        9612  1 
cpufreq_stats           7232  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
sbs                    19592  0 
dock                   10656  0 
container               5504  0 
video                  18060  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
pcmcia                 41388  0 
snd_hda_intel         263840  0 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tifm_7xx1               8832  0 
tifm_core              11652  1 tifm_7xx1
sdhci                  18828  0 
mmc_core               28420  1 sdhci
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
psmouse                39952  0 
serio_raw               8068  0 
snd                    54660  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
intel_agp              25620  1 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
agpgart                35016  3 drm,intel_agp
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  4 
ata_piix               17540  3 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  4 usbhid,ehci_hcd,uhci_hcd
processor              32072  2 thermal,acpi_cpufreq
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor
toshiba@Satellite:~$ 



toshiba@Satellite:~$ modinfo ath_pci
modinfo: could not open /lib/modules/2.6.22-14-generic/madwifi/ath_pci.ko: No such file or directory
toshiba@Satellite:~$

---

### Post by croto on 2008-03-26
According to the output of lspci, you don't have an atheros card, you have a 

Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

which is consistent with the driver controlling it (ipw3945, as reported by lsmod). So check on google if you can put this card in monitor mode, and if  it can do packet injection. 

Actually, it seems to be possible, check this out:  [http://www.aircrack-ng.org/doku.php?id=ipw3945](http://www.aircrack-ng.org/doku.php?id=ipw3945)

And forget about configuring the kernel.

---

### Post by thesteve151 on 2008-03-26
thanks for the help, i don't have wired internet, so i can't try that guide in the link just yet, i will have to go to a friends house, and try it another day, i will post up my results after i try it.

---

