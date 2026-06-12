---
title: "no lan after precise install"
date: 2012-05-22
forum: Installation &amp; Upgrades
---

### Post by MatsWolpers on 2012-05-22
background:
i run a small lan at my home. to the best of my knowledge, nobody other than me works with it.
the lan is 
 adsl router <---> giga-Switch 4 ports <--> 3 computers

one of the computers is a qnap qnap 439 Pro ii + which ran 10.04 LTS server until a month ago.

i installed 12.04 server amd64 on this qnap hardware.
this is a fresh install on a new hard disk, not an upgrade over the previous 10.04
the installation appears smooth and the system boots normally.
network config was manual as my lan does not use dhcp. however this is about the 200th time i've done network config and i do believe i know what i'm doing, at least at the hands-on-keys level.
this hw offers two eth ports, and i wantonly used eth1 during installation. The hardware is a Intel 82574L.

symptom: 
after installation and successful reboot, apt-get update fails repeatedly, claiming Temporary failure resolving 'security.ubuntu.com/... and similar for all configured sites.


investigation so far (wasn't quite as systematic as i write it now...):
* the connection LEDs between the qnap and the switch are all green
* the system can ping itself but no other pc in the lan. (0% vs 100% packet loss)
* my adsl router does not recognize this computer as a connected device
* /etc/network/interfaces showed expected data for the configured eth1 and lo
* route -n produces output like in the offical docu
* examined lshw -class network and found what appears like correct hardware detection to the untrained eye.
* i tried reconfiguring to use eth0 by editing /etc/network/interfaces and /etc/init.d/networking restart, and found the problem to persist.
* i tried ifup eth0: RTNETLINK answers: File exists, Failed to bring up eth0 (same for eth1)
* /var/log/installer/syslog has lines 
net/hw-detect.hotplug: detected hotpluggable network interface lo
net/hw-detect.hotplug: detected hotpluggable network interface eth0
net/hw-detect.hotplug: detected hotpluggable network interface eth1

and
check-missing-firmware: /dev/.udev/firmware-missing does not exist, skipping
check-missing-firmware: /run/udev/firmware-missing does not exist, skipping
check-missing-firmware: no missing firmware in /dev/.udev/firmware-missing, /run/udev/firmware-missing

followed by 
kernel: [  140.670813] ADDRCONF(NETDEV_UP): eth1 link not ready
kernel: [  140.826820] ADDRCONF(NETDEV_UP): eth0 link not ready

but i cannot decide what this is telling me except that obviously i have no lan.

preliminary summary:
after installing 12.04server, a previously working hardware has lost its lan capability.
well-known config issues have been checked (if by myself... there is always the BIG problem before the machine)

further investigation:
=============
my own ideas are growing desperate at this point:
- i might find yet another hard disk and install some other OS to see if the problem is in the hw or in the OS.
- i might decommission that hw and buy something else

questions
======
is there anybody with a less disruptive idea for understanding, and preferably fixing this concern? 
could this be a firmware concern?
what else is there that i should have been thinking of?

many thanks,
mats


ps as i have no lan, i cannot transfer files from qnap to my other machines, and type writing copy of all those conf files and command outputs is a little tedious. if someone does need the exact output of something, i'll force myself, but i hope that you may please excuse my not preempting such requests;-)

---

### Post by darkod on 2012-05-22
It's silly, but it might create problems. Is the DNS set correctly?

The DNS was little changed in server 12.04 when using static IP (like most servers should use anyway).

In /etc/network/interfaces do you have the line:

dns-nameservers x.x.x.x y.y.y.y

---

### Post by MatsWolpers on 2012-05-22
yes i do, and it points to the adsl router's address, same as the other two pc in my lan (all of which go out quite easily).

thanks for thinking along,
mats

---

### Post by darkod on 2012-05-22
It's not the same situation but maybe this can give you some idea:
[http://www.linuxquestions.org/questions/linux-hardware-18/intel-82574l-gigabit-network-card-issues-and-resolution-831364/](http://www.linuxquestions.org/questions/linux-hardware-18/intel-82574l-gigabit-network-card-issues-and-resolution-831364/)

In the first post there is also a command how to check which driver (module) is the adapter trying to use, so that might help you google it further.

I guess 12.04 is still new so google doesn't return anything specific to 12.04 but some people had issues with this adapter even in 10.04.

---

### Post by MatsWolpers on 2012-05-23
darko,

some food for thought there, thanks a lot. i'll follow up and post any results. in the meantime,
many thanks.

mats

---

### Post by MatsWolpers on 2012-05-24
_update::further analysis::ethtool_
i have managed to bring ethtool to the defunct machine via usb stick.
ethtool eth0 brings this output:

       Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full
	Supported pause frame use: No 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advrtised pause frame use: No
	Advertised auto-negotiation: Yes
        Speed: Unknown!
        Duplex: Unknown!
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
	MDI-X: Unknown
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000001f (1)
			       drv
        Link detected: no
FWIW, ethtool eth1 is the same thing.

all of which, to my untrained eyes, points in the sme direction previously established: there is no link, and that's the end of that.


_update::further analysis::e1000e driver_
my system shows e1000e version 1.5.1-k. according to [http://sourceforge.net/projects/e1000/files/e1000e%20stable/](http://sourceforge.net/projects/e1000/files/e1000e%20stable/), this date from 2011-aug-12. current versions are 1.11.3 of 2012-apr-20 and 2.0.0 of 2012-may-15.

some of the change logs seem to address auto config problems with the links, which is encouraging.
less encouraging is the fact that i'm not god's gift to compiling c code, but i'll see what i can do by following the book.

_kernel 3.2.0-24_
btw, there is a 3.2.0-24 kernel out now: does anyone happen to know what e1000e.ko version is included in that?

many thanks,
mats

---

### Post by MatsWolpers on 2012-05-26
a final update:

i did the eeprom update fixeep-82574_83.sh to be found at [http://sourceforge.net/projects/e1000e](http://sourceforge.net/projects/e1000e)
and rebooted.

the intended change happened (flipping that bit from 0x58 to 0x5a) , but the consequences were not what i had hoped for: i am stuck with no link.

so i tried to do the driver compilation, using the 1.11.3 tarball.
sadly, it turns out i cannot do this (not easily, to be more precise) as my system does not sport a compiler installation.
without the network, i do not see myself chasing the dependency tree and manually downloading all kinds of debs, transfer them via usb stick, and manually install everything  just to obtain a driver that may or may not solve my problems: i simply don't have time for this, sorry.

i'll try falling back to 10.04 when stuff worked (wonder how, by now) and maybe try again later. 
thanks anyway,
mats

---

### Post by MatsWolpers on 2012-05-27
:lolflag:
this _is_ embarrassing, but i cannot be the only installer with a bad hair week, can i. so for the benefit of others, here is what i found:

1. i did install 10.04 as indicated previously and THAT gave me the old no link situation.
2. from another machine, i found a hint that "no link" might be related to cabling issues. So i checked all my cables again, found them satisfactory, but for the heck of it (and for want of other ideas) i swapped cables between two machines. nothing changed of course: the cables _are_ good. but while i looked at dmesg, i saw a fairly recent "link coming up" message. 
[INDENT]**FOLLY 1:** in retrospect, it seems possible that after flashing eth0, i did shutdown -r rather than shutdown -h. but the frustrated power off later would then have enabled the eeprom fix.[/INDENT]
3. so i tried my pings again, and i tried my lan cable in both eth sockets (remember i said two ports?), and i have internal ping both ways. but i still could not get apt-get to work.
4. so now i did another eeprom flash for the other eth port undr 10.04, powered down, repeated the 12.04 install, this time wiring both eth ports while in sw selecting eth0, and i omitted software package DNS server from my selection. all is smooth, system is up, and i have apt. In this way i identified which of my two eth sockets is eth0 ( they are one above the other on the back pane: the lower one is eth0.

[INDENT]**Folly 2:** it is now embarrassingly clear that i tried to access the net through an unconfigured DNS service. This is clearly not the best idea i ever had. [/INDENT]

 
to summarize, then:
1. "ADDRCONF (NETDEV_UP): eth0: link is not ready" concerns are sometimes related to cabling, including the quality of the cable itself, and including the positioning of the plug into the correct socket.
2. when applying the fixeep patch, be sure to shutdown -h. 
3. when selecting the dns package during installation, try configuring it before accessing the internet.

gosh, i do feel stupid right now,
mats

---

