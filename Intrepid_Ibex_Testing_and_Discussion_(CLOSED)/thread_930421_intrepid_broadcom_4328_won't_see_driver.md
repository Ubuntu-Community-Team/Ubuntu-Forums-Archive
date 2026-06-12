---
title: "intrepid broadcom 4328 won't see driver"
date: 2008-09-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by unclecameron on 2008-09-26
I have just done an upgrade from hardy to intrepid, hardy was using fwcutter/ndiswrapper successfully, intrepid won't see it

```

 lshw -C Network

 *-network
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

```
```

dmesg | grep -e ndis -e wlan
[  111.844328] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)

```
I successfull ran:
```

./usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

```
after apt-get installing b43-fwcutter. It downloaded and installed the code, I see the firmware in /lib/firmware/b43, but my network manager just doesn't see it
```

iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.

```
Wired works fine, the physical wireless switch is on. Anyone having any luck with this?

---

### Post by Idefix82 on 2008-09-26
I have the same card and this worked for me:
[http://ubuntuforums.org/showthread.php?t=616801]("http://ubuntuforums.org/showthread.php?t=616801")
on Hardy. You could try it on Intrepid, too. It's a matter of two minutes.

---

### Post by Ayuthia on 2008-09-26
> **unclecameron said:**
> I have just done an upgrade from hardy to intrepid, hardy was using fwcutter/ndiswrapper successfully, intrepid won't see it

```

 lshw -C Network

 *-network
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

```
```

dmesg | grep -e ndis -e wlan
[  111.844328] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)

```
I successfull ran:
```

./usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

```
after apt-get installing b43-fwcutter. It downloaded and installed the code, I see the firmware in /lib/firmware/b43, but my network manager just doesn't see it
```

iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.

```
Wired works fine, the physical wireless switch is on. Anyone having any luck with this?
The b43 driver does not work with the 4328 card yet so that driver needs to be blacklisted.  Since you are using Intrepid, the wl driver should be out there for you (The new Broadcom Linux driver--proprietary instead of the open source b43 version).  You might check and see if System->Administration->Hardware Drivers has it out there for you.  You will need to disable the b43 option and enable the wl option.  You will also need to blacklist ndiswrapper if you are going to use the wl driver.

---

### Post by unclecameron on 2008-09-26
I blacklisted them in /etc/modprobe.d/blacklist
```

# replaced by b43 and ssb.
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb

```
wl was already enabled by default, but I rebooted and still it doesn't work.
```

dmesg | grep -e ndis -e wlan

```
shows no results, neither did ps aux for ndis. The odd thing is that I had this chipset working with hardy running using the bcmwl5.inf driver, I'm "pretty sure" I wasn't using the wl driver, then I might've just been ignorant of what was really happening :) Anyway, it initially didn't work on Hardy either, until I installed the bcm/ndiswrapper, then it worked fine.

---

### Post by unclecameron on 2008-09-26
ok, I figured it out, the problem is with the wl driver, not the ndiswrapper/bcm one. It has the same bug and workaround you need for Hardy listed here [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") down at the bottom. Even after you load the correct driver, for some reason it doesn't load things in the right order, that's the problem. Hope this helps someone else, now Intrepid is working (almost) perfectly on Alpha5 :)

---

### Post by jenoki on 2008-09-26
I loaded suceessfully 'wl' driver when **DISABLE** on-board Broadcom 4401 wired LAN from **BIOS Setup**,
showed up as eth1, recognized on Network Manager, and Connect successfully with my AP:KS

thanks.

---

### Post by Ek0nomik on 2008-10-06
I just installed Intrepid today, has anyone gotten this working?  Does the load order of certain modules need to be changed?  I know according to Broadcom the driver doesn't work with b44, which a lot of wired network cards use.

---

### Post by unclecameron on 2008-10-25
it works with 4328 cards at least, mine has been stable for a long time now and acts perfectly, even after all the updates since alpha5 when I first installed.

---

