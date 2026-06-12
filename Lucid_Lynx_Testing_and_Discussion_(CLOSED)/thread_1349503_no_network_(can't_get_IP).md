---
title: "no network (can't get IP)"
date: 2009-12-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rtalcott on 2009-12-08
I have tried to install 4 daily builds...32 bit and 64 bit on 3 different machines...install boots from usb no problem BUT NetworkManager cannot pick up an IP address...mouse over the icon and I see "Requesting a wired network address for Auto eth0."  All 3 machines ran 9.10...no problem.

Since I have not seen anyone else bring this issue up I guess it's my problem...any suggestions?

rt

---

### Post by Gina on 2009-12-08
I can't even get that far, I'm afraid.

---

### Post by rtalcott on 2009-12-08
Weird but one of the very early daily Builds installed fine...BUT I managed to make a mess of that install so I thought it would be easiest to do a clean install...and that's when I started having the network problem.

rt

---

### Post by cariboo on 2009-12-08
Can you set up and ip address manually?

---

### Post by rtalcott on 2009-12-08
I am trying to set up manually but...I know it should be simple...but I am having no luck...can't get it to take the numbers...that machine is off right now so I am not giving you the exact details...as I said...an early Daily build worked fine for a week or two...them I made a mess of it...lost X...decided to do a clean install and found I could not get an IP...on 3 machines...1 64 bit AMD quad core and two Intel P4's...
rt

---

### Post by descendent87 on 2009-12-08
Had the same problem, have had to go back to 9.10 for now
[http://ubuntuforums.org/showthread.php?t=1347572](http://ubuntuforums.org/showthread.php?t=1347572)

---

### Post by cariboo on 2009-12-08
> **descendent87 said:**
> Had the same problem, have had to go back to 9.10 for now
[http://ubuntuforums.org/showthread.php?t=1347572](http://ubuntuforums.org/showthread.php?t=1347572)

I believe the op is having a problem with a wired connection, your wireless problem could be totally different.

To the op when you get time could paste the output of:

```
sudo lshw -C network > network.txt
```

in your next post. Just copy the text file that is created to a system that has a working network connection

---

### Post by rtalcott on 2009-12-08
I still have my now hosed (no X) 10.04 on the drive...I have a network on this install...when I run the command it tells me I have a RTL8111/8168B PCI Gigabit Ethernet Controller  physical id:0 logical name eth0

I can do apt-get update so I have a network connection

I'll shut this down and run the command on the usb live cd

I greatly APPRECIATE your assistance!
rt

---

### Post by rtalcott on 2009-12-08
I gotta run unfortunately...this will have to wait for a couple hours!

Unfortunately reality intrudes!
Thank you!
rt

---

### Post by rtalcott on 2009-12-08
From the LiveCD....can't get an IP:

*-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:bc:03:b9:67
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=1GB/s
       resources: irq:29 ioport:8c00(size=256) memory:fd8ff000-fd8fffff memory:fd7f0000-fd7fffff(prefetchable) memory:fd700000-fd71ffff(prefetchable)

---

### Post by rtalcott on 2009-12-08
From my hosed install of 10.04 BUT I can get an IP:

*-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:bc:03:b9:67
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.103 latency=0 link=yes multicast=yes port=MII speed=1GB/s
       resources: irq:29 ioport:8c00(size=256) memory:fd8ff000-fd8fffff memory:fd7f0000-fd7fffff(prefetchable) memory:fd700000-fd71ffff(prefetchable)

---

### Post by rtalcott on 2009-12-08
from the working 10.04 install...same machine...earlier daily build..

riverversion=2.3LK-NAPI duplex=full ip=192.168.1.103

I have an IP...I do not see one on the file from the LiveCD
rt

---

### Post by rtalcott on 2009-12-09
Today's daily Build...9 December...picked up an IP address...so this problem is "solved" although I do not know exactly what caused or what fixed it!
rt

---

### Post by juanJosepablos on 2009-12-09
did you try alpha1, I had same problem about the network, and now is working.

---

### Post by rtalcott on 2009-12-09
Did not realize that Alpha1 was out yet!
rt

---

### Post by ranch hand on 2009-12-09
Tomorrow.  And it better work better than the ISO I just tested.

---

### Post by rtalcott on 2009-12-09
Good Luck!  The network is working fine but now the nVidia drivers kill gnome and I'm back to the command line...gui works but not on 1920x1080...oh well..it's still early and this is a sandbox machine.  But the network not working was a pain.
rt

---

