---
title: "No internet connection ..."
date: 2006-07-15
forum: Installation &amp; Upgrades
---

### Post by Turtle.net on 2006-07-15
Hi,
That's not my first installation of ubuntu ... but it seems that I still have some issues.
I just bought an e-machines H6216.
I tried live-cd for x86 and live-cd for amd64, and in both cases everything seems ok...but i do not ha an internet connection.
Here are some more details :
I have two ethernet ports (one directly from the motherboard, the other from a PCI car from Dynex the DX-E101).
```
ubuntu@ubuntu:~$ lspci
...
0000:00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
...
0000:04:06.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
...
ubuntu@ubuntu:~$ dmesg | grep eth
[4294677.900000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.48.
[4294678.413000] eth0: forcedeth.c: subsystem: 01462:7207 bound to 0000:00:14.0
[4294683.856000] Driver 'sd' needs updating - please use bus_type methods
[4294707.332000] eth1: VIA Rhine III at 0x1e800, 00:0f:3d:7e:51:0b, IRQ 50.
[4294707.333000] eth1: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
[4294723.902000] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294724.044000] eth0: no link during initialization.
[4294754.978000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[4294765.734000] eth1: no IPv6 routers present
[4294831.459000] eth1: link down
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
nls_utf8                2176  1
vfat                   13440  1
fat                    53020  1 vfat
ipv6                  265600  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
lp                     11844  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
ac                      5252  1 acpi_sbs
dm_mod                 58936  1
md_mod                 72532  0
tsdev                   8000  0
snd_hda_intel          18964  1
snd_hda_codec         142640  1 snd_hda_intel
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
pcspkr                  2180  0
psmouse                36228  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
rtc                    13492  0
serio_raw               7300  0
soundcore              10208  1 snd
af_packet              22920  4
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm
shpchp                 45632  0
agpgart                34888  0
i2c_core               21904  1 i2c_acpi_ec
pci_hotplug            29236  1 shpchp
sg                     37920  0
evdev                   9856  1
via_rhine              23940  0
mii                     5888  1 via_rhine
sd_mod                 19984  2
squashfs               44980  1
unionfs                89884  1
loop                   17288  2
nls_cp437               5888  2
isofs                  37688  1
usb_storage            74176  2
ide_generic             1536  0
ehci_hcd               32008  0
ohci_hcd               21892  0
usbcore               129668  4 usb_storage,ehci_hcd,ohci_hcd
forcedeth              23428  0
ide_cd                 33028  1
cdrom                  38560  1 ide_cd
ide_disk               17664  1
generic                 5124  0
amd74xx                15132  0 [permanent]
sata_nv                 9604  0
libata                 78992  1 sata_nv
scsi_mod              139496  4 sg,sd_mod,usb_storage,libata
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D3:EC:09:EF
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0x8000

eth1      Link encap:Ethernet  HWaddr 00:0F:3D:7E:51:0B
          inet6 addr: fe80::20f:3dff:fe7e:510b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1095 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:67210 (65.6 KiB)  TX bytes:2520 (2.4 KiB)
          Interrupt:50 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2740 (2.6 KiB)  TX bytes:2740 (2.6 KiB)

``` Sorry for this long post.
I hope someonewill be able to help me.

-----

Ok I solved the problem ... but I don't know why, I have done the set up several times ... and suddenly it worked...

---

### Post by halitech on 2006-07-18
ok, what did you do that seemed to fix the issue?

---

### Post by Turtle.net on 2006-07-19
The last thing I have done where : shutting down the PC, unplugging the power source for several minutes, rebooting the cable modem, starting ubuntu (after plugging back the power source obviously) and setting up (again) eth0 for DHCP and manually typing the DNS server adresses....

I don't know if that can help.

Good luck

---

