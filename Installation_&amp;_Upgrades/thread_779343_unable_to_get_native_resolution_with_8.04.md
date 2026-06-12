---
title: "unable to get native resolution with 8.04"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by GaussianMonk on 2008-05-02
I just upgraded to Kubuntu Hardy and I haven't been able to get my native resolution(1680 x 1050) working. Video card is Radeon Mobility x1400; I downloaded the latest ATI driver, activated it in the restricted drivers menu, and I have Catalyst manager installed, but nothing lets me go past 1400 x 1050. 
Any suggestions?

---

### Post by AteZ on 2008-05-19
first x windows would not start and i fixed it with a xorg.conf copied from a knoppix cd.
then
i could not get past 1024x768 and i needed native resolution on my acer extensa 5120 of 1280x800
when i opened a terminal and entered the following command:

sudo aticonfig --initial -f

and rebooted

it worked for me:)

i found the solution in this thread:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

