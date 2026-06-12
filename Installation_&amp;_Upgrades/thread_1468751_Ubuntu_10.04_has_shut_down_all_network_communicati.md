---
title: "Ubuntu 10.04 has shut down all network communication"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by flopwich on 2010-05-01
I upgraded to 10.04 yesterday and Firefox, or rather something I don't know that's replaced it called "Namoroku", worked fine.  Today Firefox won't work and Thunderbird and Evolution won't work, either with wifi or with a direct Ethernet link.  When I did the System Test, it claimed that the internet connection was fine, but I can't get anything in or out.  This is on an Acer Aspire One that I have configured as dual boot with Windows 7.  Under Windows Firefox works fine on the wifi.  I haven't checked on the Ethernet connection, but assume it works if the wifi does.

Ubuntu also tells me that my battery is "broken", although that's a lesser problem.  I can ignore that.  Windows has no problem with the battery, either.  

Any help for the communications problems would be appreciated.

Here's the sudo lshw -c net output...

          [FONT=DejaVu Sans, sans-serif][SIZE=2]*-network               [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]description: Ethernet interface [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]product: Atheros AR8132 / L1c Gigabit Ethernet Adapter [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]vendor: Atheros Communications [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]physical id: 0 [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]bus info: pci@0000:01:00.0 [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]logical name: eth0 [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]version: c0 [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]serial: 70:5a:b6:21:f3:fd [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]capacity: 100MB/s [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]width: 64 bits [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]clock: 33MHz [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]resources: irq:27 memory:57000000-5703ffff ioport:5000(size=128) [/SIZE][/FONT] 
   [FONT=DejaVu Sans, sans-serif][SIZE=2]*-network [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]description: Wireless interface [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]product: AR9285 Wireless Network Adapter (PCI-Express) [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]vendor: Atheros Communications Inc. [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]physical id: 0 [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]bus info: pci@0000:02:00.0 [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]logical name: wlan0 [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]version: 01 [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]serial: c4:17:fe:62:77:06 [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]width: 64 bits [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]clock: 33MHz [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]configuration: broadcast=yes driver=ath9k ip=192.168.2.100 latency=0 multicast=yes wireless=IEEE 802.11bgn [/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]resources: irq:17 memory:56000000-5600ffff [/SIZE][/FONT]

---

### Post by flopwich on 2010-05-02
I just discovered that I am able to PING my email server, so I'm not sure what's going on.  Communications continue to work fine in Windows, however.

---

### Post by udippel on 2010-05-04
> **flopwich said:**
> I just discovered that I am able to PING my email server, so I'm not sure what's going on.  Communications continue to work fine in Windows, however.

Yes. Make this a Ubuntu bug. I use to experience the same; read the short version up here:
[http://ubuntuforums.org/showthread.php?p=9232313#post9232313](http://ubuntuforums.org/showthread.php?p=9232313#post9232313)

Uwe

---

### Post by flopwich on 2010-05-04
Thank you for pointing me to that information.  The process describes looks a little over my head and I wouldn't have a clue how to "put things back" if it didn't work.  Also, the symptoms my computer shows are a little different.  For example, it won't work any better with an Ethernet connection to my router any better than with wireless.  Last night the wireless started working just fine, for a while.  Tonight it will connect to some sites, like the National Weather Service, but not Google, regardless of whether it's a wireless or a wired connection.  Update Manager and System Testing can both connect just fine, wirelessly.

Everything continues to work just fine in Windows.  As much as I like Ubuntu and would prefer to use it, and most especially delight in being able to cut the cord connecting me to the Borg (Microsoft), this one's a show-stopper.  I must once more accept that resistance is futile and be assimilated, hoping that if I check upgrades in Ubuntu once in a wile, one of the upgrades will fix this bug.

Thanks again for your help.

---

### Post by flopwich on 2010-05-12
For whatever it's worth, the problem with Firefox had to do with IPv6.  

First, I downloaded the latest version of Firefox, then hunted down that Namoroka thing and deleted it and the directory it was in and installed Firefox.  

From a suggestion found elsewhere on here, you open Firefox, enter "about:config" and it pulls up all the configuration parameters for Firefox.  Search for "IPv6disable" and set it to "true".  Firefox worked perfectly.  Now if I could just find the same fix for Thunderbird I'd be on a roll.  So the problem is half-solved.

I don't know if this is a bug in Ubuntu or in Firefox, but it happened with the upgrade from Ubuntu 8 to 9 and now again from 9 to 10.  It never happens in Windows.  It'd be nice if somebody would fix it.  It looks like the routines to handle IPv6 aren't working very well, where ever it is.

The problem with the battery seems to have fixed itself. (?)

---

