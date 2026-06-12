---
title: "Installation on Crosshair IV with PhenomII 1055T and 2 SSD WD SiliconEdge in RAID 0"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by patrick.dalla on 2010-08-22
Hi,

I'm trying to install ubuntu 10.04_01 on this machine config:
- Phenom II X6 1055T
- Crosshair IV Formula
- Kingston 2GB memory DDR3 1333MHz
- ATI Radeon 5870
- 2 SSDs Western Digital SiliconEdge Blue 64GB.

I've configured the 2 SSDs in RAID 0, and tried to install ubuntu on it. The AMD64 version doesn't even boot totally. The I386 version install finishes, but when I try to boot nothing happens.

Someone with a help?

---

### Post by Icky_Ev on 2010-08-22
Out of curiosity, will it install and run on a non-RAID set up?

Here's my input (take it for what it's worth): 

I had a very, very similar set up to yours (1055, ASUS XTD, ATI 5770) and have spend the last 2 weeks struggling with system instability, crashes, lost data and general grief. The only common element in all the troubleshooting was the ASUS board. 

I'm going to RMA the board as faulty, but now I'm wondering if it (ASUS) just doesn't play terribly nice with Lucid. It's a pretty big jump to assume that, but given how similar my setup is to yours, I figured I would contribute my own tale of woe. 

My 1055 is sitting in a crummy Gigabyte right now, and so far, so good.

---

### Post by ronparent on 2010-08-22
Try to get the system to boot to a live cd session first. This will help debug any startup problems. Also find any boot parameters you may need.

---

