---
title: "&quot;This kernel requires following features not present on the cpu pae unable to boot pl"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by jazzmasterd on 2012-04-23
Hi guys, 

I'd like to install Linux on my old laptop. I downloaded the Ubuntu 12.04 LTS (Precise Pangolin) Beta 2, PC (Intel x86) desktop CD from ubuntu.com.

I got the following error when attempting to boot from the disc i created. 

"This kernel requires following features not present on the cpu pae unable to boot" 

I have a gateway tablet pc running windows xp currently. 

32-bit i'm pretty sure
intel(R) 
processor 1.5GHz
598MHz
504 of RAM

Have I provided enough information? What do I do next? 

-John

---

### Post by jadtech on 2012-04-23
make sure the iso you burn is 32bit , the ram seems like you might need to install the lite version lubuntu or xubuntu ..

---

### Post by jazzmasterd on 2012-04-23
I went to [http://gb.releases.ubuntu.com//precise/](http://gb.releases.ubuntu.com//precise/)
and downloaded the first item "PC (Intel x86) desktop CD"

Is that correct? 

Where do I find a "lite" version?

---

### Post by Elfy on 2012-04-23
Hi - the default Ubuntu iso now requires PAE - your CPU does not have that facility.

Try Xubuntu or Lubuntu.

[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

---

### Post by jazzmasterd on 2012-04-23
Thank you, I will try lubuntu.

---

### Post by jadtech on 2012-04-23
here is  the link for lubuntu 

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu#A32-bit_or_64-bit.3F](https://help.ubuntu.com/community/Lubuntu/GetLubuntu#A32-bit_or_64-bit.3F)

---

### Post by deckoff on 2012-04-28
I came across 12.04 beta CDs which were modified with custom kernels which dont need pae. Any links to the stable version

---

