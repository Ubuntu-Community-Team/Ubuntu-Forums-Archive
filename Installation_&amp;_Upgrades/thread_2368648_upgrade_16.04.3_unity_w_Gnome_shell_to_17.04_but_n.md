---
title: "upgrade 16.04.3 unity w Gnome shell to 17.04 but no internet..."
date: 2017-08-13
forum: Installation &amp; Upgrades
---

### Post by Kris_M on 2017-08-13
Mod move if needed.

Have a Unity 16.04.3 build that I ran gnome shell on and been running 3.18 default Gnome - seems fine. Love it. Wanted to try 3.24 .

Tried update to 17.04 using software updater - took maybe 15 min - seemed to go fine, rebooted fine but no internet.

I clonezilla-ed SSD back to before  but wondering what I did wrong, for next try.
Thanks!!!

I have 2 intel chipped NICs - 1 on mobo that I don't use, and one on addon card that I use. - NIC to Router to V2DSL. 90Mbs

MBR/BIOS

---

### Post by deadflowr on 2017-08-13
*Thread moved to **Installation and Upgrades***
16.04.3 is past testing and no longer under development.

While this is an upgrading issue, perhaps look over the networking and wireless sticky:
[https://ubuntuforums.org/showthread.php?t=370108]("https://ubuntuforums.org/showthread.php?t=370108")
While the wireless script does say wireless, it will output some useful info about wired setups, too.
fwiw

---

### Post by vocx on 2017-08-13
> **Kris_M said:**
> Mod move if needed.

Have a Unity 16.04.3 build that I ran gnome shell on and been running 3.18 default Gnome - seems fine. Love it. Wanted to try 3.24 .

Tried update to 17.04 using software updater - took maybe 15 min - seemed to go fine, rebooted fine but no internet.

I clonezilla-ed SSD back to before  but **wondering what I did wrong**, for next try.
Thanks!!!

I have 2 intel chipped NICs - 1 on mobo that I don't use, and one on addon card that I use. - NIC to Router to V2DSL. 90Mbs

MBR/BIOS
If I understand the problem correctly, you had 16.04, then upgraded to 17.04. On 16.04 you had Internet and everything was fine. When you upgraded to 17.04 you noticed you don't have Internet any more. So you restored the entire contents of your previous 16.04 installation. Is this correct?

I don't think you did anything wrong. Also, why does it matter that you are using Gnome shell or Unity? The problem is not there. The problem is probably with the wireless or wired card drivers. When you perform an upgrade the kernel version changes, so new drivers are used. If in 16.04 you did something special, like getting new drivers from the Internet, or blacklisting a module, then you probably have to do the same in the new 17.04 system.

So, run the wireless script, make a note of your network card, and browse for solutions to get that working in 17.04.

---

### Post by Kris_M on 2017-08-13
I'm back...  Thanks to all! :D
@deadflowr I realized that there is the possibility that I could try to tether from my cell phone - that would at least give me internet to get that script run.

I will also use the mobo's NIC in case that makes a difference. (I found that when trying to install 17.04 It would get stuck on a green screen if I had my HDTV plugged to the Intel display port. So I figure it may need to be special!)(I was using my Nvidia 750gtx ti.)(which went fine)(but that's another build...)

@vocx - yes.  It may not make a difference unity of Gnome, but I just say what I'm on and what I've done. :) The only drivers I tried to install were for a RealTek NIC chip that I had on there at one point.

Okay, off to try! - No big deal - about a 15 min test.

---

### Post by Kris_M on 2017-08-13
The short answer is /var/run/NetworkManager is empty.

Looking to see if I can run NM. edit probably not, it probably doesn't exist and w/o a connection no way to get it. Tether did nothing. - No NM.


```
   	 	 	 	   kris@kris-Z97X-UD3H:~$ sudo lshw -c network
   *-network DISABLED         
        description: Ethernet interface
        product: Ethernet Connection I217-V
        vendor: Intel Corporation
        physical id: 19
        bus info: pci@0000:00:19.0
        logical name: eno1
        version: 00
        serial: 40:8d:5c:59:ac:23
        capacity: 1Gbit/s
        width: 32 bits
        clock: 33MHz
        capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair
        resources: irq:26 memory:f7900000-f791ffff memory:f793c000-f793cfff ioport:f080(size=32)
   *-network DISABLED
        description: Ethernet interface
        product: 82574L Gigabit Network Connection
        vendor: Intel Corporation
        physical id: 0
        bus info: pci@0000:05:00.0
        logical name: enp5s0
        version: 00
        serial: 68:05:ca:58:c4:4c
        capacity: 1Gbit/s
        width: 32 bits
        clock: 33MHz
        capabilities: pm msi pciexpress msix bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=1.8-0 latency=0 link=no multicast=yes port=twisted pair
        resources: irq:16 memory:f78c0000-f78dffff memory:f7800000-f787ffff ioport:d000(size=32) memory:f78e0000-f78e3fff memory:f7880000-f78bffff
   *-network DISABLED
        description: Ethernet interface
        physical id: 2
        logical name: enp0s20u6
        serial: 96:5c:ac:b7:a3:03
        capabilities: ethernet physical
        configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device link=no multicast=yes
 kris@kris-Z97X-UD3H:~$ 
 
 
 
 
 
 
 
 
 kris@kris-Z97X-UD3H:~$ nmcli dev status
 DEVICE     TYPE      STATE      CONNECTION  
 eno1       ethernet  unmanaged  --          
 enp0s20u6  ethernet  unmanaged  --          
 enp5s0     ethernet  unmanaged  --          
 lo         loopback  unmanaged  --          
 kris@kris-Z97X-UD3H:~$ sudo ethtool eno1
 Settings for eno1:
 	Supported ports: [ TP ]
 	Supported link modes:   10baseT/Half 10baseT/Full  
 	                        100baseT/Half 100baseT/Full  
 	                        1000baseT/Full  
 	Supported pause frame use: No
 	Supports auto-negotiation: Yes
 	Advertised link modes:  10baseT/Half 10baseT/Full  
 	                        100baseT/Half 100baseT/Full  
 	                        1000baseT/Full  
 	Advertised pause frame use: No
 	Advertised auto-negotiation: Yes
 	Speed: Unknown!
 	Duplex: Unknown! (255)
 	Port: Twisted Pair
 	PHYAD: 2
 	Transceiver: internal
 	Auto-negotiation: on
 	MDI-X: Unknown (auto)
 	Supports Wake-on: pumbg
 	Wake-on: d
 	Current message level: 0x00000007 (7)
 			       drv probe link
 	Link detected: no
 kris@kris-Z97X-UD3H:~$ 
 
 
  
```

---

### Post by vocx on 2017-08-13
> **Kris_M said:**
> The short answer is /var/run/NetworkManager is empty.

Looking to see if I can run NM. edit probably not, it probably doesn't exist and w/o a connection no way to get it. Tether did nothing. - No NM.
Do you mean, you think network-manager is not installed? I think it should be.

Maybe the service is not started, in which case you can start it manually
```

sudo service networking restart
sudo service network-manager restart

```

---

### Post by Kris_M on 2017-08-13
Thanks for your time but no joy. Even if I put something in NetworkManager, the restart clears it out. It apparently can't see any NIC or host.

---

### Post by Kris_M on 2017-08-13
Fixed - /user/lib/NetworkManager/conf.d/10-globally-managed-devices.conf

add "except:type:ethernet,"
sudo service network-manager restart

---

### Post by vocx on 2017-08-13
> **Kris_M said:**
> Fixed - /user/lib/NetworkManager/conf.d/10-globally-managed-devices.conf

add "except:type:ethernet,"
sudo service network-manager restart
I don't know what you modified and why.

The directory "/usr/lib/NetworkManager/conf.d" does not exist in my system.

There is a "/etc/NetworkManager/conf.d" directory, but it does not contain a "10-globally-managed-devices.conf" file.

So, I must conclude your system, and my Ubuntu 16.04 (Unity) are different.

---

### Post by Kris_M on 2017-08-13
> **vocx said:**
> I don't know what you modified and why.

The directory "/usr/lib/NetworkManager/conf.d" does not exist in my system.

There is a "/etc/NetworkManager/conf.d" directory, but it does not contain a "10-globally-managed-devices.conf" file.

So, I must conclude your system, and my Ubuntu 16.04 (Unity) are different.

That's the problem and precisely what @deadflowr was referring to - it just took me a while to get it. The libraries where NetworkManager has its conf changed going from 16.04 to 17.04.

Thanks to all!!!

---

