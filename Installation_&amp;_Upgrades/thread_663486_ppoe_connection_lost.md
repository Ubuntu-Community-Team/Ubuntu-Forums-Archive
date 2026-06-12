---
title: "ppoe connection lost"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by xamasutra on 2008-01-10
hello
i m in China and it s quite difficult to get some help here.
Well i had to replace my mother card with internet broken by a same one.
i had dual boot windows kubuntu working with connection.
Now connection working only with windows.

i desinstalled and reinstalled pppoeconf package: no change

pon dsl-provider give me an error in the etc/peers/dsl-provider with a line with provider provider provider writen like this 3 times.
ping is no working (uneable to reach)

what can i do?

i give below the listing of some commands on terminal to help you

max@headbrain:~$ sudo lshw -C network && ip link show
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth2
       version: 10
       serial: 00:19:21:20:b3:f7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.131 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
1: lo: <LOOPBACK,UP,10000> mtu 16436 qdisc noqueue
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth2: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:19:21:20:b3:f7 brd ff:ff:ff:ff:ff:ff
max@headbrain:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
max@headbrain:~$ lsmod
Module                  Size  Used by
rfcomm                 42136  2
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
i915                   25856  2
drm                    83348  3 i915
ppdev                  10244  0
cpufreq_powersave       2688  0
cpufreq_conservative     8072  0
cpufreq_ondemand        9612  0
cpufreq_userspace       5280  0
cpufreq_stats           7232  0
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
button                  8976  0
container               5504  0
video                  18060  0
sbs                    19592  0
dock                   10656  0
ac                      6148  0
battery                11012  0
ppp_generic            29332  0
slhc                    7552  1 ppp_generic
ipv6                  273892  8
lp                     12580  0
snd_intel8x0           34972  0
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            33152  0
af_packet              24840  4
snd_seq_midi            9600  0
serio_raw               8068  0
snd_rawmidi            25728  1 snd_seq_midi
parport_pc             37412  1
parport                37448  3 ppdev,lp,parport_pc
psmouse                39952  0
pcspkr                  4224  0
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
iTCO_wdt               11940  0
iTCO_vendor_support     4868  1 iTCO_wdt
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
intel_agp              25620  1
agpgart                35016  3 drm,intel_agp
evdev                  11136  3
ext3                  133896  2
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0
sr_mod                 17828  0
cdrom                  37536  1 sr_mod
sd_mod                 30336  6
8139cp                 25088  0
ata_generic             8452  0
usbhid                 29536  0
hid                    28928  1 usbhid
floppy                 60004  0
8139too                27776  0
mii                     6528  2 8139cp,8139too
ata_piix               17540  5
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  4 sg,sr_mod,sd_mod,libata
ehci_hcd               36492  0
uhci_hcd               26640  0
usbcore               138632  4 usbhid,ehci_hcd,uhci_hcd
thermal                14344  0
processor              32072  1 thermal
fan                     5764  0
fuse                   47124  5
apparmor               40728  0
commoncap               8320  1 apparmor


max@headbrain:~$ sudo ifconfig
[sudo] password for max:
eth2      Lien encap:Ethernet  HWaddr 00:19:21:20:B3:F7
          inet adr:192.168.0.131  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::219:21ff:fe20:b3f7/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:116 erreurs:0 :0 overruns:0 frame:0
          TX packets:111 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:9246 (9.0 KB) Octets transmis:10308 (10.0 KB)
          Interruption:20 Adresse de base:0xc000

lo        Lien encap:Boucle locale
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          Octets reçus:0 (0.0 b) Octets transmis:0 (0.0 b)


max@headbrain:~$ sudo dhclient eth2
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth2/00:19:21:20:b3:f7
Sending on   LPF/eth2/00:19:21:20:b3:f7
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth2 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.131 -- renewal in 264930 seconds

---

### Post by xamasutra on 2008-01-11
up

---

### Post by zvacet on 2008-01-11
If you have just one card 

```
sudo gedit /etc/network/interfaces
```

and replace eth2 with eth0.Save and close and try again to connect.

---

