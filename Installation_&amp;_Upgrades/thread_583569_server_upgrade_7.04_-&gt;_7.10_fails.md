---
title: "server upgrade 7.04 -&gt; 7.10 fails"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by jpgeerets on 2007-10-20
hi smart people.

yesterday i did a server update to 7.10.

half-way upgrade fails.
i made a reboot.
system is running, but it is terrible slow (very busy with other things...?) and it generates a lot of error messages during boot.
messeges:
> 
[122612.589990] device-mapper: ioctl: error adding target to table
[122612.590280] device-mapper: table: 254:2: linear: dm-linear: Device lookup failed
[122612.590315] device-mapper: ioctl: error adding target to table


someone any idea what i have to do next?
perhaps the only thing is a clean, new install, but i hope someone can give some advice.

thanks in advance!

Jean-Paul

---

### Post by ipper on 2007-10-25
I experienced the same bug and came across this link [https://wiki.ubuntu.com/Evms](https://wiki.ubuntu.com/Evms) that might be helpful to you.

---

### Post by jpgeerets on 2007-10-25
hi ipper,

tnx for your comment.
i guess this will be the problem.
but, i dont have the option to change this at this moment.
the root disk will be mount as readonly.....
any idea how to solve this?
perhaps boot with live-cd?
i hope to hear....

tnx!

JP

---

