---
title: "[SOLVED] Ubuntu installination prompt?"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by Camilia on 2008-09-01
Hi I forgot my password so I am reinstalling ubuntu and after click install 95% got prompt for:
dev/sda2 fat38
dev/sda1 nffs
dev/sda5ex3
dev/sda6swap
Which 1 do I select?

Now my computer is:
Emachine T3095
CPU:            AMD Sempron&#8482; 3000+ Processor(2GHz, 333MHz FSB, 512KB L2) 
Chipset:        NVIDIA® nForce&#8482; 2 chipset
Memory:         512MB DDR (1 × 512MB) SDRAM (PC2700)
                Expandable to 2GB
Hard Drive: 	80GB HDD
Optical Drive: 	DVD±RW 16x Multi Format Double Layer
Video:          NVIDIA® GeForce®4&#8482; MX graphics 64MB DDR shared memory
Network: 	10/100Mbps integrated Ethernet LAN

---

### Post by Pumalite on 2008-09-01
You can install on top of sda5. You have to go 'Manual' and pick that partition. You can ignore /swap

---

### Post by JC Cheloven on 2008-09-01
fat38 ??? ---->>  Not 'fat32' ????????

Anyway, I guess your previous ubuntu partition is /dev/sda5. You should safely Re-Install ubuntu there.

---

### Post by Camilia on 2008-09-01
Problem solved!! Thank you for the help!!

---

