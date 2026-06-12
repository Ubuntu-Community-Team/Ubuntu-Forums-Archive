---
title: "edgy to feisty on HP zv6000 -- network problems"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by jleasure on 2007-04-22
I expect some pain and suffering with my Broadcom BCM4306 wireless.. but I was hoping my WIRED connection would work!

(turns out the wireless headache was fixed by compiling the latest ndiswrapper / version 1.42)

fyi: lspci gives
```
03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```
edgy 6.10 used the 8139too driver by default, but feisty 7.04 tries the 8139cp first, then fails, and uses the 8139too:

```
Apr 22 15:06:10 gerard kernel: [   25.378589] 8139cp 0000:03:06.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Apr 22 15:06:10 gerard kernel: [   25.378595] 8139cp 0000:03:06.0: Try the "8139too" driver instead.
Apr 22 15:06:10 gerard kernel: [   25.381524] 8139too Fast Ethernet driver 0.9.28
Apr 22 15:06:10 gerard kernel: [   25.381610] ACPI: PCI Interrupt 0000:03:06.0[A] -> GSI 22 (level, low) -> IRQ 22
Apr 22 15:06:10 gerard kernel: [   25.382316] eth0: RealTek RTL8139 at 0xffffc2000004a400, 00:0f:b0:6c:1b:d4, IRQ 22
Apr 22 15:06:10 gerard kernel: [   25.382321] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'

```

Turning off wireless connections in Network Manager, the wired connection would connect then disconnect then connect .. back and forth.. and the following is in daemon.log:

```
Apr 22 15:41:37 gerard NetworkManager: <information>^ISWITCH: terminating current connection 'eth0' because it's no longer valid. 
Apr 22 15:41:37 gerard NetworkManager: <information>^IDeactivating device eth0. 

```

in kern.log:

```
Apr 22 15:41:16 gerard kernel: [ 2368.809326] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Apr 22 15:41:16 gerard kernel: [ 2368.809502] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr 22 15:41:21 gerard kernel: [ 2373.975287] eth0: link down
Apr 22 15:41:23 gerard kernel: [ 2375.628955] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Apr 22 15:41:23 gerard kernel: [ 2375.628976] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr 22 15:41:37 gerard kernel: [ 2390.025042] eth0: link down
Apr 22 15:41:38 gerard kernel: [ 2390.710937] eth0: no IPv6 routers present
Apr 22 15:41:39 gerard kernel: [ 2391.656652] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Apr 22 15:41:39 gerard kernel: [ 2391.656842] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr 22 15:41:45 gerard kernel: [ 2398.453543] eth0: link down

```




if I kill network manager, and run "dhclient eth0" myself, I seem to remain connected, but kern.log is spammed:
```
Apr 22 15:57:04 gerard kernel: [ 3355.552230] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Apr 22 15:57:05 gerard kernel: [ 3356.575167] eth0: link down
Apr 22 15:57:07 gerard kernel: [ 3358.160659] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Apr 22 15:57:08 gerard kernel: [ 3359.673647] eth0: link down
Apr 22 15:57:10 gerard kernel: [ 3361.303345] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Apr 22 15:57:11 gerard kernel: [ 3362.360787] eth0: link down
Apr 22 15:57:13 gerard kernel: [ 3363.911774] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Apr 22 15:57:14 gerard kernel: [ 3364.776174] eth0: link down
Apr 22 15:57:15 gerard kernel: [ 3366.425922] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Apr 22 15:57:16 gerard kernel: [ 3366.775663] eth0: link down
Apr 22 15:57:17 gerard kernel: [ 3368.437241] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Apr 22 15:57:18 gerard kernel: [ 3368.953878] eth0: link down
Apr 22 15:57:19 gerard kernel: [ 3370.532365] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Apr 22 15:57:21 gerard kernel: [ 3372.259914] eth0: link down
Apr 22 15:57:23 gerard kernel: [ 3373.884562] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Apr 22 15:57:23 gerard kernel: [ 3373.891811] eth0: link down
Apr 22 15:57:24 gerard kernel: [ 3375.560658] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Apr 22 15:57:26 gerard kernel: [ 3377.278466] eth0: link down
Apr 22 15:57:28 gerard kernel: [ 3378.912859] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Apr 22 15:57:28 gerard kernel: [ 3379.139025] eth0: link down
Apr 22 15:57:30 gerard kernel: [ 3380.798469] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

```


Thank you for reading and THANK YOU for any help!

Jason

---

### Post by hearty on 2007-04-23
I am facing similar prob on diff machine

```

root@zipf:~# uname -r
2.6.20-15-generic

```

```

root@zipf:~# cat /etc/issue
Ubuntu 7.04 \n \l


```
```

root@zipf:~# dmesg
[  119.465707] eth0: link up.
[  119.466779] [COLOR="Red"]ADDRCONF(NETDEV_CHANGE):[/COLOR] eth0: link becomes ready
[  124.832758] eth0: no IPv6 routers present
[  127.699482] eth0: link down.
[  128.507540] eth0: link up.
[  128.507557] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  128.907953] eth0: link down.
[  129.694124] eth0: link up.
[  129.695168] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  129.966659] eth0: link down.
[  130.794537] eth0: link up.
[  130.794554] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  131.367126] eth0: link down.
[  132.173463] eth0: link up.
[  132.173482] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  134.994976] eth0: link down.
[  136.538473] eth0: link up.
[  136.538495] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  138.714074] eth0: link down.
[  140.090841] eth0: link up.
[  140.090856] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  141.390888] eth0: link down.
[  142.222557] eth0: link up.
[  142.222573] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  143.495893] eth0: link down.
[  144.377198] eth0: link up.
[  144.377213] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  145.535406] eth0: link down.
[  146.430498] eth0: link up.
[  146.430513] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  147.015149] eth0: link down.
[  147.809415] eth0: link up.
[  147.809430] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  154.655985] eth0: no IPv6 routers present
[  167.737107] eth0: link down.
[  168.567053] eth0: link up.
[  168.567071] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  174.577393] eth0: no IPv6 routers present
[  178.406895] eth0: link down.
[  179.207197] eth0: link up.
[  179.207214] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  182.060574] eth0: link down.
[  182.876908] eth0: link up.
[  182.876926] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  188.764155] eth0: no IPv6 routers present
[  192.184034] eth0: link down.
[  192.973821] eth0: link up.
[  192.973838] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  194.731099] eth0: link down.
[  195.552255] eth0: link up.
[  195.552273] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  201.747831] eth0: no IPv6 routers present

```
```

root@zipf:~# lspci 
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP61 SMU (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control


```

---

