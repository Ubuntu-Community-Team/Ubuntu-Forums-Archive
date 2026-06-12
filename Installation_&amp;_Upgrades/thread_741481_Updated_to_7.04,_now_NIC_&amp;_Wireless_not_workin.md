---
title: "Updated to 7.04, now NIC &amp; Wireless not working"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by Arhineus on 2008-03-31
I just updated to 7.04.  I've had problems with my wireless network card before, but now my wired network card isn't working either.  When I connect a cable to it from the router, it is as if there is no connection being sensed, as my router doesn't detect the connection.  I know there is nothing wrong with the cable, as I have checked it out.

Any ideas where to start looking?

---

### Post by process91 on 2008-03-31
Post some diagnostic calls. For instance, the results of the following commands:

```
ifconfig -a
sudo ls /sys/class/net/
lspci | grep network
lspci | grep ethernet 
```Also post the contents of your /etc/network/interfaces file

---

### Post by Arhineus on 2008-04-01
Results: ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:DA:BA:FB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x1800 

eth1      Link encap:Ethernet  HWaddr 00:14:A4:36:7B:B5  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:4 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7930 (7.7 KiB)  TX bytes:7930 (7.7 KiB)


```

Results of: sudo ls /sys/class/net/
```
eth0
eth1
lo

```

Both lspci (|grep network & | grep ethernet) commands returned no results.

The contents of /etc/network/interfaces are listed below:

```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


```

---

### Post by Arhineus on 2008-04-01
I took a further look, and got the following from lspci.

00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)

---

### Post by process91 on 2008-04-01
OK that helps. I'm not sure why your internal NIC isn't working, but the Broadcom chip is a known pain. I have it too, and in Gutsy it worked really well but in previous versions I had gone through tons of code and hacks to try to get it working including ndiswrapper and such. Assuming you have too, try this.

```
sudo rmmod ndiswrapper
sudo aptitude install bcm43xx-fwcutter
```This should get your wireless working, at least it did for me. You may have to reboot, but just a **/etc/init.d/networking restart** should kick that into gear.

Now for your wired connection, can you give me the output of this command - ```
ethtool eth1
```(If eth1 turns out to be your wireless card just change it to eth0 and give me the output of that command)

---

### Post by cazper6 on 2008-04-01
Hey guys, Okay im having a similiar problem.. i am on a sony Vaio .. had vista on it.. and i put ubuntu on it.. everything worked just fine with vista.. but when i put ubunto 7.10 on it.. it seemed to work fine til i couldnt get the internet working. it shows the driver as enabled  and it shows me as connected to the internet in the taskbar. atleast 85% most the time. but i cant pull up any websites.. i cant open up a telnet session or anything. i did all the trouble shooting on the ubuntu helping and everything seems to be in order and fine.. but idk why firefox wont pull up a page. Oh and idk if this matters with ubuntu but theres a proxy website we have to log into where i am on a airforce base.. and it automatically pull up when you try to pull up a website.. then i log in.. but i cant get anything to pull up on this.. any help?? plz

---

### Post by Arhineus on 2008-04-01
> **process91 said:**
> OK that helps. I'm not sure why your internal NIC isn't working, but the Broadcom chip is a known pain. I have it too, and in Gutsy it worked really well but in previous versions I had gone through tons of code and hacks to try to get it working including ndiswrapper and such. 


Yeah, I had a hard time getting it to work originally, but it was working pretty well until this update.  I found using Wifi-Radar always works best for me.

> 
Assuming you have too, try this.

```
sudo rmmod ndiswrapper
sudo aptitude install bcm43xx-fwcutter
```This should get your wireless working, at least it did for me. You may have to reboot, but just a **/etc/init.d/networking restart** should kick that into gear.


Tried that, no luck.

> 
Now for your wired connection, can you give me the output of this command - ```
ethtool eth1
```(If eth1 turns out to be your wireless card just change it to eth0 and give me the output of that command)

When I run that, these are the results.
> 
arhineus@homeserver:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 13
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pg
        Wake-on: d
        Current message level: 0x000000c5 (197)
        Link detected: no
arhineus@homeserver:~$ sudo ethtool eth1
Settings for eth1:
        Link detected: no
arhineus@homeserver:~$ 


---

### Post by cazper6 on 2008-04-01
yeah i just tried all that.. the only thing ive noticed so far was in system there is no windows wireless device thingy.. just the synaptic package manager and i tried to install the ndiswrapper which i think went through well... i mean.. it shows as connected and everything.. i dont understand.. im stumped.. im not illeterite most the time with trouble shooting and stuff lol

---

### Post by Arhineus on 2008-04-01
> **cazper6 said:**
> yeah i just tried all that.. the only thing ive noticed so far was in system there is no windows wireless device thingy.. just the synaptic package manager and i tried to install the ndiswrapper which i think went through well... i mean.. it shows as connected and everything.. i dont understand.. im stumped.. im not illeterite most the time with trouble shooting and stuff lol

I'm not a guru by any means, but I'll try and help out.

If you bring up a terminal window, are you able to ping your router (I'm assuming you have a router)?

---

### Post by cazper6 on 2008-04-01
its a base router, i cant get to it or anything.. but i can try to ping it,
it pinged 64mb  0% lost

---

### Post by Arhineus on 2008-04-01
Are you able to ping an external IP / domain?

---

### Post by cazper6 on 2008-04-01
yeah

---

### Post by Arhineus on 2008-04-01
As your interfaces are working,  would say it's an unrelated issue to what I'm experiencing.

I just re-read one of your past posts, and I think this has something to do with your wireless network, not your system itself.

---

### Post by Arhineus on 2008-04-02
I just tried doing an clean install, of 7.10, and am having the exact same problem.

Contents of /etc/network/interfaces changed to:

```
auto lo
iface low inet loopback
```

---

### Post by Arhineus on 2008-04-03
Well, I have no idea what the problem was.  I did another clean install of 7.1, and wouldn't you know it, everything is working perfectly now.  *shrugs*

Thanks for the help.

---

