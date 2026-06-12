---
title: "Dell M1330 &amp; Lexar 16GB - No Desktop"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by bpmorris on 2008-07-04
Hi Everyone,

I have just purchased a new Dell M1330 along with a Lexar 16GB Express Card with the intention of dual booting with Hardy Ubuntu installed on the flash drive. The install appeared to work successfully and I can continue to boot into Vista ok however when I boot into Ubuntu I get the login screen ok but when I then login I just get a blank brown desktop with no further errors or prompts. I have tried researching this issue myself but without an error to search on I am not sure where to start. I have tried reinstallation 3 times today with the same result. Booting of the live CD works fine too which is the confusing thing! Has anyone seen and possibly resolved this issue themselves??? Anyone have any suggestions on what I can do to troubleshoot or fix this???

Thanks Guys!

Ben

---

### Post by upchucky on 2008-07-04
ubuntu is choking on the video driver, search for xorg.conf  stuff. you need to edit the xorg file for your display, set the modes, search my posts as i have posted an example xorg several times for people as a hint.



the messages for the video in the live cd will work a generic display that is why the cd works. in the messages are generic settings that you can use to get you started.

---

