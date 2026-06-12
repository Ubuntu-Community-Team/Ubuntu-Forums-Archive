---
title: "Problem installing"
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by kanyini on 2011-03-29
Hi. I have Acer Aspire One ZG5 and i had problem with it recently, it didnt boot up so i had to flash the bios. After the flashing, my operating system was missing (ubuntu).

So i did bootable usb stick with ubuntu 10.10 in it and plugged in, for my surprise i didnt have enough space (2.6 GB :confused:) ? I tried to clean up some drive space in Gparted partition editor, but i only saw my usb stick available and no other drives?

All i did was  "run ubuntu from usb" but cant install cos no space..

what can i do? dont have operating system currently.

thanks..

---

### Post by whych on 2011-03-29
It looks like your hard drive isn't being detected by the new bios.
First try entering the bios setup and check whether it is detected.
If it isn't detected you have a problem with either the motherboard hardware or the drive.
If it's the drive, the best is to get a large sdhc card and install to that.

---

### Post by kanyini on 2011-03-30
Hi thanks for answering.

I went to bios and it says: "HDD Model Name: None"

So is my HDD broken?

---

### Post by galacticaboy on 2011-03-30
It may not be broken, the connecting cords could just be loose, or heck it may be broken. If you know what you are doing take it apart and check to see that the Hard Drive is plugged in all the way. If it will void a warranty I would take it back or take it to a PC store and have them look at it.

---

### Post by Sean Moran on 2011-03-30
> **kanyini said:**
> Hi thanks for answering.

I went to bios and it says: "HDD Model Name: None"

So is my HDD broken?
Not sure whether this model is a desktop or a laptop, but if it's a desktop and it's possible to pop the case, you might have some luck if you *carefully* unplug and reseat the IDE and power cable connectors at the HDD end, and gently at the motherboard end for the IDE cable.  It maybe as simple as something loose inside, but one would expect the BIOS to pickup the presence of the hard disk if it's powered up and talking to the motherboard.

There's also a good rule-of-thumb for hardware techs: Change the cable first.  Cables are cheaper than new hard disks.  Try another cable before buying a new hard disk.

---

### Post by kanyini on 2011-03-30
Hi, its a laptop.

So my best bet would be buying a sd card and install ubuntu on that? (like[ whych]("http://ubuntuforums.org/member.php?u=678190") [U]kindly suggested)
[/U]

---

### Post by Dutch70 on 2011-03-30
You may want to check to see if it's still under warranty. I don't know how old your laptop is, but it's worth checking on before you do anything.

---

