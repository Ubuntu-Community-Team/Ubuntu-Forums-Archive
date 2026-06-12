---
title: "Wireless - WEP problems in Kubuntu Jaunty Beta Live"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by vaclavpe on 2009-04-05
Hello all,

I want to replace my old Suse10.0 with Kubuntu, therefore I downloaded 9.04 beta and tried Live version. But I did not succeded to set wireless connection with my Orinoco 626 card.

In KDE connection manager I choose my AP, set "Infrastructure", WEP passphrase, password, manual IP address.

There are three points, which I am not sure about:
- In LIVE version I have my wireless card as ETH1 - no standard WLAN0.
- KDE ConMgr does not store Netmask correctly. I set 255.255.255.0 and it is replaced by 0
- with "iwconfig" I see changes only in "Rx invalid crypt" item. Others are zeros.

Overall, I can't get connected.

In Suse, I have following working setup: ESSID, managed mode, Shared key, ASCII, manual IP addres

I don't want to replace my old system until I solve this connection problem.

Can somebody help me out ? I can send any output needed.

Thank you in advance.

---

### Post by vaclavpe on 2009-04-05
... story continues ...

If I run following commands from command line, it works well:
 > sudo iwconfig eth1 essid VPLan
 > sudo iwconfig eth1 key restricted dead-beef-00
 > sudo ifconfig eth1 192.168.1.99 up
 > sudo route add default gw 192.168.1.254
 > echo nameserver 192.168.1.254 > /etc/resolv.conf

I use WEP with hexadecimal key.

In fact, I am filling this bug from system configured that way. "Network management" icon is anyway not aware that I have connection and says "eth1: Not connected".

If KDE Network Manager is not able to set this network, where should I put the manual configuration to have the connection permanent after each boot of the system ? And preferably, to see that I am connected ?

---

### Post by CyberMando on 2009-04-05
The manual configuration should go in /etc/network/intefaces. If this is a laptop that you will want to connect to other access points at times, you should look into wicd.
sudo aptitude install wicd
would get it installed and it will work as it should. Be aware though that wicd does not run the post connect scripts that are in /etc/network/if-up.d. These are run if you configure the network in interfaces.

---

### Post by vishalrao on 2009-04-06
i uninstalled the network manager plasmoid and installed network-manager-gnome (nm-applet) for vpn/pptp and static ip and wireless support... working well here...

---

### Post by vaclavpe on 2009-04-06
I chose wicd 1.5.9. Currently it works but seems does not work automatically. Furthermore, I have tray icon (just run "wicd-client") and if I click on it, it opens empty manager window.

So i will see. If I will not be satisfied, I will try nm-applet.

Anyway, I would prefer straight kde network manager - if it were not buggy. But I somewhere found that it can not handle manual IP addresses, that's the main problem.

---

