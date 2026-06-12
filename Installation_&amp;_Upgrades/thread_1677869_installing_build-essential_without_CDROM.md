---
title: "installing build-essential without CDROM"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by ryanchang on 2011-01-29
Hey Community,

I recently purchased an ASUS 1015PED netbook and installed Ubuntu 10.10 NBR from a USB. My netbook model needs an updated driver from Broadcom to get it working with the chipset. Other users with my model have gotten the driver installed and working, but I have not. After hours of research I discovered that I needed build-essential installed to compile the tar.gz, but I **don't** have a CD-ROM drive. 

I got as far as mounting the .iso as a CD, but ubuntu still asks me to insert a physical CD. I know I need to make some sort of symbolic link between the mounted .iso and aptitude so aptitude believes that the mounted .iso is actually a CDROM. Any advice? I just need to get wi-fi working before the semester starts, and I don't want to manually install potentially 60+ dependencies!

Thanks a ton in advance,
Ryan

---

### Post by zvacet on 2011-01-29
Ubuntu software center>software repositories>uncheck CD as repository and refresh (or close ,you will see option for that).After that install build-essential from synaptic or you can do it from terminal

```
sudo apt-get install build-essential
```

---

### Post by ajgreeny on 2011-01-29
You will need a wired connection to install all updates, then to search for the updated driver you need, (broadcom-sta-common?).  You may then find that you can use wireless without problems.

---

### Post by scottmac112 on 2011-01-29
And if that doesn't work, you could just install NDISwrapper. It only requires 2 DEBs, and you just use the Windows driver. But it might be easier to just use the wired connection and go through the "Additional Drivers" panel.

---

