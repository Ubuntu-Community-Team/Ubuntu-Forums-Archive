---
title: "wiFi driver for a Zepto3215"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by brymo on 2008-03-30
Hi
I just bought a Zepto 3215w Notebook, and can´t get my Wifi to work in Ubuntu. The computer config look like this:

SAMSUNG COMBO CD-RW/DVD
Keyboard 3x1x DK
15,4" WXGA 1280x800 - 3215WD
6 Cell Batteri
Intel® GMA X3100
Manual 3214/3215/3414/3415
1,60 GHz Intel® Core Duo T2330 533MHZ 1MB
2048MB (1024x2) DDR2 667/PC5300 SODIMM
160GB 7200rpm SATA Harddisk
**Zepto Zpro2 N-Standard (NBG)**

Does anyone know what I should do?

---

### Post by Pumalite on 2008-03-30
This will tell you if it's supported or not:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

---

### Post by brymo on 2008-03-30
Thanks

I can´t see the card anywhere on the list, so what are my options at this point. Could I get a driver anywhere?

---

### Post by Opspin on 2008-05-30
> **brymo said:**
> Hi
I just bought a Zepto 3215w Notebook, and can´t get my Wifi to work in Ubuntu. The computer config look like this:

[Their own site]("http://zepto.dk/PageControls/Product.aspx?componentid=956") says that the Zepto Zpro2 N-Standard (NBG) isn't compatible with Linux, so unless someone reverse engineer it or somehow whips up a driver for it, I'm sorry to say that with my limited knowledge, you're SOL :(

---

### Post by schleiss on 2008-06-22
I don't have a Zpro2 card myself. But promised a friend to look into if it would be possible to make it work. And this guy below appears to have done it.

[http://xodeus.dk/?page_id=141]("http://xodeus.dk/?page_id=141")

---

### Post by issih on 2008-06-22
We really need to know the actual chipset that is being used rather than the vendors name for it :)

From a brief google I suspect you have the realtek rt 2860 chipset

Can you post the output of running the following in terminal:
```
sudo lshw -C network
```

```
lspci
```

```
ifconfig -a
```

---

