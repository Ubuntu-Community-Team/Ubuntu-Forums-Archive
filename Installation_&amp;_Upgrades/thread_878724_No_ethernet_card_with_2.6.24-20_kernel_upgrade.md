---
title: "No ethernet card with 2.6.24-20 kernel upgrade"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by puccio on 2008-08-03
Some days ago I upgraded my Ubuntu passing from a kernel **2.6.24-19** to a **2.6.24-20**.

Booting with this new kernel 2.6.24.-20, _my ethernet card does not work_ (it is not listed when I do *ifconfig -a*)

If I boot with the previous 2.6.24-19 kernel, everthing works fine. Here is it an ```
lspci
``` from it to see which Ethernet card I have:

```
Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Inspiron 6400
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at ef9fe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
```


Does anybody have any clue? 

Thanks in advance.

---

### Post by Pumalite on 2008-08-03
Post:
lshw -C network

---

### Post by puccio on 2008-08-03
Here it is (the output is performed launching the command while using the working kernel):

```
*-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:d0:b5:b3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=10.0.0.104 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
```

---

### Post by Pumalite on 2008-08-03
According to this your card is recognized by the kernel and the module is loaded You just have to configure it.

---

### Post by puccio on 2008-08-03
That was the output from the working kernel, this is instead the one from the 2.6.24-20 kernel which does *not* work:

```
 *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
```

Any idea? :confused:

---

### Post by Pumalite on 2008-08-03
In this kernel; the card is not recognized. Try reinstalling the driver

---

### Post by puccio on 2008-08-03
Hi,
first of all thanks for the reply.

But, what do you mean exactly by "try reinstalling the driver"? I mean, up to now I haven't installed any driver manually, everything worked fine...

I feel it strange if I had to tweak manually my system after a simple upgrade....

---

### Post by Pumalite on 2008-08-03
Try this: open up all your repos except src and do a:
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by puccio on 2008-08-03
Thanks, I did like you proposed and it works now :-)

---

