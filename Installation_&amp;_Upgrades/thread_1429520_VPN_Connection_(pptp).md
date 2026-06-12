---
title: "VPN Connection (pptp)"
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by phanto on 2010-03-14
Hi,

I tried since yesterday to get a VPN-connection but it seems that until now I'm not able to reach the Company-network. Our company use the pptp connection.
I tried many different setup's but without sucess. I use Ubuntu 9.10 and installed the pptp-manager.

Following settings:

Gateway (set)
Username (set)

MSCHAPv2 (check)
Point to point (check)
Stateful (check)
BSD (check)
Deflate (check)
TCP (check)

Below you find the result from the syslog, what can I do now?

```
Mar 14 13:03:58 snofla-desktop pptp[2767]: nm-pptp-service-2756 log[ctrlp_disp:pptp_ctrl.c:950]: PPTP_SET_LINK_INFO received from peer_callid 0
Mar 14 13:03:58 snofla-desktop pptp[2767]: nm-pptp-service-2756 log[ctrlp_disp:pptp_ctrl.c:953]:   send_accm is FFFFFFFF, recv_accm is FFFFFFFF
Mar 14 13:03:58 snofla-desktop pptp[2767]: nm-pptp-service-2756 warn[ctrlp_disp:pptp_ctrl.c:956]: Non-zero Async Control Character Maps are not supported!
Mar 14 13:03:58 snofla-desktop pppd[2759]: Connection terminated.
Mar 14 13:03:58 snofla-desktop NetworkManager: <info>  VPN plugin failed: 1
Mar 14 13:03:58 snofla-desktop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Mar 14 13:03:58 snofla-desktop pptp[2761]: nm-pptp-service-2756 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Mar 14 13:03:58 snofla-desktop pptp[2761]: nm-pptp-service-2756 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Mar 14 13:03:58 snofla-desktop pppd[2759]: Exit.
Mar 14 13:03:58 snofla-desktop pptp[2767]: nm-pptp-service-2756 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Mar 14 13:03:58 snofla-desktop pptp[2767]: nm-pptp-service-2756 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Mar 14 13:03:58 snofla-desktop pptp[2767]: nm-pptp-service-2756 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Mar 14 13:03:58 snofla-desktop NetworkManager: <info>  VPN plugin state changed: 6
Mar 14 13:03:58 snofla-desktop NetworkManager: <info>  VPN plugin state change reason: 0
Mar 14 13:03:58 snofla-desktop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Mar 14 13:03:58 snofla-desktop NetworkManager: <info>  (eth0): writing resolv.conf to /sbin/resolvconf
Mar 14 13:03:58 snofla-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
```

Hopefully somebody is able to give me the needed hint.

br phanto

---

### Post by demuxer on 2010-04-14
I have the same problem, my syslog :

 NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'MyVpnProfile' failed to connect: 'No VPN secrets!'.
Apr 14 11:05:52 karmicdesktop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.

HELP PLEASE

---

