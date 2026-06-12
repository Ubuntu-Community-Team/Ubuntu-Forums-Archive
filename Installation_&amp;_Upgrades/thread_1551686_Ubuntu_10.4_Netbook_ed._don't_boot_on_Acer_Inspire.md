---
title: "Ubuntu 10.4 Netbook ed. don't boot on Acer InspireOne AO751h"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by Zlika on 2010-08-12
Hi everybody,

When I try to boot the Ubuntu 10.4 Netbook Edition on my Acer Inspire One AO751h, it doesn't work most of the time : black screen with a white blinking cursor at the upper left corner.
However, from time to time (~1 out of 5 tries), it works and I was able to install the distro on the hard drive disk.
But I have now exactly the same problem when booting from the HDD.

I've updated the BIOS to the latest version (3212) but the problem still remains.
This problem is specific to Ubuntu, because I can boot other live CD like Ultimate Boot CD or the Acer restore DVD without any problem.

When the boot is succesfull, I have watched the Linux logs but there is nothing related to the previous unsuccessfull tries.

Does anyone know what is the problem ?
Thank you

Thomas

---

### Post by earthpigg on 2010-08-12
> **Zlika said:**
> 
This problem is specific to Ubuntu, because I can boot other live CD like Ultimate Boot CD or the Acer restore DVD without any problem.


it sounds like the problem is specific to *the copy of ubuntu .iso you have downloaded and burned*. in fact, it sounds like it was either a corrupt download or a corrupt burn.

verify md5sums of the iso after downloading? verify the integrity of the cd?

or: download again (via torrent this time, so you can skip the md5 check) and burn again at slowest speed.

---

### Post by Zlika on 2010-08-13
Thank you for your answer.
The MD5 was correct.
Following your advice I burned a new CD at the lowest speed.
And it's working now ! I can't understand how a bad CD can install a "nearly working" OS, but it's working, so thank you very much for your help.

Thomas

Edit:
In fact it was another problem related to the wifi driver: we have the choice between an open source and a proprietary driver. The open source driver is buggy and makes the computer hang most of the time during startup. The solution is to use the proprietary driver.

---

