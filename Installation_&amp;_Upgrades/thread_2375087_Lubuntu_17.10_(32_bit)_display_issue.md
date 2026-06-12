---
title: "Lubuntu 17.10 (32 bit) display issue"
date: 2017-10-21
forum: Installation &amp; Upgrades
---

### Post by WillEllen on 2017-10-21
Upgraded from 17.04 which worked well.  When I changed the display resolution in 17.10 the system froze and had to be re-booted. When it came back up the GUI was just the desktop picture (no apps).

I installed a new 17.10 from a DVD with the same results.  I saw information on-line that some kind of option is offered on the log-in screen but it was not on mine.  

Is there a way to resurrect my favorite OS or is my display card no longer compatible.

---

### Post by mörgæs on 2017-10-22
Depends. You have not told us which card.

Please copy and paste the command ```
sudo lshw -sanitize > lshw.txt
``` to the terminal, run it and post lshw.txt in CODE tags.

---

### Post by WillEllen on 2017-10-22
*-display:0
                description: VGA compatible controller
                product: RV350 [Radeon 9550/9600/X1050 Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=32 mingnt=8
                resources: irq:16 memory:c0000000-cfffffff ioport:c000(size=256) memory:e9000000-e900ffff memory:c0000-dffff
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV350 [Radeon 9550/9600/X1050 Series] (Secondary)
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm cap_list
                configuration: latency=32 mingnt=8
                resources: memory:d0000000-dfffffff memory:e9010000-e901ffff

---

### Post by WillEllen on 2017-10-23
Solved  Replaced the Radeon display card with a Nvidia and all is well.

---

