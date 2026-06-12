---
title: "mounting 3 different raid controller"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by tonylau on 2007-03-23
To whom it may concern,

I have 3 raid controllers in a 8U machine wanting to install Ubuntu 6.1 with the following hardware specification:

Motherboard: Tyan 2882-D (latest BIOS)
Memory: 4GB DDR400 ECC Register
Raid controller: 
3ware 8506-8 (2 drives installed with raid 1 setup) (latest firmware)
3ware 9500-8 (750GB x 8 with raid 5 setup) (latest firmware)
3ware 9550-16 (750GB x 16 each with raid 5 setup) (latest firmware)

I want to install the OS into the 8506-8 (raid 1), then mount the rest afterward.  The problem I am facing is the OS drive will become sdd, the rest of the raid controller will be sda, sdb, sdc.  So I am wondering if there is a noprobe option at installation, where I can organize the order?   From my experience, if I mount the OS partition as sdb, sdc, etc...instead of sda, then the OS might have some problem booting.  So I am hoping I can use noprobe for this situation.

Another question is, does anyone know how to mount a 11TB from Ubuntu?  Is it is the same with Red Hat?

Please help~
Anthony

---

