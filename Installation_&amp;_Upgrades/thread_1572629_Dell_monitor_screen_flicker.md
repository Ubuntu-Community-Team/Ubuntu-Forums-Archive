---
title: "Dell monitor screen flicker"
date: 2010-09-11
forum: Installation &amp; Upgrades
---

### Post by medha6 on 2010-09-11
Hi,

I was on earlier 9.x version of ubuntu with following configuration working perfectly:

IBM ThinkPad T60 with ATI Technologies Inc Radeon Mobility X1400 VGA graphics card (found it from lspci)
With an external Dell 19" monitor attached to it.

I upgraded yesterday to Ubuntu 10.4 LTS and now the Dell monitor screen keeps flickering all the time!

I always work with an external bigger monitor attached to my laptop as working for long hours on the smaller screen of the laptop gives me headache.

The frustrating point is, this setting was working perfectly until I was on Ubuntu 9.x, I upgraded to 10.04 LTS and this has stopped working. :(

Can someone please help me?

Thanks.

---

### Post by medha6 on 2010-09-11
Just FYI. I booted into my earlier kernel 2.6.31.22 and it's working now. Which means that this is probably broken hardware driver issue. Although booting into earlier kernel does spit out some error messages at the boot time.

A permanent fix for this problem by the Ubuntu community will be appreciated.

Thanks.

---

### Post by medha6 on 2010-09-15
Nobody has any solution? I am repenting quite a bit for upgrading to  Ubuntu 10.04, it has wrecked a lot of my originally installed  applications. ](*,)

---

### Post by efflandt on 2010-09-16
Did you try **nomodeset** kernel boot parameter?  By default 10.04 uses kernel mode setting (kms) instead of user space modules, and my old desktop with X1300 and work laptop with Radeon Mobility X1300 do not like kms.  Without **nomodeset** (or **radeon.modeset=0**) the desktop will not suspend/hibernate (video never turns off) or the Dell laptop has frequent video glitches during boot.  But nomodeset fixes both by using the older style modules.

---

### Post by medha6 on 2010-09-16
Yes. I did read about **nomodeset** option on the web when I searched for Ubuntu and monitor problems, but I came across a lot of different links, many of which gave procedures for GRUB-2 and somehow to my surprise, even after upgrade, my laptop doesn't have GRUB-2 on it (there is no /etc/default/grub), and I was not sure how to update the older GRUB file (/boot/grub/menu.lst) by changing the "kopt" lines.

Can you give me a definite link which I can follow? (I just didn't want to take a chance by trying something on my own and then risking to have a completely dysfunctional laptop)!

Thanks for your reply.

---

