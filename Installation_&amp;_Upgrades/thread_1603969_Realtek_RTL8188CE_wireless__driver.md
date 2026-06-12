---
title: "Realtek RTL8188CE wireless  driver"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by Zippy777 on 2010-10-23
Hello
I've just purchased a Toshiba Satellite L670D laptop and installed Ubuntu 10.10. Everything works fine excepting the most important thing, the wireless internet connection.
I've ran the test which said "Unclaimed" and then I followed the procedure to install a Windows driver. The installation program says the driver is installed but the test still shows "unclaimed". 
I am really stuck, any ideas please?

I also obtained the driver for Ubuntu but the "readme" file suggests that it takes such skills to install that I do not have.

Thanks for your help

---

### Post by mhgsys on 2010-10-23
read; 
[http://art.ubuntuforums.org/showthread.php?t=1580036](http://art.ubuntuforums.org/showthread.php?t=1580036)

---

### Post by Zippy777 on 2010-10-23
I've done what is suggested at [http://art.ubuntuforums.org/showthread.php?t=1580036](http://art.ubuntuforums.org/showthread.php?t=1580036) but it didn't help. I am still getting Unclaimed, please see below:
    *-network UNCLAIMED     
            description: Network controller
            product: Realtek Semiconductor Co., Ltd.
            vendor: Realtek Semiconductor Co., Ltd.
            physical id: 0
            bus info: pci@0000:02:00.0
            version: 01
            width: 64 bits
            clock: 33MHz
            capabilities: pm msi pciexpress bus_master cap_list
            configuration: latency=0
            resources: ioport:d000(size=256) memory:ff600000-ff603fff
       *-network
            description: Ethernet interface
            product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
            vendor: Realtek Semiconductor Co., Ltd.
            physical id: 0
            bus info: pci@0000:03:00.0
            logical name: eth0
            version: 05
            serial: 88:ae:1d:e6:c6:3d
            size: 10MB/s
            capacity: 100MB/s
            width: 64 bits
            clock: 33MHz
            capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
            configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
            resources: irq:27 ioport:c000(size=256) memory:d0104000-d0104fff(prefetchable) memory:d0100000-d0103fff(prefetchable)
     ubuntu@ubuntu:~$ 
     
Any ideas please?
Thanks in advance

---

### Post by mhgsys on 2010-10-25
I see your also posting here; [[http://ubuntuforums.org/showthread.php?p=10019180](http://ubuntuforums.org/showthread.php?p=10019180)

Look @dushyanthan

---

### Post by Zippy777 on 2010-10-25
Yes, because I realized I was in the wrong place "Installation and updates".
Thanks

---

