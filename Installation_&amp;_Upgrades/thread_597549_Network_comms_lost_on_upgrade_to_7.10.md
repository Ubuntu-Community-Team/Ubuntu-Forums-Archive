---
title: "Network comms lost on upgrade to 7.10"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by axe_mad on 2007-10-30
I am a complete novice on Ubuntu and I am in need of some help explained in a very simple way. 
I have been happily using Ubuntu :) (previous release to 7.10) for internet access and have always selected to update the software. After upgrading the OS to 7.10 a few days ago using the automatic update appeared to upgrade without any errors but after the reboot there was no connection to the net :confused:. Using Network Tools the only network device listed is Loopback Interface (lo). PLEASE HELP! I am using a borrowed computer now. The connection is a  wired link from the onboard ethernet ASUS A7V600 motherboard. I can't even access the modem setup.

:guitar:

---

### Post by vambo on 2007-10-30
Go to Network . For Wired Connection, if it indicates "Roaming Config" ( or something very like that I don't quite recall), select the connection then select Properties. Change to dhcp and that (fingers crossed) should be you.

---

### Post by axe_mad on 2007-10-30
Thanks but still no good:( on the Network settings - Wired connection is ticked and address: dhcp. Location is blank. I have tried a reboot after changing settings, not sure if that is necessary:-k My gut feeling is that the network card is not being picked up. The Lan led on the modem is off when normally it is on to indicate a connection. On one reboot it preformed a 'system check' and there was an item marked [fail] but it was too fast to read before the splash screen.

---

### Post by signtist on 2007-10-30
I have a similar/ same problem. after update, ubuntu does not see my wireless network device. I only have modem (which I do not have ) and Ethernet.

this is when I start the 'normal' way - meaning in the grub starter menu the pre-set which starts after a couple of seconds:

**Ubuntu 7.10,kernel 2.6.22-14-386**

but if I choose to start:

**Ubuntu 7.10,kernel 2.6.22.15-generi**c (what is the diffrence anyway?)

my internet works! and ubuntu sees the the wireless network

---

### Post by vambo on 2007-10-30
Doesn't look to promising.

Have a look in /etc/network/interfaces, and see if you have an entry like this

> iface eth0 inet dhcp

If you have try the following at the terminal.

```
sudo ifup -a
```

Hope it helps, but to be honest I'm not optimistic. Smells of driver trouble.

---

### Post by axe_mad on 2007-10-30
The nerest entry is

auto eth1 #iface eth1 inet dhcp

 and the sudo ifup -a gives an 'Ignoring unknown interface eth1=eth1' etc

Is there a way back to the previous version :) without a full install ?

back tomorrow 
cheers all

:guitar:

---

### Post by signtist on 2007-10-30
I have the entry  > iface etho inet dhcp 

if I enter > sudo ifup -a 

i get the following

```
Ignoring unknown interface eth2=eth2.
Ignoring unknown interface ath0=ath0.
Ignoring unknown interface wlan0=wlan0.
ra1: ERROR while getting interface flags: No such device
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device ra1 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ra1 ; No such device.
There is already a pid file /var/run/dhclient.ra1.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ra1: ERROR while getting interface flags: No such device
ra1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ra1.
ra0: ERROR while getting interface flags: No such device
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device ra0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ra0 ; No such device.
There is already a pid file /var/run/dhclient.ra0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ra0: ERROR while getting interface flags: No such device
ra0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ra0.
```

I still wonder why I do have internet when I start ubuntu
Ubuntu 7.10,kernel 2.6.22.15-generic
so it cannot be such a big issue, right?
Thanks

---

### Post by vambo on 2007-10-30
Take it your not running off wireless :)
The can't find eth1 etc things are nothing to be bothered about, but it seems to think  it should have wireless (I think).
Anyway, if it ain't burst, don't fix it (unless you want to play with it of course - but if you do back up that file first!)

---

### Post by axe_mad on 2007-10-31
Can anyone help, I am no further on with the problem - see original post. My thoughts are that I will have to re-install an earlier version from scratch but I was hoping that would be the last resort.:(

:guitar:

---

### Post by jeffjohn on 2007-11-02
URGENT HELP! required too!  Upgraded efficiently all looked good BUT now no Internet connection.  selected DCHP  what else is there?  Can ping around home network ok.

var/log/messages:-

message handler not found under /com/redhat/dchp/eth0

worked transparently under FF but absolutely stuck with GG!

Please assist me, someone!  Shall have to migrate back after a wasted 8 hrs if I can't get connected soonest.

many thanks Jeffjohn:(

---

### Post by vambo on 2007-11-02
Have you looked at /etc/network/interfaces to see if eth0 (I'm assuming that's your network
connection) has dhcp configured (see above)?

---

### Post by mooreslawuk on 2008-03-23
> **axe_mad said:**
> Can anyone help, I am no further on with the problem - see original post. My thoughts are that I will have to re-install an earlier version from scratch but I was hoping that would be the last resort.:(

:guitar:
I'm stuck too. If I type 'sduo ifup -a', I get no response.I have noticed that my wireless settings are associated with eth1 and not, say, wlan0. Is this OK, if not how to fix? eth0 appears to use  DHCP correctly, but I still have not network connection.

Many Thanks

---

