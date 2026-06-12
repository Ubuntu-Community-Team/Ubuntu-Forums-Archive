---
title: "best way to upgrade 8.04-&gt;10.04"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by martvefun on 2010-04-30
Hello,

I've a computer with ubuntu 8.04 and I'd like to upgrade it to the next LTS.

In the update-manager, I don't have the option to upgrade to the next version.

I know I can do that with a terminal or with a alternate cd but I don't know exactly how (usually the informations are to go from 9.10->10.04)

Also important question :
how to minimize the risks ?
As it's a computer share with all my family, I don't want to ruin the windows xp installed on another partition (I'm the only one using ubuntu). I'm a bit afraid to go to grub2 for example 

thank you

---

### Post by kansasnoob on 2010-04-30
[http://www.ubuntu.com/getubuntu/upgrading#Upgrade%20from%208.04%20LTS%20to%2010.04%20LTS](http://www.ubuntu.com/getubuntu/upgrading#Upgrade%20from%208.04%20LTS%20to%2010.04%20LTS)

---

### Post by martvefun on 2010-04-30
thank you
except the recommended solution doesn't work as I said and it doesn't said about the command line

what about the risks ?

---

### Post by dino99 on 2010-04-30
> **martvefun said:**
> thank you
except the recommended solution doesn't work as I said and it doesn't said about the command line

what about the risks ?

well, there are some differences :
8.04 have : grub1, hal
10.04 replace by: grub2, udev

depend on system, sometimes video and/or sound work fine in a case and have some issue in the other case. (often have issues with ati, intel, broadcom, ...)

so it depend of the free space on hdd: can you install both ? or prefer to wait let say 1 month till the main lucid issues are fixed ?

---

### Post by martvefun on 2010-05-01
no unfortenatly I don't have enought free space to install both
maybe I'll wait

---

### Post by briandu on 2010-05-01
if you boot from livecd and everything works then it should be OK.

Remember the livecd is not anything special other than what you would have installed. Sure it has more options, because of all the hardware out there and needs to detect most of it, but it will probably be fine. Unless, of course, you have some zany hardware - then the fun can start; OTOH id you have bog standard hardware then there is no reason to have a prob.


But always back up first!!

BTW - how much disk space do you have - you can install in 1GB

---

### Post by martvefun on 2010-05-01
> **briandu said:**
> BTW - how much disk space do you have - you can install in 1GB

hum seen like this, ok I've enough :P

It's just that it's not so bad if I lose my ubuntu, I don't use it so often (reason I was too lazy to upgrade every 6 months) and everything important is backed up.
It's more if I lose the access to the other OS I know some persons who won't be happy...
The risk is more with grub2 then. If I install the new ubuntu on another partition, I'll have to use the new version of grub so the problem is the same.
But that's right I can test with the live cd at first

---

