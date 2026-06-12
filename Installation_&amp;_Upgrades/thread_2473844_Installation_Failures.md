---
title: "Installation Failures"
date: 2022-04-15
forum: Installation &amp; Upgrades
---

### Post by bxdobs on 2022-04-15
Been using/installing Ubuntu forever (in VM's) ... spent all day yesterday attempting to install either 20.04.4 or 18.04.6 desktop 64 on a Lenovo P310 (5-year-old machine) with 8G ram and 1T Hd (Lenovo diags give this machine a pass on all critical systems) ... was either getting Code 10 error or Error 5 Failures ... the iso files were installed on both a brand new Kingston 64G stick or a RW DVD ... replaced the HD, the DVD, even an even older no-name brand PC ... erase and install failed in all 10 attempts ... the try ubuntu method with the manually gparted 200M boot partition didn't work either.  

Error 5 suggests there is an issue with the iso image I have downloaded both iso images twice and done a bit comparison they are all the same 
Error 5 also suggests a possible HD failure ... all the HD pass Smart diags and Lenovo Diags

My last attempt on the older machine with 18.04.6, I left running overnight and it has been in text mode endlessly spitting out blk_update_requests

Is there some way to take an installed image from one of my VM's (I have 16.04, 18.04, and 20.04 running in VMWare Worksation 15 Player) and just copy to a blank HD? tt

Or is there another way to install Ubuntu?

---

### Post by tea for one on 2022-04-15
Which software did you use to prepare the Ubuntu installer?

---

### Post by bxdobs on 2022-04-15
Corel burn apparently doesn't do a verification ... not sure why rufus (used to create the USB Stick) also had issues ... Once I burned a DVD with Cyberlink DVD Create (with Verify) the installation finally went all the way.

---

