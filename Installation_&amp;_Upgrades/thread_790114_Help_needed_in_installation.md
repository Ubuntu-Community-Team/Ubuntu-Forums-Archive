---
title: "Help needed in installation"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by MATHEWJOHN on 2008-05-11
I am getting an error while installing Ubuntu 7.10 

Here is the message
udevd-event[2254]: run program: /sbin/modprobe abnormal exit
[210.158539]end request: I/O error devfd0,sector 0

any one have idea???

---

### Post by housam on 2008-05-11
Did you checked the CD for errors ? did you verified the [[COLOR="Red"]_MD5Sums _[/COLOR]]("https://help.ubuntu.com/community/BurningIsoHowto#head-6788e413b69a8947c263c08d435f3e7fa8a3237d")for the downloaded ISO before burning ? what is the specs. of your machine ?

---

### Post by ajmorris on 2008-05-11
there is also a check cd integrity option in the menus somewhere, i cant remember exactly where, but iirc, its in the system menu somewhere.

AJ

---

### Post by MATHEWJOHN on 2008-05-11
cd recieved from the ubuntu... My system conf is P4 3Gh, 768 DDRram, I am trying to install this to its second HDD 20 GB one...

---

### Post by housam on 2008-05-11
I think there is something wrong with the HDD. reformat the HDD manually using the Gparted tool ( on the live CD ) and then create the needed partitions for installing Ubuntu. during the installation process choose the manual way and assign the partitions manually.

---

### Post by MATHEWJOHN on 2008-06-01
Please help I am new to Ubuntu. I have installed ubuntu 8.04 (dual boot XP)

My system configuration is P4 3 GHZ HT, Pentium orginal mother board, 768 MB DDR, 80 GB HDD (IDE), Shared Video memory.... 


My issue is that Ubuntu Hangs most of time.... I have extracted some from my syslog
*****************************************************************

Jun  1 20:19:19 Thekkadathu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jun  1 20:19:19 Thekkadathu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jun  1 20:19:19 Thekkadathu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun  1 20:19:19 Thekkadathu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jun  1 20:19:19 Thekkadathu NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Jun  1 20:19:19 Thekkadathu NetworkManager: <info>    address 192.168.1.5 
Jun  1 20:19:19 Thekkadathu NetworkManager: <info>    netmask 255.255.255.0 
Jun  1 20:19:19 Thekkadathu NetworkManager: <info>    broadcast 192.168.1.255 
Jun  1 20:19:19 Thekkadathu NetworkManager: <info>    gateway 192.168.1.1 
Jun  1 20:19:19 Thekkadathu NetworkManager: <info>    nameserver 192.168.1.1 
Jun  1 20:19:19 Thekkadathu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Jun  1 20:19:19 Thekkadathu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jun  1 20:19:19 Thekkadathu NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Jun  1 20:19:19 Thekkadathu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Jun  1 20:19:19 Thekkadathu avahi-daemon[4924]: Withdrawing address record for 192.168.1.5 on eth0.
Jun  1 20:19:19 Thekkadathu avahi-daemon[4924]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.5.
Jun  1 20:19:19 Thekkadathu avahi-daemon[4924]: Interface eth0.IPv4 no longer relevant for mDNS.
Jun  1 20:19:19 Thekkadathu avahi-daemon[4924]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.5.
Jun  1 20:19:19 Thekkadathu avahi-daemon[4924]: New relevant interface eth0.IPv4 for mDNS.
Jun  1 20:19:19 Thekkadathu avahi-daemon[4924]: Registering new address record for 192.168.1.5 on eth0.IPv4.
Jun  1 20:19:20 Thekkadathu NetworkManager: <info>  Clearing nscd hosts cache. 
Jun  1 20:19:20 Thekkadathu NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Jun  1 20:19:20 Thekkadathu NetworkManager: <info>  Activation (eth0) successful, device activated. 
Jun  1 20:19:20 Thekkadathu NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Jun  1 20:19:20 Thekkadathu NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Jun  1 20:19:20 Thekkadathu kernel: [   39.951287] NET: Registered protocol family 10
Jun  1 20:19:20 Thekkadathu kernel: [   39.951824] lo: Disabled Privacy Extensions
Jun  1 20:19:21 Thekkadathu ntpdate[5492]: adjust time server 91.189.94.4 offset -0.190255 sec
Jun  1 20:19:22 Thekkadathu avahi-daemon[4924]: Registering new address record for fe80::219:d1ff:fe3f:69e on eth0.*.
Jun  1 20:19:23 Thekkadathu kernel: [   42.762485] hda-intel: Invalid position buffer, using LPIB read method instead.
Jun  1 20:19:31 Thekkadathu kernel: [   50.862628] eth0: no IPv6 routers present
Jun  1 20:19:36 Thekkadathu NetworkManager: <info>  Updating allowed wireless network lists. 
Jun  1 20:19:36 Thekkadathu NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jun  1 20:39:13 Thekkadathu -- MARK --
Jun  1 20:59:13 Thekkadathu -- MARK --
*****************************************

pls help

---

