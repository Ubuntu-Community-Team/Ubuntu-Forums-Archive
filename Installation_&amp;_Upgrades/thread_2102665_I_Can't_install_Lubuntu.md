---
title: "I Can't install Lubuntu"
date: 2013-01-07
forum: Installation &amp; Upgrades
---

### Post by Migomaxpop on 2013-01-07
Hi there :D , I have i problem! I can't install the Lubuntu 12.10 on my pc.
Here is what i do:
1-enter the CD.
2-restart the computer.
3-it's successfully boot from the CD.
4-i select install Lubuntu.
5-it give me black screen with a listener dash flashing.
6-then lubuntu loading like . . . .
7-some code i can't remember looks like:
                      Lubuntu
                                   . . . . XXXXXXXXX
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
8-another black screen.
9-the cursor finally shows up.
10-then the problem it back to the loading screen, like a loop from step number 6 to number 9.
and the screen is doing a sound every time its switching to another screen in the loop, what Frickin me out.

My PC:intel Celeron 2.6GHz,
225MB RAM, SiS 32bit.

Any idea how to install it.
thanx!

---

### Post by cariboo on 2013-01-07
It would help if you could tell us what the error message you are getting says, as I suspect you may be having a hardware problems.

---

### Post by Rex Bouwense on 2013-01-07
According to 
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)
you need more RAM than you have installed to properly install Lubuntu.  As the web site suggests try the alternate install.

---

### Post by Migomaxpop on 2013-01-07
> **cariboo907 said:**
> It would help if you could tell us what the error message you are getting says, as I suspect you may be having a hardware problems.

First time:
```
ask 0x100 SAct 0x0 Serr oxo action ox6
[   95.197655] ata3.00: faild commnd: SET FEATURES
[   95.197675] ata3.00: cmd ef/05:fe:00:00:00/00:00:00:00:00/40 tag 0
[   95.197655]        :res 51/04:fe:00:00:00:00/00:00:00:00:00/40 Emsak 0x1 (device error)
[   95.197655] ata3.00: ata3.00 statuse: { DRDY ERR }
[   95.197655] ata3.00 error: { ABRT }

```
secoud time and forever:
```

. . . .*Start Mount network filesystem
[   95.197655] ata3.00: faild commnd: SET FEATURES
[   95.197675] ata3.00: cmd ef/05:fe:00:00:00/00:00:00:00:00/40 tag 0
[   95.197655]        :res 51/04:fe:00:00:00:00/00:00:00:00:00/40 Emsak 0x1 (device error)
[   95.197655] ata3.00: ata3.00 statuse: { DRDY ERR }
[   95.197655] ata3.00 error: { ABRT }

```
is it bad :(

---

### Post by Migomaxpop on 2013-01-07
> **Rex Bouwense said:**
> According to 
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)
you need more RAM than you have installed to properly install Lubuntu.  As the web site suggests try the alternate install.

i was running ubuntu 12.04 for ones!!!
but now none of ubuntu or any ubuntu family want to setup,
if alternate install is to download an iso image and burn it, so i think thats exactly what i did

---

### Post by Migomaxpop on 2013-01-08
Please i still need Help

---

### Post by Migomaxpop on 2013-01-08
[B][COLOR="DarkRed"]What is the best ubuntu for my PC:intel Celeron 2.6GHz,
 225MB RAM, SiS 32bit. ???[/COLOR][/B]

---

### Post by forkandles on 2013-01-08
With your current hardware and memory, you really need to look at something like these OSs:

[http://www.slitaz.org/en/](http://www.slitaz.org/en/)

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

The alternative is to beg, steal or borrow somebody's old Windows machine which has become surplus to requirements and which has more memory and a Pentium P4 (or more recent CPU).
There should be plenty of such PCs and laptops generally available after the splurge on brand new machinery at Christmas. Just ask around.

Alternatively add more memory to your PC, if possible.

---

### Post by Rex Bouwense on 2013-01-08
> **Migomaxpop said:**
> [B][COLOR="DarkRed"]What is the best ubuntu for my PC:intel Celeron 2.6GHz,
 225MB RAM, SiS 32bit. ???[/COLOR][/B]
Did you go to the web site that I quoted in my previous posting?  That explains what you need to do.  If that doesn't work then post back.

---

### Post by Migomaxpop on 2013-01-11
> **Rex Bouwense said:**
> Did you go to the web site that I quoted in my previous posting?  That explains what you need to do.  If that doesn't work then post back.

sure i did, it say that i need minimum 300mb of ram.

---

### Post by Migomaxpop on 2013-01-11
> **forkandles said:**
> With your current hardware and memory, you really need to look at something like these OSs:

[http://www.slitaz.org/en/](http://www.slitaz.org/en/)

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

The alternative is to beg, steal or borrow somebody's old Windows machine which has become surplus to requirements and which has more memory and a Pentium P4 (or more recent CPU).
There should be plenty of such PCs and laptops generally available after the splurge on brand new machinery at Christmas. Just ask around.

Alternatively add more memory to your PC, if possible.
that is interesting, i hate the way Ms Windows is getting attack by a simple virus like autorun.inf and that's why i don't want it again.

---

### Post by Migomaxpop on 2013-01-11
i finally add more memory another 256 now i have 516 and still have the same problem.

---

### Post by dino99 on 2013-01-11
sadly you will have hard time due to your sis chipset (not or badly supported by recent kernels), and too low ram quantity.

that said, you might download Jaunty i386, which i suppose will be able to use your hardware as it is, or try some other OS proposed in a previous post.

[http://old-releases.ubuntu.com/releases/9.04/](http://old-releases.ubuntu.com/releases/9.04/)

---

