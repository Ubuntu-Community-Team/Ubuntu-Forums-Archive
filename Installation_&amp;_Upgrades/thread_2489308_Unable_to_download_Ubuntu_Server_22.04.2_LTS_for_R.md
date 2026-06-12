---
title: "Unable to download Ubuntu Server 22.04.2 LTS for RaspberryPi 4 - Server Error"
date: 2023-07-25
forum: Installation &amp; Upgrades
---

### Post by birdingpix on 2023-07-25
I am unable to download Ubuntu Server 22.04.2 LTS for RaspberryPi 4 ... I always get an 'Internal Server Error'. 

How can I get this OS?   Is it no longer available for Raspberry Pi?   I have tried to download it via both directly logged-into Ubuntu... or using Raspberry Pi Imager program... both end up with Internal Server Erro upon beginning the download. 

Please help!

Thank you
Dave

---

### Post by MAFoElffen on 2023-07-25
There is currently a bigger problem.

[https://cdimage.ubuntu.com/releases/22.04.2/release/](https://cdimage.ubuntu.com/releases/22.04.2/release/) <--- That whole web directory is missing from their download server

I'm sure that it should be fixed quickly, as that is a whole lot of images that has no current access.

I reported it to launchpad as a bug: [https://bugs.launchpad.net/ubuntu-cdimage/+bug/2028731](https://bugs.launchpad.net/ubuntu-cdimage/+bug/2028731)

---

### Post by guiverc on 2023-07-25
I take it the issue has been resolved (*from bug report*), but there are also mirrors of downloads

[https://launchpad.net/ubuntu/+cdmirrors](https://launchpad.net/ubuntu/+cdmirrors)

Do note:  the raspberry pi is a *port* and not all mirrors include the ports.

Thanks @MAFoElffen for reporting & getting this resolved so quickly !

---

### Post by MAFoElffen on 2023-07-25
That "was" quick. LOL

@guiverc:
I had the same idea and investigated the mirrors, in case there was an alternate solution... which all the mirrors I checked (I checked several in the US) have copies of the amd64 releases, but for ports 'links' on the mirrors they all pointed back to the Ubuntu servers at [https://cdimage.ubuntu.com/]("https://cdimage.ubuntu.com/releases/22.04.2/release/") so no love 'there'. I even checked Universities and ISP'es that had mirrors. LOL

---

### Post by guiverc on 2023-07-25
Yeah, my mention of mirrors (*even with mention of ARM being a port & thus not all include it*) would be read as most, or at least a good portion of them provide PORT support, where most don't include ports too in my experience.

I'm unaware of a **PORT CD MIRROR** list, which is why I provided what I did, despite my own belief that it's only a *[smallish*] portion of them that are useful for ***port*** downloads.  I have [*historically*] downloaded raspberry pi images from port mirror(s).

> **MAFoElffen said:**
> 
I'm sure that it should be fixed quickly,

They had to, Steve (*Vorlon*) couldn't let you be wrong :P

---

