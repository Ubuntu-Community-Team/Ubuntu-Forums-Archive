---
title: "Post-Upgrade Network Interface and wicd Issues"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by mootpoint on 2008-10-31
Upgraded 8.04 64-bit to 8.10. Had some interesting issues with NVidia drivers, which I fixed. 

Networking anomalies:

1) I had wicd installed on 8.04. Still installed on 8.10. wicd is configured to automatically connect to my home wireless network, and to automatically bring up eth0 if there's a cable in it. At home, wireless network will connect successfully when the laptop is at home, and it boots up as one would expect (fast). 

However, away from home, I can't get wicd it to come up, even manually. During boot, the process hangs for 100 seconds as follows:

[   18.243942] ip_tables: (C) 2000-2006 Netfilter Core Team
[   18.280641] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.280723] iwlagn 0000:02:00.0: restoring config space at offset 0x1 (was 0x40100102, writing 0x40100106)
[   18.280890] firmware: requesting iwlwifi-4965-2.ucode
[   18.552850] Registered led device: iwl-phy0:radio
[   18.553446] Registered led device: iwl-phy0:assoc
[   18.554084] Registered led device: iwl-phy0:RX
[   18.554701] Registered led device: iwl-phy0:TX
[   18.585341] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.877402] NET: Registered protocol family 17
[  117.040246] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[  117.272088] ppdev: user-space parallel port driver
[  117.533252] type=1503 audit(1225463935.655:5): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/etc/krb5.conf" pid=5150 profile="/usr/sbin/cupsd"

If I interrupt the boot process with a Ctrl-Alt-Del during the 100-second pause, I'm informed that rc.S and rc.6 have been interrupted, and the bootup continues.

In either case, I have more stuff in ifconfig than I used to, and more than I need/want:

lo        Link encap:Local Loopback  
   <snip>
wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:97:68:39  
   <snip>
wlan0:avahi Link encap:Ethernet  HWaddr 00:1f:3b:97:68:39  
          inet addr:169.254.5.24  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3B-97-68-39-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Never used to have the wlan0:avahi, or the wmaster0. 

Hardware: HP Pavilion Laptop, here's the lspci for the two network interfaces:

02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

Anyway, I guess the question is what to do to solve the 100-second nonsense, and how do I get wicd working again?

m00t

P.S. Installed network-manager, which uninstalled wicd. No change in the "100-second pause during bootup" behavior.

---

