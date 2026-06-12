---
title: "Compaq/HP 6910p No Wifi"
date: 2015-10-19
forum: MINT
---

### Post by T_S_O_P on 2015-10-19
Installed Linux Mint on said Laptop and everything was fine and then the Wi-Fi dropped. This might of happened after a suspend or hiberante as I was trying the features. I tried the forums and have read threads of people with similar issues and tried the fixes but I think I have only compounded my problems. I have never been able to get Wi-Fi again even after reboot.

---

### Post by howefield on 2015-10-19
Thread moved to the "*MINT*" forum.

---

### Post by T_S_O_P on 2015-10-19
```
sudo lshw -C network

             
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1e:ec:2a:b7:02
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.3-0 ip=192.168.0.7 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:43 memory:e4620000-e463ffff memory:e4640000-e4640fff ioport:4060(size=32)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wlan0
       version: 61
       serial: 00:1f:3b:5e:34:d9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 driverversion=3.16.0-38-generic firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:e4000000-e4001fff
```

Is that the MINT forum within this message board or the Linux Mint forum?

---

### Post by howefield on 2015-10-19
> **T_S_O_P said:**
> Is that the MINT forum within this message board or the Linux Mint forum?

The former of course.

[http://ubuntuforums.org/forumdisplay.php?f=453](http://ubuntuforums.org/forumdisplay.php?f=453)

---

### Post by T_S_O_P on 2015-10-29
I have now also installed xubuntu as a dual install, and the wireless isn't working on that platform either. Shoul I post that in the other forum?

---

### Post by Rob Sayer on 2015-10-31
If you installed Mint 17 I wouldn't expect wireless problems to go away if you installed xubuntu 14.04.  17 is based on 14.04.

You didn't say which release of mint or xubuntu you installed.  That's essential info (but not enough necessarily).

However, it means you can get better support.  Mint support is better than most distros but for non techie users *nothing* beats ubuntu support.

I actually have mint 17 on both my laptop and netbook.  But on the netbook I previously went back from mint 13 to ubuntu 12.04 because it has a pesky Broadcom wireless adapter.  It never worked very well until ubuntu 14.04/mint 17 came out.  They just don't have the networking expertise on the mint forums.  Or expertise period really.

You can post about your xubuntu wireless issues here in the regular ubuntu forum.  There are some real wireless experts here.  If you have a dual install of mint 17 and ubuntu 14.04, what works in 14.04 should work in 17 as well.  For later versions of ubuntu I would *not* assume that.  You can never assume that the same hardware config works on all releases.

I always install long term support versions of ubuntu (or whatever is based on it) unless I absolutely need a new non lts release for hardware support reasons.

Mint promotes itself as the best beginner's distro.  There is a lot of truth to that ... until you have a hardware support issue or something like that.  I like Mint ... actually I'm an ex ubuntu user a this point but that can change ... but for beginners I always recommend ubuntu for the quality of the tech support.

---

### Post by jeremy31 on 2015-11-02
It reports network disabled, so post the result of ```
rfkill list all
```
If it reports hard block: yes see if there is a switch on the computer that disables wifi

A maintenance manual shows a button above the F4 button that can enable/disable wifi

---

