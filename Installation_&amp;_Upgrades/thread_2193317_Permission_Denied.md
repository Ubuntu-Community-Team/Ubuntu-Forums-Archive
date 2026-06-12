---
title: "Permission Denied"
date: 2013-12-12
forum: Installation &amp; Upgrades
---

### Post by nibal on 2013-12-12
I have a 12.04 i386 Ubuntu Desktop. I need to bind uio_pci_generic module to a new prototype pci card that i am developing. Lshw sees the card, but reports it "UNCLAIMED".
The way to bind the module to my pci card is to manipulate and write stuff into /sys/bus/pci/...
However, when I try to use sudo, I get permission denied. Sudo works with all other commands:

> 

DrWho:~-> sudo touch test
DrWho:~-> ls -la test
-rw-r--r-- 1 root root 0 Dec 12 14:04 test



Doesn't, however, work with /sys/bus/pci...:(

> 
DrWho:~-> sudo echo "8086 10f5" > /sys/bus/pci/drivers/uio_pci_generic/new_id
bash: /sys/bus/pci/drivers/uio_pci_generic/new_id: Permission denied
DrWho:~-> ls -la /sys/bus/pci/drivers/uio_pci_generic/new_id
--w------- 1 root root 4096 Dec 12 13:46 /sys/bus/pci/drivers/uio_pci_generic/new_id


What can i do, short of changing distro?

TIA
Nikos

---

### Post by steeldriver on 2013-12-12
You are applying sudo to the echo (which doesn't need it) but not to the part that redirects the output to a root-owned file (which does) - you have a bunch of options e.g.

1. 
```
echo "stuff" | **sudo tee** /root/owned/file
```

2.  
```
**sudo bash -c** 'echo "stuff" > /root/owned/file'
```

3.
```

**sudo -i**
echo "stuff" > /root/owned/file
exit

```

---

### Post by coffeecat on 2013-12-12
> **nibal said:**
> 
What can i do, short of changing distro?


Change distro? Since you have encountered an issue with bash and not with Ubuntu, that would not achieve much.

Try this:

```
echo "8086 10f5" | sudo tee /sys/bus/pci/drivers/uio_pci_generic/new_id
```

You were trying to use the redirect >. The output of a redirect does not inherit the sudo permission.

**Edit**: ninja'd by steeldriver who has given you some alternatives. Good to see choice!

---

### Post by nibal on 2013-12-12
> **coffeecat said:**
> Change distro? Since you have encountered an issue with bash and not with Ubuntu, that would not achieve much.

Well, the instructions @ [http://www.mjmwired.net/kernel/Documentation/DocBook/uio-howto.tmpl](http://www.mjmwired.net/kernel/Documentation/DocBook/uio-howto.tmpl) clearly used a ">" redirector and apparently worked. i upgraded my kernel in case it was a kernel issue to 3.11 (latest for 12.04) but it is not. I write into the kernel tables there, using bash, and permissions could be controlled by the kernel. Bash &sudo seemed to work fine. Tried also:

> 
DrWho:~-> sudo sh -c "echo -n '0000:04:00.0' > /sys/bus/pci/drivers/uio_pci_generic/bind"
[sudo] password for nbal: 


to no avail.

```
echo "8086 10f5" | sudo tee /sys/bus/pci/drivers/uio_pci_generic/new_id
```

> You were trying to use the redirect >. The output of a redirect does not inherit the sudo permission.

Thank you so much :guitar:. I didn't know that. It seems like a sudo bug. Since it is the same process, it should inherit the sudo permissions. However, your code resolved the permissions issue:

[QUOTE]
DrWho:~-> sudo echo -n 0000\:04\:00\.0 | sudo tee /sys/bus/pci/drivers/uio_pci_generic/bind
0000:04:00.0tee: /sys/bus/pci/drivers/uio_pci_generic/bind: No such device


I am not home yet. Unfortunately, as you can see, I still need the right device. lspci and lshw report the device I use:

> 
DrWho:~-> lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
.
.
.
04:00.0 Multimedia video controller: NEC Corporation Device 0165 (rev 0b)

DrWho:~> sudo lshw
*-pci:3
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:f7800000-f78fffff
           *-multimedia UNCLAIMED
                description: Multimedia video controller
                product: NEC Corporation
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 0b
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:f7800000-f7801fff memory:f7802000-f78027ff


Any ideas on this? I tried also at the PCI bridge address, without success :(

TIA

---

### Post by nibal on 2013-12-13
> Any ideas on this? I tried also at the PCI bridge address, without success

Forgot to mention that my prototype is a PCI express (mini PCI slot) card. This appears to be a different protocol than pci 2.3, that the driver requires. When faced with an incompatible card, either older pci 2.2 or newer pci express, uio_pci_generic responds with the misleading message "No such device":(
Have to change board and start all over again.

---

