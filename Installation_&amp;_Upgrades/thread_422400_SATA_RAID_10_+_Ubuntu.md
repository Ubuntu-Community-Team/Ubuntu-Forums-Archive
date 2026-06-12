---
title: "SATA RAID 10 + Ubuntu?"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by CarrierII on 2007-04-25
Hi
I am trying to install Ubuntu 7.04 onto my PC, which has a SATA RAID 0+1 (AKA 10) - I currently have a windows installation and I am aiming to dual boot (I've already backed up my system) but I'm wondering how do I get Ubuntu to recognise and use my SATA RAID?

The disks are all Maxtor ~ 80 GB, 16 MB Cache, 7200 RPM and the storage controller is an Intel 82801GR/GH which came on my south bridge as part of an Intel 945 chipset.

The rest of my system is: Intel P4D, 2.66 Ghz. 1 GB RAM, ATI X1650, and two generic sony DVD drives.

Help please.

CarrierII

Edit - using the AMD/IA 64 version.

---

### Post by CarrierII on 2007-04-25
Polite bump.
(one more topic and this would've moved to the second page)

---

### Post by derrekito on 2007-04-25
I'm trying to figure this out as well for Feisty.

---

### Post by CarrierII on 2007-04-25
Thanks (And bump so anyone else might see it)

---

### Post by psusi on 2007-04-25
You should read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto) for more info, but I am not sure if 0+1 is supported or not.

---

### Post by derrekito on 2007-04-25
> **psusi said:**
> You should read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto) for more info, but I am not sure if 0+1 is supported or not.

will this still work while dual booting with windows off the same raid?

---

### Post by mozkill on 2007-04-25
what do people mean when they talk about "fake raid" ?????   why not use a real raid?  can someone answer me on this or provide a link that explains why a real hardware raid is not possible?

i want to build a computer with SATA raid and im wondering if i will be able to use Ubuntu...

---

### Post by CarrierII on 2007-04-26
I wil be using my --Hardware-- disk controller to create a --hardware-- RAID. Will Ubuntu use it properly or will it read all sorts of weird things?

I read that link... I don't know if this is a true hardware RAID or not, Windows does require a file "iastor.sys" to use it , if that tells anyone...

---

### Post by psusi on 2007-04-26
Yea, that's a fake raid.  If you read the link it explains that a lot of motherboards these days come with on board "sata raid" but they are in fact, just regular sata controllers with special bios and drivers for windows that fake it.  

Getting it working in linux is a pain, but possible, which is why that howto exists.

---

### Post by CarrierII on 2007-04-26
Thanks.

---

### Post by ataylor on 2007-04-27
Gidday,

The problem is not Raid 10. I have a 3Ware 9650 hardware raid card which is set up with 4x340Mb SATA drives in a Raid 10 array - no problems.

I'd start looking at the chipset running the Raid and see if it is supported.

Rgds/Alan

---

