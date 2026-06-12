---
title: "Sound problem Ubuntu 9.4"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by mailtobanti on 2010-01-23
Friends, 
I have install Ubuntu9.4 fresh in my computer. Every thing is fine except sound (Traditional bug of 90% open source Linux platform ). Sound is not coming. But I think recording is going on. Please give me proper guide line to fix this thing. 

Thank you

---

### Post by tachuela on 2010-01-23
Post:
```
sudo lshw -C sound
```

---

### Post by mailtobanti on 2010-01-23
Thank you for giving me response. Please Help me to fix this issue. I am not willing to go to windows.

> **tachuela said:**
> Post:
```
sudo lshw -C sound
```

*-multimedia            
       description: Multimedia audio controller
       product: CM8738
       vendor: C-Media Electronics Inc
       physical id: 6
       bus info: pci@0000:02:06.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=C-Media PCI latency=32 maxlatency=24 mingnt=2 module=snd_cmipci

---

### Post by MasterNetra on 2010-01-23
I can only assume you mean 9.04, have you tried Ubuntu 9.10 Karmic?

---

### Post by mailtobanti on 2010-01-23
> **masternetra said:**
> i can only assume you mean 9.04, have you tried ubuntu 9.10 karmic?
no.

---

### Post by tachuela on 2010-01-23
Your output states that your kernel recognises your Sound Card ( good news ) It might be something simple. Check the volumes.
Go to Applicacions>Accesories>Terminal; type alsamixer and hit 'Enter' Make sure that all volumes are 100%

---

### Post by mailtobanti on 2010-01-24
> **tachuela said:**
> Your output states that your kernel recognises your Sound Card ( good news ) It might be something simple. Check the volumes.
Go to Applicacions>Accesories>Terminal; type alsamixer and hit 'Enter' Make sure that all volumes are 100%

Every thing is 100% percent at alsamixer. 
PLese see the  attachment JPG.

Thank you

---

### Post by tachuela on 2010-01-24
Try a Hail Mary! Go to Software Sources and open all your chanels: backposts. Partner, Updates, Propietary drivers for devices (restricted), software restricted by copyright or legal issues (multiverse ),pre-released updates, unsupported updates
Then do:
```
sudo apt-get update
sudo apt-dist-upgrade
```

Good luck!

P.S. I've done with success in the past

---

