---
title: "Wireless suddenly stopped working."
date: 2009-08-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dawynn on 2009-08-31
My family was using the laptop today when wireless suddenly stopped working.  Now, I can't get wireless to work in Jaunty or Karmic.  Any ideas?  Default system at this point is a mix of Linux Mint Gloria (xfce ce) and Karmic Xubuntu.

Here's what I retrieved from my system
(system was connected to a wired network at the time information was retrieved):
```

Computer: Compaq Presario C300
Distribution: Linux Mint Gloria + Karmic Xubuntu
Kernel: 2.6.31-8-generic i686

Hardware: 
(from lspci)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
(from lsusb)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

ifconfig result:
eth0      Link encap:Ethernet  HWaddr 00:16:d4:eb:b8:97  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:feeb:b897/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:998 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1373370 (1.3 MB)  TX bytes:138988 (138.9 KB)
          Interrupt:16 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1400 (1.4 KB)  TX bytes:1400 (1.4 KB)

iwconfig result:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod:
ipt_addrtype            2204  4 
ip6table_filter         3164  1 
ip6_tables             13004  1 ip6table_filter
iptable_filter          3100  1 
ip_tables              11692  1 iptable_filter
iwl3945                76636  0 
iwlcore               111804  1 iwl3945
mac80211              181140  2 iwl3945,iwlcore
led_class               4096  2 iwl3945,iwlcore
cfg80211               93084  3 iwl3945,iwlcore,mac80211

dmesg:
[    9.149342] udev: starting version 146
[    9.865610] cfg80211: Calling CRDA to update world regulatory domain
[   10.384497] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   10.384503] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   10.384631] iwl3945 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   10.384647] iwl3945 0000:06:00.0: setting latency timer to 64
[   10.447664] intel_rng: FWH not detected
[   10.448167] iwl3945 0000:06:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   10.448171] iwl3945 0000:06:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   10.448287]   alloc irq_desc for 27 on node -1
[   10.448290]   alloc kstat_irqs on node -1
[   10.448324] iwl3945 0000:06:00.0: irq 27 for MSI/MSI-X
[   10.761317] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   10.918115] cfg80211: World regulatory domain updated:
[   10.918120] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.918124] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.918127] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.918130] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.918133] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.918136] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.073866]   alloc irq_desc for 22 on node -1
[   11.073870]   alloc kstat_irqs on node -1
[   11.073879] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.073916] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.157934] type=1505 audit(1251766303.396:2): operation="profile_load" pid=1925 name=/usr/bin/freshclam
[   18.160648] type=1505 audit(1251766303.398:3): operation="profile_load" pid=1926 name=/sbin/dhclient3
[   18.161325] type=1505 audit(1251766303.398:4): operation="profile_load" pid=1926 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   18.161708] type=1505 audit(1251766303.398:5): operation="profile_load" pid=1926 name=/usr/lib/connman/scripts/dhclient-script
[   18.163483] type=1505 audit(1251766303.398:6): operation="profile_load" pid=1927 name=/usr/sbin/mysqld-akonadi
[   18.190720] type=1505 audit(1251766303.426:7): operation="profile_load" pid=1928 name=/usr/bin/evince
[   18.199656] type=1505 audit(1251766303.434:8): operation="profile_load" pid=1928 name=/usr/bin/evince-previewer
[   18.204979] type=1505 audit(1251766303.442:9): operation="profile_load" pid=1928 name=/usr/bin/evince-thumbnailer
[   18.227181] type=1505 audit(1251766303.462:10): operation="profile_load" pid=1929 name=/usr/lib/cups/backend/cups-pdf
[   18.227999] type=1505 audit(1251766303.462:11): operation="profile_load" pid=1929 name=/usr/sbin/cupsd
[   18.531190] ip_tables: (C) 2000-2006 Netfilter Core Team
[   18.565932] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   18.566367] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   18.566370] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   18.566373] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   18.611215] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   22.909599] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   30.283946] ppdev: user-space parallel port driver
[   31.602066] [drm] TV-14: set mode NTSC 480i 0
[   31.743157] [drm] TV-14: set mode NTSC 480i 0
[   32.041487] [drm] TV-14: set mode NTSC 480i 0
[   32.193486] [drm] TV-14: set mode NTSC 480i 0
[   33.548026] eth0: no IPv6 routers present

iwlist scan:
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wmaster0  Interface doesn't support scanning.
wlan0     Failed to read scan data : Network is down

```

Any help is appreciated.  Let me know if there is any other pertinent information that I can provide.

---

### Post by Peter09 on 2009-09-01
Check (if you have one) that the wireless on-off hardware switch has not been moved to off.

---

### Post by dawynn on 2009-09-01
Wow, do I feel really silly right now.  I'd looked around for such a switch last night and couldn't find one.  But I found it now, right next to the power switch.  OK, wireless is working again now.

---

### Post by biasquez on 2009-09-01
someone has intel 5100 AGN or use iwlagn driver? works fine for you?

---

### Post by MacUntu on 2009-09-01
Maybe it's helpful to someone: my iwl3945 wasn't working for weeks (timeouts, messages of MAC being in deep sleep). Yesterday I had finally time to investigate and loading the module with the fw_restart3945 option once fixed it (the card wasn't even working in Windows).

```
sudo stop network-manager
sudo killall wpa_supplicant
sudo modprobe -r iwl3945
sudo modprobe iwl3945 fw_restart3945=0
sudo start network-manager
```

Now it's working fine again. :)

---

