---
title: "Latest updates to 16.04 cause my network adapters to disappear"
date: 2018-09-22
forum: Installation &amp; Upgrades
---

### Post by gerry-q on 2018-09-22
I've been running LTS 16.04 on a Dell Inspiron 1721 laptop for about two years.
When it started up a couple weeks ago, I noticed that my ethernet connection and my wi-fi connection had suddenly disappeared.
The previous day, normal periodic updates were installed and other than that I did not make any changes to the hardware or system setup.

I tried various things but no improvement so I downloaded the latest Ubuntu Installation image (LTS 16.04.5 64bit Desktop) and attempted to reinstall Ubuntu.  After the reboot, the system gave the same response - no network adapters were available.

I had the laptop subjected to diagnostic tests on the hard drive and memory - no problems found

So, I downloaded a new copy of my original install disk for LTS16.04.1 64 bit and booted from it.  I decided to select the option to "Try Ubuntu" and the system started with no issues - and the network connections for both ethernet and wi-fi functioned normally.  

Since that worked with no issues, I double clicked the desktop icon to Install ubuntu.  I did not check the box to download updates during the install.  I did check the box to install third party software as needed.

After a lengthy install which included downloading and installing updates as the last step, I was prompted to reboot - which I did (removing the install disk when prompted).

After I logged in and the system finished startup, I noted that once again I had no network connections.  I've reluctantly concluded that a recent change to Ubuntu is causing my network adapters(except bluetooth) to fail.  The Wi-Fi card is a Dell Wireless 1390 802.11g Mini Card and the Ethernet card is a Dell 10/100 Integrated NIC and Modem.  All are the original equipment shipped in late 2007 with the Dell Inspiron 1721 Laptop.

I am now out of ideas as to how I might get around this issue.  I would be happy to supply additional information if anyone has any suggestions.
Thanks in advance
Gerry

---

### Post by TheFu on 2018-09-22
Compare the drivers between the working and non-working installs.  It is possible that the recognition code was "improved" for newer devices and broke for older ones.

I would use **lshw -C network** and make a note of the driver AND the driver version.  The good news is that you can use the 16.04.1 "Try Ubuntu" to get the working version. No need to re-re-reinstall.

---

### Post by gerry-q on 2018-09-22
Thank you for the quick reply to my issue.
As I was reviewing my post, I realised that the problem could be caused if a "Third Part Driver" was being installed ..... the "Try Ubuntu" option probably does NOT use third party software at all.

So I did another install but this time I did not check the box to install third party software,  It worked !  My ethernet network adapter is back.

I also used the command you identified so that I could determine the name and version of the driver(s).  The output is attached.

Pardon my inexperience but how would I locate and install these drivers if I was going to repair a non functional installation ?  Feel free to point me to a tutorial or online article ..... I don't expect you to spend a lot of effort helping me to learn.

Thanks again for your help.
Gerry

---

### Post by ubfan1 on 2018-09-23
Your 4311 chip is one of the Broadcom chips, which have working open source drivers (the b43) , but still lack some firmware necessary for the chip to work.  Search this site and askubuntu.com for broadcom -- there must be hundreds of Q/As.

---

### Post by TheFu on 2018-09-23
That's 1. Which is it?  The working or the non-working?

Posting this would have been easier for me:

```
$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:b1:d7:01
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 1
00bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=
2.0 duplex=full ip=192.168.2.43 latency=64 link=yes multicast=yes port=twisted p
air speed=100Mbit/s
       resources: irq:21 memory:fe5fe000-fe5fffff
```
 Where's the other?  Also, only work with 1 device at a time. Either the wired connection or the wifi. Don't confuse people.  The driver above is "b44" and the version is "2.0".  If it is working, then that is what you want, or a newer version of the same "b44" driver.

For wired connections, I've learned to avoid certain vendors.  Broadcom is one.  Marvell, Realtek are others.  I seek out Intel PRO/1000 adaptors, since those almost always "just work" without any any hassles.  In the old days, the Intel NiCs were $100+, but these days they are available on motherboards and lacking that, $25. That's a tiny price to pay for zero hassle networking. At least to me.  The Intel NICs off load more processing from the CPU than other NICs, IME.

---

### Post by gerry-q on 2018-09-23
The NewtworkDrivers.txt attachment to my post is the result of "sudo lshw -C network" executed after booting from a newly installed LTS16.04.1 created without enabling third party software to be loaded during the installation.

The resulting HDD O/S contains a working ethernet connection.  However, the Wi-Fi adapter (BCM4311) is not functional and no wi-fi connection is available.  An unfortunate result for a laptop pc but definitely better than no network adapters at all.

I'm sorry if you found my reply confusing.  I thought my statement was pretty explicit: "  It worked !  My ethernet network adapter is back."

I had also interpreted from my attachment that the driver name was b44 and version was 2.0.  Thanks for confirming that.

I still do not know how to make use of the driver name and version ...... I will have to do the research myself I guess.

Thanks for your help TheFu
Gerry

---

### Post by TheFu on 2018-09-23
>  I thought my statement was pretty explicit: " It worked ! My ethernet network adapter is back." But it didn't say which installed OS or if any extra steps were needed to get the driver working.  That is kinda important.

Google "ubuntu 16.04 b44 driver" ... see what comes up.

As for troubleshooting the wifi, do the same thing, but be certain to disable the wired NIC first.  Having both wired and wifi on the same subnet is too complex for normal users. routing doesn't always work the way regular users think it should.

---

