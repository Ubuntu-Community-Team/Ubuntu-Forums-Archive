---
title: "Installing Fax Modem"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by marciano#1 on 2007-10-30
This my new system: 
D945GCNL Intel motherboard with Intel Core 2 Duo E4400 Processor.
Feisty
I have a problem with Encore Modem Fax PCI card: ENF656-ESW-MOPR
This is my second one (I got the same problem with a similar card).
The problem is that after installing the card, Ethernet is disabled. It is like no wire is installed to the router: led light is off.
What can I do?
Thank you in advance.
PS: Sometimes reinstalling the card LAN launches fine
#lshw
   *-pci:5
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-communication
                description: Modem
                product: Motorola
                vendor: Motorola
                physical id: 4
                bus info: pci@06:04.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: generic bus_master cap_list
                configuration: driver=serial latency=32 maxlatency=62 mingnt=1
                resources: iomemory:52000000-52000fff ioport:1000-10ff irq:18

Testing with scanModem the program hangs up "expecting fi....."
Is there any other way to get a working driver for this modem?

---

