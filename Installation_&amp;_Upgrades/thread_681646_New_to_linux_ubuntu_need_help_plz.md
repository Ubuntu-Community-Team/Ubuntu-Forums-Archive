---
title: "New to linux ubuntu need help plz"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by pfairfield on 2008-01-29
hi guys i tryed ubuntu7.10 on VMware and from the live cd i have also seen the youtube videos of wat it can do am now fed up with windows and really wont to cross over so i went be on the install from the live cd but first let me give u info on my pc

E6600
JW-ip35 pro mobo
sata2 samsung Hdd
2gb DDR2 800mhz
and ATI readon X1950pro ultimate (i no there is big problems with ATI cards)
also am runing this on a 32" philips HDtv (PAL)

so after the install is all said  and done and it tells me to remove the disk i do so then when it boots up i get past the grub (think it was called) part and i get a blank screen nothing else i download drivers that peeps said that work but how can i get them to stick in live cd mode i let it download the restricted drivers and install it then says reset to take effect to when doing so nothing happens and when am back in the live cd they have not installed or stuck so any help would be great cos i love the way ubuntu 7.10 looks and runs i really hate windows cheers guys

---

### Post by DeusEx on 2008-01-29
when booting from your harddisk, e.g. not using the Live CD, after getting blank screen try hitting ctrl+alt+F3.
This switches to another linux screen. Switching back would be ctrl+alt+F7.
In the other screen, a terminal window should appear. This mostly works. Try to find out what goes wrong:
```

dmesg

```

shows some info.

```

cat /var/log/syslog

```

does too.

I am guessing the installer picked a resolution your screen doesn't support. Also post the contents of /etc/X11/xorg.conf (this is the config file for your grafical environment).

---

### Post by pfairfield on 2008-01-29
CHEERS!!! that ctrl+alt+F3 worked a treat just about to install the updates and restricted drivers just hoping it dont fook it up and when i paste /etc/X11/xorg.conf in the terminal i get this paul@paul-desktop:~$ /etc/X11/xorg.conf
bash: /etc/X11/xorg.conf: Permission denied


paul@paul-desktop:~$ cat /var/log/syslog
Jan 29 13:34:26 paul-desktop syslogd 1.4.1#21ubuntu3: restart.
Jan 29 13:34:26 paul-desktop anacron[5317]: Job `cron.daily' terminated
Jan 29 13:36:56 paul-desktop avahi-daemon[5210]: Files changed, reloading.
Jan 29 13:36:56 paul-desktop avahi-daemon[5210]: No service file found in /etc/avahi/services.
Jan 29 13:36:57 paul-desktop avahi-daemon[5210]: Got SIGTERM, quitting.
Jan 29 13:36:57 paul-desktop avahi-daemon[5210]: Leaving mDNS multicast group on interface eth1.IPv4 with address 86.4.81.196.
Jan 29 13:39:07 paul-desktop kernel: [  638.057378] Failure registering capabilities with primary security module.
Jan 29 13:39:07 paul-desktop avahi-daemon[13057]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Jan 29 13:39:07 paul-desktop avahi-daemon[13057]: Successfully dropped root privileges.
Jan 29 13:39:07 paul-desktop avahi-daemon[13057]: avahi-daemon 0.6.20 starting up.
Jan 29 13:39:07 paul-desktop avahi-daemon[13057]: Successfully called chroot().
Jan 29 13:39:07 paul-desktop avahi-daemon[13057]: Successfully dropped remaining capabilities.
Jan 29 13:39:07 paul-desktop avahi-daemon[13057]: No service file found in /etc/avahi/services.
Jan 29 13:39:07 paul-desktop avahi-daemon[13057]: Joining mDNS multicast group on interface eth1.IPv4 with address 86.4.81.196.
Jan 29 13:39:07 paul-desktop avahi-daemon[13057]: New relevant interface eth1.IPv4 for mDNS.
Jan 29 13:39:07 paul-desktop avahi-daemon[13057]: Network interface enumeration completed.
Jan 29 13:39:07 paul-desktop avahi-daemon[13057]: Registering new address record for fe80::2e0:61ff:fe06:c0b0 on eth1.*.
Jan 29 13:39:07 paul-desktop avahi-daemon[13057]: Registering new address record for 86.4.81.196 on eth1.IPv4.
Jan 29 13:39:07 paul-desktop avahi-daemon[13057]: Registering HINFO record with values 'I686'/'LINUX'.
Jan 29 13:39:07 paul-desktop anacron[5317]: Job `cron.weekly' started
Jan 29 13:39:08 paul-desktop anacron[13087]: Updated timestamp for job `cron.weekly' to 2008-01-29
Jan 29 13:39:08 paul-desktop avahi-daemon[13057]: Server startup complete. Host name is paul-desktop.local. Local service cookie is 1800708954.
Jan 29 13:39:10 paul-desktop syslogd 1.4.1#21ubuntu3: restart.
Jan 29 13:39:10 paul-desktop anacron[5317]: Job `cron.weekly' terminated
Jan 29 13:40:08 paul-desktop NetworkManager: <WARN>  nm_signal_handler(): Caught signal 15, shutting down normally. 
Jan 29 13:40:08 paul-desktop NetworkManager: <info>  Caught terminiation signal 
Jan 29 13:40:08 paul-desktop NetworkManager: <debug> [1201614008.189789] nm_print_open_socks(): Open Sockets List: 
Jan 29 13:40:08 paul-desktop NetworkManager: <debug> [1201614008.189807] nm_print_open_socks(): Open Sockets List Done. 
Jan 29 13:40:08 paul-desktop NetworkManager: <info>  Deactivating device eth0. 
Jan 29 13:40:08 paul-desktop NetworkManager: <info>  Deactivating device eth1. 
Jan 29 13:40:08 paul-desktop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 5447
Jan 29 13:40:08 paul-desktop dhclient: killed old client process, removed PID file
Jan 29 13:40:08 paul-desktop dhclient: DHCPRELEASE on eth1 to 80.5.160.21 port 67
Jan 29 13:40:08 paul-desktop avahi-daemon[13057]: Withdrawing address record for 86.4.81.196 on eth1.
Jan 29 13:40:08 paul-desktop avahi-daemon[13057]: Leaving mDNS multicast group on interface eth1.IPv4 with address 86.4.81.196.
Jan 29 13:40:08 paul-desktop avahi-daemon[13057]: Interface eth1.IPv4 no longer relevant for mDNS.
Jan 29 13:40:09 paul-desktop avahi-daemon[13057]: Withdrawing address record for fe80::2e0:61ff:fe06:c0b0 on eth1.
Jan 29 13:40:09 paul-desktop kernel: [  699.671823] sky2 eth1: disabling interface
Jan 29 13:40:09 paul-desktop NetworkManager: <info>  starting... 
Jan 29 13:40:09 paul-desktop kernel: [  699.696558] sky2 eth1: enabling interface
Jan 29 13:40:09 paul-desktop kernel: [  699.700557] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jan 29 13:40:09 paul-desktop NetworkManager: <info>  eth1: Device is fully-supported using driver 'sky2'. 
Jan 29 13:40:09 paul-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jan 29 13:40:09 paul-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jan 29 13:40:09 paul-desktop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth1'. 
Jan 29 13:40:09 paul-desktop NetworkManager: <info>  Deactivating device eth1. 
Jan 29 13:40:09 paul-desktop kernel: [  699.763862] r8169: eth0: link down
Jan 29 13:40:09 paul-desktop kernel: [  699.765331] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 29 13:40:09 paul-desktop NetworkManager: <info>  eth0: Device is fully-supported using driver 'r8169'. 
Jan 29 13:40:09 paul-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jan 29 13:40:09 paul-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jan 29 13:40:09 paul-desktop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Jan 29 13:40:09 paul-desktop NetworkManager: <info>  Deactivating device eth0. 
Jan 29 13:40:09 paul-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Jan 29 13:40:09 paul-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jan 29 13:40:10 paul-desktop kernel: [  701.406701] sky2 eth1: Link is up at 100 Mbps, full duplex, flow control both
Jan 29 13:40:10 paul-desktop kernel: [  701.408239] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jan 29 13:40:10 paul-desktop NetworkManager: <info>  Will activate wired connection 'eth1' because it now has a link. 
Jan 29 13:40:10 paul-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Jan 29 13:40:10 paul-desktop NetworkManager: <info>  Will activate connection 'eth1'. 
Jan 29 13:40:10 paul-desktop NetworkManager: <info>  Device eth1 activation scheduled... 
Jan 29 13:40:10 paul-desktop NetworkManager: <info>  Activation (eth1) started... 
Jan 29 13:40:10 paul-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 29 13:40:10 paul-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jan 29 13:40:10 paul-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jan 29 13:40:10 paul-desktop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jan 29 13:40:10 paul-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jan 29 13:40:10 paul-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Jan 29 13:40:10 paul-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan 29 13:40:10 paul-desktop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jan 29 13:40:10 paul-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Jan 29 13:40:11 paul-desktop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Jan 29 13:40:11 paul-desktop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Jan 29 13:40:11 paul-desktop NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Jan 29 13:40:11 paul-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Jan 29 13:40:12 paul-desktop avahi-daemon[13057]: Registering new address record for fe80::2e0:61ff:fe06:c0b0 on eth1.*.
Jan 29 13:40:13 paul-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Jan 29 13:40:16 paul-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Jan 29 13:40:16 paul-desktop dhclient: DHCPOFFER from 10.137.196.1
Jan 29 13:40:16 paul-desktop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Jan 29 13:40:16 paul-desktop dhclient: DHCPACK from 10.137.196.1
Jan 29 13:40:16 paul-desktop avahi-daemon[13057]: Joining mDNS multicast group on interface eth1.IPv4 with address 86.4.81.196.
Jan 29 13:40:16 paul-desktop avahi-daemon[13057]: New relevant interface eth1.IPv4 for mDNS.
Jan 29 13:40:16 paul-desktop avahi-daemon[13057]: Registering new address record for 86.4.81.196 on eth1.IPv4.
Jan 29 13:40:16 paul-desktop avahi-daemon[13057]: Withdrawing address record for 86.4.81.196 on eth1.
Jan 29 13:40:16 paul-desktop avahi-daemon[13057]: Leaving mDNS multicast group on interface eth1.IPv4 with address 86.4.81.196.
Jan 29 13:40:16 paul-desktop avahi-daemon[13057]: Interface eth1.IPv4 no longer relevant for mDNS.
Jan 29 13:40:16 paul-desktop avahi-daemon[13057]: Joining mDNS multicast group on interface eth1.IPv4 with address 86.4.81.196.
Jan 29 13:40:16 paul-desktop avahi-daemon[13057]: New relevant interface eth1.IPv4 for mDNS.
Jan 29 13:40:16 paul-desktop avahi-daemon[13057]: Registering new address record for 86.4.81.196 on eth1.IPv4.
Jan 29 13:40:16 paul-desktop avahi-daemon[13057]: Withdrawing address record for 86.4.81.196 on eth1.
Jan 29 13:40:16 paul-desktop avahi-daemon[13057]: Leaving mDNS multicast group on interface eth1.IPv4 with address 86.4.81.196.
Jan 29 13:40:16 paul-desktop avahi-daemon[13057]: Interface eth1.IPv4 no longer relevant for mDNS.
Jan 29 13:40:16 paul-desktop avahi-daemon[13057]: Joining mDNS multicast group on interface eth1.IPv4 with address 86.4.81.196.
Jan 29 13:40:16 paul-desktop avahi-daemon[13057]: New relevant interface eth1.IPv4 for mDNS.
Jan 29 13:40:16 paul-desktop avahi-daemon[13057]: Registering new address record for 86.4.81.196 on eth1.IPv4.
Jan 29 13:40:16 paul-desktop dhclient: bound to 86.4.81.196 -- renewal in 1576 seconds.
Jan 29 13:40:16 paul-desktop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Jan 29 13:40:16 paul-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Jan 29 13:40:16 paul-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Jan 29 13:40:16 paul-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.domain_name
Jan 29 13:40:16 paul-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Jan 29 13:40:16 paul-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Jan 29 13:40:16 paul-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Jan 29 13:40:16 paul-desktop NetworkManager: <info>    address 86.4.81.196 
Jan 29 13:40:16 paul-desktop NetworkManager: <info>    netmask 255.255.252.0 
Jan 29 13:40:16 paul-desktop NetworkManager: <info>    broadcast 255.255.255.255 
Jan 29 13:40:16 paul-desktop NetworkManager: <info>    gateway 86.4.80.1 
Jan 29 13:40:16 paul-desktop NetworkManager: <info>    nameserver 194.168.4.100 
Jan 29 13:40:16 paul-desktop NetworkManager: <info>    nameserver 194.168.8.100 
Jan 29 13:40:16 paul-desktop NetworkManager: <info>    hostname 'paul-desktop' 
Jan 29 13:40:16 paul-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jan 29 13:40:16 paul-desktop NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Jan 29 13:40:16 paul-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Jan 29 13:40:16 paul-desktop avahi-daemon[13057]: Withdrawing address record for 86.4.81.196 on eth1.
Jan 29 13:40:16 paul-desktop avahi-daemon[13057]: Leaving mDNS multicast group on interface eth1.IPv4 with address 86.4.81.196.
Jan 29 13:40:16 paul-desktop avahi-daemon[13057]: Interface eth1.IPv4 no longer relevant for mDNS.
Jan 29 13:40:16 paul-desktop avahi-daemon[13057]: Withdrawing address record for fe80::2e0:61ff:fe06:c0b0 on eth1.
Jan 29 13:40:16 paul-desktop avahi-daemon[13057]: Joining mDNS multicast group on interface eth1.IPv4 with address 86.4.81.196.
Jan 29 13:40:16 paul-desktop avahi-daemon[13057]: New relevant interface eth1.IPv4 for mDNS.
Jan 29 13:40:16 paul-desktop avahi-daemon[13057]: Registering new address record for 86.4.81.196 on eth1.IPv4.
Jan 29 13:40:17 paul-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Jan 29 13:40:17 paul-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Jan 29 13:40:17 paul-desktop NetworkManager: <info>  Activation (eth1) successful, device activated. 
Jan 29 13:40:17 paul-desktop NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Jan 29 13:40:17 paul-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Jan 29 13:40:17 paul-desktop ntpdate[16422]: adjust time server 91.189.94.4 offset 0.039204 sec
Jan 29 13:40:18 paul-desktop avahi-daemon[13057]: Registering new address record for fe80::2e0:61ff:fe06:c0b0 on eth1.*.
Jan 29 13:40:25 paul-desktop kernel: [  716.008976] audit(1201614025.220:4):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=16700 profile="/usr/sbin/cupsd"
Jan 29 13:40:27 paul-desktop kernel: [  717.984134] eth1: no IPv6 routers present
paul@paul-desktop:~$

---

### Post by DeusEx on 2008-01-29
xorg.conf: that's a permissions thing try
```

sudo cat /etc/X11/xorg.conf

```

your syslog isn't telling anything about your graphics card unfortunately...

---

### Post by starscalling on 2008-02-01
try doing 
sudo lspci -vvv
and if you want live help feel free to come to the irc channel on freenode ;)

---

