---
title: "ndiswrapper problems"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by thesheff17 on 2007-12-13
I have followed this link [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)
for my hp pavilion tx 1000 and the first time around I get it to work.  After I reboot I have the same issue over and over.  I try to remove the module re-install everything and go through it again and I still have the ndiswrapper fail.

here is my output when I try to bring up the eth1.  I don't know what to try anymore and I have worked on it for about 8 hrs.  Any help would be greatly appreciated.  I am running ubuntu x86_64 ubuntu 7.10


root@thesheff17-laptop:~# ifup eth1
eth1: ERROR while getting interface flags: No such device
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'eth1' UP
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWAUTH]: No such device
WEXT auth param 7 value 0x0 - Failed to disable WPA in the driver.
ioctl[SIOCSIWAUTH]: No such device
WEXT auth param 5 value 0x0 - ioctl[SIOCSIWAUTH]: No such device
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAP]: No such device
ioctl[SIOCGIFFLAGS]: No such device
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
There is already a pid file /var/run/dhclient.eth1.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.

Here is me scanning the network and it not working even though it worked once.
 iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by thesheff17 on 2007-12-14
I don't know what I did but I have fixed the problem.

---

