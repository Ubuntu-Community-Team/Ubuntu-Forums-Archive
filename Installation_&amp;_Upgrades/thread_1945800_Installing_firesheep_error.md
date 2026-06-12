---
title: "Installing firesheep error"
date: 2012-03-23
forum: Installation &amp; Upgrades
---

### Post by icedice on 2012-03-23
As the title suggests I am trying to get firesheep. When I compile the code I get this error

```
libtool: link: require no space between `-L' and `/usr/lib'
make[1]: *** [libfiresheep.la] Error 1
make[1]: Leaving directory `/home/josh/firesheep/backend'
make: *** [all-recursive] Error 1

```

To me it seems to be a problem with the program but I'm not really sure. 

I'm using ubuntu 10.04 x86

---

### Post by Paddy Landau on 2012-03-24
Firesheep looks great, but looking at its website, it is not supported on Linux. Could that be the problem?

---

### Post by icedice on 2012-03-24
I've seen people build it and run it in ubuntu and backtrack

---

### Post by haqking on 2012-03-24
[http://linuxnoise.wordpress.com/2010/12/31/installing-firesheep-on-unity-linux/](http://linuxnoise.wordpress.com/2010/12/31/installing-firesheep-on-unity-linux/)
[http://www.hackersgarage.com/how-to-install-firesheep-on-linux.html](http://www.hackersgarage.com/how-to-install-firesheep-on-linux.html)
[http://www.embeddedheaven.com/install-firesheep-ubuntu.htm](http://www.embeddedheaven.com/install-firesheep-ubuntu.htm)

---

### Post by Paddy Landau on 2012-03-25
> **haqking said:**
> [http://linuxnoise.wordpress.com/2010/12/31/installing-firesheep-on-unity-linux/](http://linuxnoise.wordpress.com/2010/12/31/installing-firesheep-on-unity-linux/)
[http://www.hackersgarage.com/how-to-install-firesheep-on-linux.html](http://www.hackersgarage.com/how-to-install-firesheep-on-linux.html)
[http://www.embeddedheaven.com/install-firesheep-ubuntu.htm](http://www.embeddedheaven.com/install-firesheep-ubuntu.htm)
The last link worked for me (64-bit) -- but Firesheep reported, "Failed to list network devices." And it frequently crashes my Firefox. Oh well.

---

### Post by haqking on 2012-03-25
> **Paddy Landau said:**
> The last link worked for me (64-bit) -- but Firesheep reported, "Failed to list network devices." And it frequently crashes my Firefox. Oh well.

it is a common problem.

does your network device support promiscuous mode ?

---

### Post by Paddy Landau on 2012-03-25
> **haqking said:**
> does your network device support promiscuous mode ?
Sorry, I don't even know what that means :oops:

---

### Post by haqking on 2012-03-25
> **Paddy Landau said:**
> Sorry, I don't even know what that means :oops:

the same as in the usual sense ;-)

it means it will receive all traffic rather than just the traffic intended for itself.

whether your NIC supports that i dont know.

most ethernet NIC's do but wireless NIC's are often different

what chipset is it ?

---

### Post by Paddy Landau on 2012-03-25
I don't know how to answer your question. I think lshw may help?
```
*sudo lshw -class network*
  *-network               
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth2
       version: 05
       serial: c8:9c:dc:29:1f:a2
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 duplex=full firmware=0.13-4 ip=192.168.5.113 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:fe500000-fe51ffff memory:fe528000-fe528fff ioport:f080(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1.8
       logical name: wlan2
       serial: 68:a3:c4:c0:37:6e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.5.114 multicast=yes wireless=IEEE 802.11bgn
```

---

### Post by haqking on 2012-03-25
> **Paddy Landau said:**
> I don't know how to answer your question. I think lshw may help?
```
*sudo lshw -class network*
  *-network               
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth2
       version: 05
       serial: c8:9c:dc:29:1f:a2
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 duplex=full firmware=0.13-4 ip=192.168.5.113 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:fe500000-fe51ffff memory:fe528000-fe528fff ioport:f080(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1.8
       logical name: wlan2
       serial: 68:a3:c4:c0:37:6e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.5.114 multicast=yes wireless=IEEE 802.11bgn
```

yes your intel NIC supports promiscuous mode.

your wireless i dont think supports monitor mode/promiscuous mode using that driver [http://linuxwireless.org/en/users/Drivers](http://linuxwireless.org/en/users/Drivers)

---

### Post by Paddy Landau on 2012-03-25
> **haqking said:**
> yes your intel NIC supports promiscuous mode.

your wireless i dont think supports monitor mode/promiscuous mode using that driver [http://linuxwireless.org/en/users/Drivers](http://linuxwireless.org/en/users/Drivers)
I don't even know what I'm looking at on that page, so I'm not going mess around with my drivers. Thanks for your advice and help; I'll just do without Firesheep.

---

### Post by haqking on 2012-03-25
> **Paddy Landau said:**
> I don't even know what I'm looking at on that page, so I'm not going mess around with my drivers. Thanks for your advice and help; I'll just do without Firesheep.

ha no worries.

if you dont know what promiscuous mode is then its unlikely you need firesheep for anything ;-)

Peace

---

### Post by Ms. Daisy on 2012-03-25
Is it legal to use firesheep on a network that's not your own?  Other than doing an ethical penetration test, are there any legitimate reasons to use firesheep?

---

### Post by haqking on 2012-03-25
> **Ms. Daisy said:**
> Is it legal to use firesheep on a network that's not your own?  Other than doing an ethical penetration test, are there any legitimate reasons to use firesheep?

it is not legal or more specifically violates the AUP or IS Policy to do anything on a network that is not your own without explicit permission ;-)

if it is not corporate and on someone elses network such as residential then wiretapping laws come into play depending on country.

if it is own network and/or machine then the reasons would be for testing.

by definition session hijacking contravenes something somewhere without a legal binding agreement allowing it ;-)

---

### Post by Paddy Landau on 2012-03-26
> **Ms. Daisy said:**
> Is it legal to use firesheep on a network that's not your own?  Other than doing an ethical penetration test, are there any legitimate reasons to use firesheep?
The only ethical reasons are to check your own security and to raise awareness to try to force those companies to be more responsible. It is a disgrace that those sites have such wide-open security holes. Whenever personal or banking information is involved, they should use only SSH not only for logins but also for all access (I understand that Google does this now for its Calendar, GMail and Docs applications).

---

### Post by mcmb03 on 2012-12-24
I figured out a fix by simply fixing the error it makes. the autogen.sh has some sort of error when building the make file, so after running it open Makefile with a text editor and search for > -L /usr/
delete the space and save. Run make command from terminal again and it builds with no errors, provided you did all the other steps correctly.

---

