---
title: "Ubuntu 10.04 Freezes few minutes after login"
date: 2010-09-22
forum: Installation &amp; Upgrades
---

### Post by itsingleegfang on 2010-09-22
Hey,

I am a newbie to Ubuntu.. so was facing a problem and hence would great if someone helps me out with it..it goes as

i had previously installed Ubuntu 9.10 (dual booting with Windows XP) whichgave me errors of "Hard Disk Bad Sectors" and then would freeze my PC leaving me with no other option than Re-Booting..[ignoring the error as a BUG) so on advice of other ubuntu users.i tried  Ubuntu10.04.

On installing Ubuntu 10.04 it showing the same problem as that before.(freezing few minutes after the login page) and again dual booted with Windows XP.

i don't suspect a hard ware problem because my Windows XP works perfectly fine with the Same hard ware.

Plz help me out.with this

Thanks

Hard ware specifications
1 GB RAM
160 GB hard disk
3 Ghz Processor

PS:its the 8th time i have installed Ubuntu ..so its really frustrating ..any advice or suggestion would help :D ;)

---

### Post by gnush on 2010-09-22
Have you considered dd'ing the hard drive?

```

dd if=/dev/zero of=/dev/sdX bs=1M

```**BE CAUTIOUS! The command above will erase everything on the hard drive.**
*Replace sdX with the hard drive *you want to dd.

To check what hard drives and partitions you have in use, type the following command.

```
sudo fdisk -l
```I'm not really familiar with bad sectors so I don't know if this method will work. But it might be worth giving it a shot.

---

