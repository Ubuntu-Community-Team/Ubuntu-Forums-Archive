---
title: "ubuntu will install but wont boot cuz BROADCOM"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by ginormusus on 2007-12-01
ok, well i used the live cd, i think 7.10 is the name. or something like that and after fooling around with it running on cd. i liked it so i installed it. everything went well until i tried to boot it. it loads the Ubuntu logo and then stops, shows a bunch of words and then decides to say something like this " brodcom boot error"  and just stops booting because of the broadcom wifi 43**. so cant anyone help me plz

i got a compaq c500 series laptop, 1 gig of ddr2 ram, core duo CPU 1.73ghz and Intel 945gpu

---

### Post by Pumalite on 2007-12-01
Are you wired to the Internet while you install?

---

### Post by ginormusus on 2007-12-01
no, its a latop so wifi

---

### Post by ginormusus on 2007-12-01
but from what i understand, broadcom 43** series wifi adapters or what ever there called, are notorious for having problems with other operating systems besides windows

---

### Post by Pumalite on 2007-12-01
You have to be wired for the installation. You configure your wireless later.

---

### Post by ginormusus on 2007-12-01
really thats it! im gonna post back later, if this works ur my hero lol, jk but seriously thank u

---

### Post by ginormusus on 2007-12-01
unfortunatly no it did the same thing but some good news, the error code. 

" [50.088000]"bcm43**_microcode5fw" not avalable or load failed  "    

so thats it, any thoughts?

---

### Post by Pumalite on 2007-12-01
It seems it failed to load the driver for your Broadcom. Check here and maybe you can get a new card.
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

---

### Post by ginormusus on 2007-12-01
my wifi is built in, even with adding another. the broadcom will still be stuck inide effecting the linux, is there any way to get linux to even boot so i can install the drivers? iv tried safe mode and got nothing and it runs fine on the cd so there must be a way

---

### Post by Pumalite on 2007-12-01
Start from scratch to make sure everything is OK. Do md5sum on your iso, burn at 4x in good quality CD-R media, check the CD's integrity before install.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by teryowen on 2007-12-01
ya i had the same problem i have a dell 1501 with the bcm43xx, and wiring it up worked.

---

### Post by ginormusus on 2007-12-01
yep did all that but ill download it again and burn it at a slow speed, any other thoughts as to what it could be?

---

### Post by ginormusus on 2007-12-01
> **teryowen said:**
> ya i had the same problem i have a dell 1501 with the bcm43xx, and wiring it up worked.

what do you mean?

---

### Post by teryowen on 2007-12-01
I mean taking an ethernet cable and connecting to the net using a wire, so that you can get the correct drivers.

---

### Post by ginormusus on 2007-12-01
do i have to do that while installing?  because i tried after the installation

---

### Post by teryowen on 2007-12-01
ya before the installation get an internet connection, because it installs some patches i believe.

On my dell 1501 laptop the first time i installed it was all messed up, then i tried with the internet connection and it worked so try that out.

So connect to the internet and begin installation

---

### Post by ginormusus on 2007-12-02
cool thanks

---

