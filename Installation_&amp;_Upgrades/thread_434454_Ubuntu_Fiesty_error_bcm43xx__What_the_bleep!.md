---
title: "Ubuntu Fiesty error bcm43xx_??? What the bleep!"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by yxs8495 on 2007-05-06
I have a DELL INSPIRON 9400 laptop. I had 6.10 ubuntu on a dual drive system  with windows vista on the other partition. I tried to upgrade to fiesty and now all I get is :
bcm43xx_Error:Micromodule "bcm3xx_microcode5.fx" not available or load failed

I have no idea what this means or how to correct it. I think that something is wrong with the Xserver or something.

Thanks, yxs8495

---

### Post by junior28862 on 2007-05-06
Sounds like a bad download to me.  BCM43xx is drivers for the Broadcom 43xx series wireless card.  I would check the md5 sum of the downloaded image or try installing in safe mode.

---

### Post by Josey on 2007-05-06
Just a suggestion but If you start a thread with a tiltle like "im leaving ubuntu for good" and then post the problem you'll have like 100 responses to help :P

---

### Post by pistooli on 2007-05-06
> **yxs8495 said:**
> I have a DELL INSPIRON 9400 laptop. I had 6.10 ubuntu on a dual drive system  with windows vista on the other partition. I tried to upgrade to fiesty and now all I get is :
bcm43xx_Error:Micromodule "bcm3xx_microcode5.fx" not available or load failed

I have no idea what this means or how to correct it. I think that something is wrong with the Xserver or something.

Thanks, yxs8495

you need to install and run bcm43xx-fwcutter in order to retrieve and load the correct microcode to your wifi... 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)

the above wifi is for edgy, but I followed it on feisty and my bcm43xx work just fine...

cheers - pistooli

---

