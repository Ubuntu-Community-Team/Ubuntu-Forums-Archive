---
title: "Why is 24-bit color the default?"
date: 2006-09-17
forum: Installation &amp; Upgrades
---

### Post by jruschme on 2006-09-17
Just a quick question... Why is a color depth of 24-bit the default for Ubuntu and the installer?

I just finished installing Dapper on an old IBM ThinkPad 600e with a NeoMagic graphics controller. The installation went well, but initially graphics performance seemed sub-par. This turned out to be a result of the fact that the NeoMagic Xorg driver does not support video acceleration at densitities above 16 bits. 

Changing xorg.conf to have a default depth of 16 bits brought performance to what I'd expect, but I was wondering why I had to do this step and what would have happened had I been a new or less-saavy user?

Thanks...
John

---

