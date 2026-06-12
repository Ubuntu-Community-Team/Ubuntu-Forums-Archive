---
title: "GeForce4mx440 over Onboard Graphics"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by bvsingh on 2006-07-05
I have a problematic 845gv based motherboard from ASRock. It has a feature called "Easy Dual Monitor" which allows both the graphics chipset(onboard and AGP) to be connected to a display each. The problem is that even though my display is connected to AGP card mx440Geforce it is not detected, instead, the onboard chipset is detected by dapper drake.

(*)Can using alternate install help me?

(*)Should I intall using onboard graphics, and later after installing is there a way to get dapper to use the agp card?

(*)I know that my agp card is on IRQ16, can I use this information to help it get detected by dapper?

Urgent help needed...

---

### Post by Dr. Nick on 2006-07-05
To change video output look at your /etc/X11/xorg.conf file under the device section. here is mine for my agp. Look into changing the busid, yours should be the same as mine since its agp. I would subsiture "nv" for nvidia untill you get the nvidia drivers installed. You can type whatever you want into the identifier section, doesnt hurt anything.

```
Section "Device"
        Identifier      "NVIDIA Corporation NV18GL [Quadro4 NVS AGP 8x]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"

```

You may have to do that using the onboard, then shut down and switch cards. Is it possible to disable onboard in the bios?

---

### Post by bigken on 2006-07-05
you need to dissable the onboard graphics via the bios if you cant dissable it you should have a option to boot from agp 1st ;)

---

### Post by bvsingh on 2006-07-05
I cant disable my onboard chipset.
I will try abovementioned solutions.
Fedora also had the same problem, SUSE detected it fine, but only want dapper.

---

