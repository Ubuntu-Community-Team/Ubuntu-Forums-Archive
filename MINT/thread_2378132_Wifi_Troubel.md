---
title: "Wifi Troubel"
date: 2017-11-20
forum: MINT
---

### Post by freekeek on 2017-11-20
Hello iam Freekeek. 
i have some troubel with my Wifi. somebody can help me fix this problem?
```

########## wireless info START ##########

Report from: 20 Nov 2017 16:27 CET +0100

Booted last: 20 Nov 2017 00:00 CET +0100

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    LinuxMint
Description:    Linux Mint 18.2 Sonya
Release:    18.2
Codename:    sonya

##### kernel ############################

Linux 4.8.0-53-generic #56~16.04.1-Ubuntu SMP Tue May 16 01:18:56 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Cinnamon

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    DeviceName: Realtek PCIe GBE Family Controller
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:831f]

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
    DeviceName: Realtek RTL8723DE 802.11 bgn 1x1 WiFi + BT 4.2 Combo Adapter 
    Subsystem: Hewlett-Packard Company Device [103c:8319]

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:b009 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0000:0538  
Bus 001 Device 002: ID 04f2:b5d5 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi                    16384  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF1]>  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::3b36:badd:3cd0:2950/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60278 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:127669948 (127.6 MB)  TX bytes:4597644 (4.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:731 errors:0 dropped:0 overruns:0 frame:0
          TX packets:731 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:72772 (72.7 KB)  TX bytes:72772 (72.7 KB)

##### iwconfig ##########################

eno1      no wireless extensions.

lo        no wireless extensions.
```

---

### Post by jeremy31 on 2017-11-20
Moved to Mint
Your wifi device is not supported in Linux at this time, possibly by the end of the year

---

