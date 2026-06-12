---
title: "how to downgrade from 12.10 to 12.04?"
date: 2013-04-18
forum: Installation &amp; Upgrades
---

### Post by johncroc on 2013-04-18
My understanding of the 12.10 version of Ubuntu is that it will not be supported in the not-to-distant future.  How would I go about "downgrading" to 12.04?  Or would it be wiser the wait and upgrade to 13.04 when support for 12.10 expires?

I am a serious noob, so the more detailed and explicit you can be, the better.

Thank you in advance!

John

---

### Post by grahammechanical on 2013-04-18
Ubuntu 12.10 has 18 months support so using it will get you as far as Ubuntu 14.04. That is not the case with Ubuntu 13.04 which only has 9 months support. If you upgrade to 13.04 you will have to upgrade to 13.10 in 6 months otherwise you will have to use 13.04 for 3 months without support until 14.04 is released.

And just so you know Ubuntu 13.10 will only have 9 months support. So, you will have to upgrade to 14.04 because 13.10 will reach End Of Life 3 months before 14.10 is released. I would not bet on there being a 14.10 version. Or 15.04 and 15.10 either.

I do not believe it is possible to downgrade. There is not a utility to do it. So, now that you have 12.10 I advise that you stay with it until 14.04 and then upgrade and stay with 14.04 until 16.04. Mark Shuttleworth (the boss) only wanted 13.04 and 13.10 to have 7 months support. And I have just read that the Ubuntu shop will not be selling 13.04 or 13.10 DVDs. 

Ubuntu releases every two years a version that has 5 years support. It is released at the end of April and it is called Long Term Support (LTS). I can see a future where ubuntu is only released every two years and not every six months as at present. Sometimes were forget that free to download does not mean without cost to make. Something has to give. It may be the number of releases of Ubuntu we get.

Regards.

---

### Post by johncroc on 2013-04-18
Thank you, grahammechanical.  Awesome explanation.

---

### Post by slaado on 2013-04-21
Hi, there are understandable reasons.
Otherwise there is a Problem with sis 771/671 chipset and no solution for 12.10 distribution, or...

[http://ajoliveira.com/ajoliveira/uk/software/xorg.php](http://ajoliveira.com/ajoliveira/uk/software/xorg.php)

Thanx
Slado

---

### Post by Bucky Ball on 2013-04-21
12.04 LTS has five years support, until April 2017. 14.04 LTS is the next long-term support release. There is now downgrading, full install.

I would install 12.04 LTS and, if you want or need to, upgrade to the next LTS six months after it is released. The interim releases *do not* upgrade to the next LTS release. To get to 14.04 from 12.10 you would need to upgrade to every release in between, i.e. 12.10>13.04>13.10>14.04 LTS or do a clean install. LTS releases on the other hand do upgrade to the next LTS via the update manager (you get the option). So, 12.04 LTS>14.04 LTS in one click.

LTS releases are designed for stability, servers and production machines that are on a lot and need to be reliable, and for users who don't want or need to upgrade to every possible newest release; they just want their machine to work. 

I stick to LTS releases and occasionally install an interim on a spare partition for a plaything and to have a look. Good luck with it, whatever you decide.

---

