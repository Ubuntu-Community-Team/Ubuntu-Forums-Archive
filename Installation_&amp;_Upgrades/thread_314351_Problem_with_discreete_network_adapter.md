---
title: "Problem with discreete network adapter"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by muxecoid on 2006-12-07
Trying to set up network connection on newly installed system.

ifconfig shows eth0. I connect eth cable to the computer (discreete LAN card) and ethernet box on the wall and run

```
sudo ifdown eth0
sudo ifup eth0
```

On other computers this worked. Here it waits for DHCP for a minute, than says

```
No DHCPOFFERS received
No working leases in persistent database - sleeping.
```

I'm connecting it to university's Ethernet on other Ubuntu machines it worked just after plugging the cable to onboard LAN.

What's wrong? What needs to be done? (It's not my computer, so I do not know what network card is installed).

---

### Post by bscbrit on 2006-12-07
What is the full output of ifconfig?  I assume that you have configured the ethernet card for DHCP?  Can you ping 127.0.0.1, do you know that the card and the cable are both good, is the green light on the card on?  Does it flash during the attempt to get a DHCP lease?

I know that you are using eth0 but, other than that, you haven't given me much to go on.

---

### Post by bscbrit on 2006-12-07
Another quick thought.....

Some computers have a built in ethernet connection on the m'board and if you have installed a second ethenet card you cannot simply assume that the one you are trying to use is eth0.  Open System -> Administration -> Networking and see if it has found more than one ethernet card.

---

### Post by muxecoid on 2006-12-07
Sorry. The problem is that I can't post to forums from the faulty computer. The card is OK, the cable is OK. Card worked under windows and neighboring machine with on-board eth connects perfectly through this cable.
localhost pings perfectly.

The line LED lights when the cable is plugged, the activity LED flashes briefly when trying to get DHCP lease.

---

### Post by bscbrit on 2006-12-07
OK, lets try to rule out the obvious - I'm assuming that the uni's system is up and running, and secondly, it hasn't run out of allocatable addresses?  Is anyone else having a problem?

---

### Post by bscbrit on 2006-12-07
The next thing that you could try is logging on from another machine, make a note of its IP address and DNS addresses, switch it off, and set the addresses manually on your test machine.  If everything else is working it should work perfectly.  If not, you know that it is in the test system that the problem lies.

---

### Post by muxecoid on 2006-12-07
Yes, there are enough allocable adresses, neighboring machines can reconect freely.

When I ifup eth0 on other machines I get own IPs and DNS's IP, how do I transfer it to the faulty one?


Intuition make me think that it's due to the PCIness of the network card, but my intuition is faulty.

---

### Post by bscbrit on 2006-12-07
Open System -> Administration -> Networking, select your ethernet card and 'Properties'.  Make sure that you change from Automatic Configuration (DHCP) to 'Static IP Address' and add the appropriate values in the fields given.  Save the settings and your computer should come up on the network.  If not, it might give you some clues as to where the problem lies.  Try pinging the gateway and an external URL.  That will prove both connectivity and that the DNS server is being accessed.

Don't use it like this for too long because your network expects everyone to be using DHCP but you should be able to do this for long enough to test your new connection.

---

