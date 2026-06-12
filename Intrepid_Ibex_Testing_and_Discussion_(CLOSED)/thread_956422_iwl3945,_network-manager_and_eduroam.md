---
title: "iwl3945, network-manager and eduroam"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ctrlER on 2008-10-23
Hi.

I have an Intel 3945 abg wireless card and I'm having problems connecting to the wireless network on my university (FEUP) that is using eduroam.
It connects ok but then drops after a while (5-15 minutes) and I can't reconnect. I have to reboot the system to be able to reconnect.

I'm using the following configuration with the latest Network Manager on Ubuntu 8.10:

SSID: eduroam
WPA Enterprise
TTLS
Phase2  PAP
CA Certificate: FEUP-CA-CERT.pem
login and password to access the network.

Network-manager version is 0.7~~svn20081018t105859-0ubuntu1.
uname -a: Linux ubuntu 2.6.27-7-generic #1 SMP Wed Oct 22 00:29:18 UTC 2008 i686 GNU/Linux

dmesg:

```
[   27.734024] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.739252] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   27.739456] iwl3945 0000:03:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   27.746386] firmware: requesting iwlwifi-3945-1.ucode
[   27.891520] Registered led device: iwl-phy0:radio
[   27.892576] Registered led device: iwl-phy0:assoc
[   27.893571] Registered led device: iwl-phy0:RX
[   27.894538] Registered led device: iwl-phy0:TX
[   27.901774] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.039216] NET: Registered protocol family 17
[   30.181448] wlan0: authenticate with AP 00:0e:d7:c3:3c:f0
[   30.183955] wlan0: authenticated
[   30.183966] wlan0: associate with AP 00:0e:d7:c3:3c:f0
[   30.186336] wlan0: RX AssocResp from 00:0e:d7:c3:3c:f0 (capab=0x421 status=0 aid=131)
[   30.186345] wlan0: associated
[   30.186749] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   30.198382] wlan0: disassociating by local choice (reason=3)
[   30.200690] wlan0: deauthenticated
[   31.196075] wlan0: authenticate with AP 00:0e:d7:c3:3c:f0
[   31.198928] wlan0: authenticated
[   31.198935] wlan0: associate with AP 00:0e:d7:c3:3c:f0
[   31.200762] wlan0: RX ReassocResp from 00:0e:d7:c3:3c:f0 (capab=0x421 status=0 aid=132)
[   31.200773] wlan0: associated
[   31.201847] wlan0: disassociating by local choice (reason=3)
[   31.203159] wlan0: deauthenticated
[   32.200186] wlan0: authenticate with AP 00:0e:d7:c3:3c:f0
[   32.201273] wlan0: authenticated
[   32.201281] wlan0: associate with AP 00:0e:d7:c3:3c:f0
[   32.202557] wlan0: RX ReassocResp from 00:0e:d7:c3:3c:f0 (capab=0x421 status=0 aid=133)
[   32.202564] wlan0: associated
[   32.204302] wlan0: disassociating by local choice (reason=3)
[   40.892107] wlan0: no IPv6 routers present
[   51.451331] wlan0: deauthenticated
[   51.451485] wlan0: authenticate with AP 00:0e:d7:c3:3c:f0
[   51.453261] wlan0: authenticated
[   51.453275] wlan0: associate with AP 00:0e:d7:c3:3c:f0
[   51.454630] wlan0: RX ReassocResp from 00:0e:d7:c3:3c:f0 (capab=0x421 status=0 aid=134)
[   51.454640] wlan0: associated
[   51.454996] wlan0: disassociating by local choice (reason=3)
[   81.555952] wlan0: deauthenticated
[   81.556147] wlan0: authenticate with AP 00:0e:d7:c3:3c:f0
[   81.557443] wlan0: authenticated
[   81.557452] wlan0: associate with AP 00:0e:d7:c3:3c:f0
[   81.558687] wlan0: RX ReassocResp from 00:0e:d7:c3:3c:f0 (capab=0x421 status=0 aid=135)
[   81.558694] wlan0: associated
[   81.559821] wlan0: disassociating by local choice (reason=3)
[  105.665643] CPU0 attaching NULL sched-domain.
[  105.665661] CPU1 attaching NULL sched-domain.
[  105.665825] CPU0 attaching sched-domain:
[  105.665832]  domain 0: span 0-1 level MC
[  105.665840]   groups: 0 1
[  105.665852] CPU1 attaching sched-domain:
[  105.665858]  domain 0: span 0-1 level MC
[  105.665864]   groups: 1 0
[  121.487408] wlan0: deauthenticated
[  121.487510] wlan0: authenticate with AP 00:0e:d7:c3:3c:f0
[  121.488880] wlan0: authenticated
[  121.488902] wlan0: associate with AP 00:0e:d7:c3:3c:f0
[  121.490091] wlan0: RX ReassocResp from 00:0e:d7:c3:3c:f0 (capab=0x421 status=0 aid=136)
[  121.490105] wlan0: associated
[  121.491321] wlan0: disassociating by local choice (reason=3)
[  121.492386] wlan0: deauthenticated
[  122.493096] wlan0: authenticate with AP 00:0e:d7:c3:3c:f0
[  122.494211] wlan0: authenticated
[  122.494223] wlan0: associate with AP 00:0e:d7:c3:3c:f0
[  122.495410] wlan0: RX ReassocResp from 00:0e:d7:c3:3c:f0 (capab=0x421 status=0 aid=137)
[  122.495422] wlan0: associated
[  122.496231] wlan0: disassociating by local choice (reason=3)
[  122.497418] wlan0: deauthenticated
[  123.496102] wlan0: authenticate with AP 00:0e:d7:c3:3c:f0
[  123.497200] wlan0: authenticated
[  123.497215] wlan0: associate with AP 00:0e:d7:c3:3c:f0
[  123.498385] wlan0: RX ReassocResp from 00:0e:d7:c3:3c:f0 (capab=0x421 status=0 aid=138)
[  123.498397] wlan0: associated
[  123.499023] wlan0: disassociating by local choice (reason=3)
[  172.465490] type=1503 audit(1224764553.877:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6014/net/" pid=6014 profile="/usr/sbin/cupsd"
[  172.465860] type=1503 audit(1224764553.877:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6014 profile="/usr/sbin/cupsd"
[  172.465915] type=1503 audit(1224764553.877:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6014 profile="/usr/sbin/cupsd"
[  172.465968] type=1503 audit(1224764553.877:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6014 profile="/usr/sbin/cupsd"
[  172.466021] type=1503 audit(1224764553.877:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6014 profile="/usr/sbin/cupsd"
[  172.466075] type=1503 audit(1224764553.877:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6014 profile="/usr/sbin/cupsd"
[  172.466135] type=1503 audit(1224764553.877:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6014 profile="/usr/sbin/cupsd"
[  172.466180] type=1503 audit(1224764553.877:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6014 profile="/usr/sbin/cupsd"
[  172.466232] type=1503 audit(1224764553.877:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6014 profile="/usr/sbin/cupsd"
[  172.466706] type=1503 audit(1224764553.877:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/6014/net/dev" pid=6014 profile="/usr/sbin/cupsd"
[  183.113053] wlan0: authenticate with AP 00:0e:d7:c3:3c:f0
[  183.114329] wlan0: authenticated
[  183.114342] wlan0: associate with AP 00:0e:d7:c3:3c:f0
[  183.115728] wlan0: deauthenticated
[  184.112113] wlan0: authenticate with AP 00:0e:d7:c3:3c:f0
[  184.113207] wlan0: authenticated
[  184.113221] wlan0: associate with AP 00:0e:d7:c3:3c:f0
[  184.114442] wlan0: RX AssocResp from 00:0e:d7:c3:3c:f0 (capab=0x431 status=0 aid=139)
[  184.114456] wlan0: associated
[  277.519950] wlan0: authenticate with AP 00:11:20:68:ad:f0
[  277.522921] wlan0: authenticate with AP 00:11:20:68:ad:f0
[  277.522950] wlan0: authenticated
[  277.522958] wlan0: associate with AP 00:11:20:68:ad:f0
[  277.526289] wlan0: RX ReassocResp from 00:11:20:68:ad:f0 (capab=0x431 status=0 aid=79)
[  277.526304] wlan0: associated
[  277.577217] wlan0: deauthenticated
[  278.576104] wlan0: authenticate with AP 00:11:20:68:ad:f0
[  278.577218] wlan0: authenticated
[  278.577231] wlan0: associate with AP 00:11:20:68:ad:f0
[  278.578460] wlan0: RX ReassocResp from 00:11:20:68:ad:f0 (capab=0x431 status=0 aid=80)
[  278.578466] wlan0: associated
[  292.786819] wlan0: disassociating by local choice (reason=3)
[  292.787700] wlan0: authenticate with AP 00:11:20:68:ad:f0
[  292.984142] wlan0: authenticate with AP 00:11:20:68:ad:f0
[  292.985224] wlan0: authenticated
[  292.985238] wlan0: associate with AP 00:11:20:68:ad:f0
[  292.986428] wlan0: RX AssocResp from 00:11:20:68:ad:f0 (capab=0x421 status=13 aid=0)
[  292.986440] wlan0: AP denied association (code=13)
[  293.184118] wlan0: associate with AP 00:11:20:68:ad:f0
[  293.185299] wlan0: deauthenticated
[  294.185105] wlan0: authenticate with AP 00:11:20:68:ad:f0
[  294.186205] wlan0: authenticated
[  294.186219] wlan0: associate with AP 00:11:20:68:ad:f0
[  294.187431] wlan0: RX AssocResp from 00:11:20:68:ad:f0 (capab=0x421 status=13 aid=0)
[  294.187443] wlan0: AP denied association (code=13)
```

Attached is the full dmesg output.

---

### Post by myddewji13 on 2008-10-23
i've tried eduroam at multiple campuses with no probs yet...initially it didnt work so i deleted the profile and tried again...and so far its still working ...sorry i cant really offer any help b/c im pretty new at this..

---

### Post by ctrlER on 2008-10-23
> **myddewji13 said:**
> i've tried eduroam at multiple campuses with no probs yet...initially it didnt work so i deleted the profile and tried again...and so far its still working ...sorry i cant really offer any help b/c im pretty new at this..
Hi. Thanks for the answer. I'm pretty new at this too.
Do you have an intel 3945 wireless card?

---

