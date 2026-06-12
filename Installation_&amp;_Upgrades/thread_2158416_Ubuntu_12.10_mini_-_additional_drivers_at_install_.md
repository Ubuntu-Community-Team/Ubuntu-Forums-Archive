---
title: "Ubuntu 12.10 mini - additional drivers at install time?"
date: 2013-06-28
forum: Installation &amp; Upgrades
---

### Post by fredfillis on 2013-06-28
I have been butting heads with the install for ubuntu 12.10 mini on and off for a few weeks now and getting nowhere.

I have a  [Shuttle XS35GSV3]("http://http://global.shuttle.com/news/productsSpec?productId=1587") which has been running the full version of 12.10 with XBMC. I've had a few issues with the video side of this setup so it has been recommended that I try the minimal version of 12.10 and only add what I need.

My basic issue is that while the install of the full version of 12.10 runs with no problem, the mini install always chokes (on the same machine) when it comes to the network. My shuttle has a wired connection that works with no problem. I've tried the install from CD and from USB. I've created various boot disks under  both Windows and 12.10 and always with the same reesult. I have checked the md5 checksums on the iso  files and everything appears correct.

When trying to install the mini, I see this.

[https://www.dropbox.com/s/95v2dlcxun...624_201344.jpg]("https://www.dropbox.com/s/95v2dlcxun3wgtd/20130624_201344.jpg")

Under 12.10, if I run ```
sudo lshw -C network
``` then I get the following:

 ```
   *-network               
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:02:00.5
       logical name: eth0
       version: 03
       serial: 80:ee:73:43:b4:f9
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.8 duplex=full ip=192.168.54.119 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:46 memory:d0200000-d0203fff ioport:d100(size=128) ioport:d000(size=256)
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 74:e5:43:ed:26:73
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.5.0-34-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 ioport:c000(size=256) memory:d0100000-d0103fff


```

I had originally thought that the driver for the wired connection was jme.ko but it appears that under 12.10 that module is not being loaded.

```
xbmc@luckybox:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12618  1 
des_generic            21192  0 
md4                    12524  0 
vesafb                 13478  1 
coretemp               13169  0 
arc4                   12474  2 
parport_pc             31969  0 
ppdev                  12818  0 
nls_utf8               12494  2 
rfcomm                 37277  0 
bnep                   17708  2 
cifs                  279958  4 
bluetooth             183270  10 rfcomm,bnep
microcode              18210  0 
fscache                50235  1 cifs
joydev                 17162  0 
snd_hda_codec_hdmi     31457  2 
snd_hda_codec_idt      59762  1 
lpc_ich                16926  0 
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_hda_intel          32516  0 
snd_hda_codec         111548  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                80235  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rtl8192ce              52880  0 
rtl8192c_common        47076  1 rtl8192ce
rtlwifi                64204  1 rtl8192ce
video                  18895  0 
snd_timer              24412  2 snd_seq,snd_pcm
fglrx                4325618  178 
mac80211              461261  3 rtl8192ce,rtl8192c_common,rtlwifi
snd                    62146  10 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq,snd_seq_device,snd_pcm,snd_timer
mac_hid                13038  0 
cfg80211              175574  2 rtlwifi,mac80211
jmb38x_ms              17178  0 
memstick               15843  1 jmb38x_ms
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 41734  0 
hid                    82179  2 hid_generic,usbhid
usb_storage            39351  1 
ahci                   25497  2 
libahci                25938  1 ahci
jme                    39501  0 
sdhci_pci              18156  0 
sdhci                  27831  1 sdhci_pci


```

What I'm now looking to find out, is what driver do I need to use and  how can I get the install to detect and use the correct driver?

---

