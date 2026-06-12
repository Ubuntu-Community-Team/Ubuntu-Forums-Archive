---
title: "LTSP fails: client boot error PXE-061: Media test failure"
date: 2012-07-10
forum: Installation &amp; Upgrades
---

### Post by JD Hupp on 2012-07-10
[SIZE=-1][FONT=Arial]I have been trying to get an LTSP server and client running, but so far have failed with several approaches. All attempts have ended with the client boot error "PXE-061: Media test failure."[/FONT][/SIZE]
 
[SIZE=-1][FONT=Arial]--------[/FONT][/SIZE]
 
[SIZE=-1][FONT=Arial]WITH UBUNTU:[/FONT][/SIZE]
 
[SIZE=-1][FONT=Arial]With Ubuntu 12.04 32-Bit Alternate Install CD, and setting F4 Modes to Install an LTSP Server, I understand that with two network cards installed, the installer should automatically set up a ready-to-serve LTSP server. Just connect your client to eth1 (the secondary network interface) and boot.[/FONT][/SIZE]
 
[SIZE=-1][FONT=Arial]This Ubuntu attempt used a PC with Intel Celeron 2.8GHz, 512MB, and plenty of hard drive space. I tried 3 different client PC's set to network boot. I also tried booting clients with eth0 on the server not connected to the network just in case there was an IP conflict in play.[/FONT][/SIZE]
 
[SIZE=-1][FONT=Arial]System Monitor on the server does not show any processes running named LTSP-something or Terminal-something.[/FONT][/SIZE]
 
[SIZE=-1][FONT=Arial]--------[/FONT][/SIZE]
 
[SIZE=-1][FONT=Arial]WITH LUBUNTU:[/FONT][/SIZE]
 
[SIZE=-1][FONT=Arial]I also tried Lubuntu 12.04 32-Bit Alternate Install, which does not have an F4 option to Install an LTSP Server. Then I used this procedure for manually setting up the LTSP Server:[/FONT][/SIZE]
 
[SIZE=-1][FONT=Arial]Preferences: Network Connections: edit Wired Connection 1 (eth1), [/FONT][/SIZE][SIZE=-1][FONT=Arial]IPv4 tab:[/FONT][/SIZE]
[SIZE=-1][FONT=Arial]Auto &#8211;> Manual[/FONT][/SIZE]
[SIZE=-1][FONT=Arial]IP: 192.168.1.1[/FONT][/SIZE]
[SIZE=-1][FONT=Arial]SNM: 255.255.0.0[/FONT][/SIZE]
[SIZE=-1][FONT=Arial]Gateway: none[/FONT][/SIZE]
[SIZE=-1][FONT=Arial]DNS server: none[/FONT][/SIZE]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[SIZE=-1][FONT=Arial]Run: LXTerminal[/FONT][/SIZE]
[SIZE=-1][FONT=Arial]sudo apt-get install ltsp-server-standalone openssh-server[/FONT][/SIZE]
[SIZE=-1][FONT=Arial]sudo ltsp-build-client --arch i386[/FONT][/SIZE]
[SIZE=-1][FONT=Arial]sudo leafpad /etc/ltps/dhcpd.conf[/FONT][/SIZE]
[SIZE=-1][FONT=Arial](edit dhcpd.conf to change every 192.168.0.x &#8211;> 192.168.1.x so as not to conflict with my modem at 192.168.0.1)[/FONT][/SIZE]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[SIZE=-1][FONT=Arial]Reboot and test[/FONT][/SIZE]
 
[SIZE=-1][FONT=Arial]I also tried the Lubuntu setup with eth1 set to 192.168.0.1 and DHCPD.CONF in its default configuration to support that, but I got the same failure error.[/FONT][/SIZE]
 
[SIZE=-1][FONT=Arial]--------[/FONT][/SIZE]
 
[SIZE=-1][FONT=Arial]What do I look at next?[/FONT][/SIZE]
 
[SIZE=-1][FONT=Arial]--John[/FONT][/SIZE]

---

