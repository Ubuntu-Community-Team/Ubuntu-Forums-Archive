---
title: "Should I choose the ATI HD5750 or 4670 for lucid?"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Col-1023 on 2010-04-13
I'll be getting a new pc in the next month, the specs will be something like,

athlon ii x4-630
gigabyte MA770tx-UD3
g.skil-nt 4 gb ddr3 1333
seagate 1.5 tb
amazetech ati hd4670
antec 200
corsair-vx 450

I want to stick with AMD parts.

I was thinking of getting the ati hd5570 card, but read all sorts of horror stories about it not being stable under lucid, so will the hd5750 be stable under lucid, or should I stick with the hd4670?

Thanks in advance.

---

### Post by aviramof on 2010-04-13
lucid itself is unstable at the moment and to be hones i wouldn't let any Os to tell me what hardware to buy and considering the fact fact that ATI HD5750 is much better then 4670 i would buy it now and find solutions later.

---

### Post by psyke83 on 2010-04-13
I just did a search and found no "horror stories" for the HD5750 - only two threads from users who had configuration issues (which is unsurprising when using a development release). Go ahead and get the newer card. 

IMHO, the real advice you need is this:  if you do jump on the testing bandwagon, please take some time to read the release notes and sticky threads on this forum. Also, be smart - install the proprietary driver the "official" way - via the Hardware Drivers application. If you install the fglrx driver manually, your system **will**  experience  issues (two that come to mind: library conflicts when updating the Mesa packages, and driver failures when the kernel is upgraded to a new minor ABI due to the fact that the fglrx kernel module will not get automatically rebuilt).

---

### Post by canter690 on 2010-04-13
I have a 5750 running on 10.04.  Had initial problems with Alpha1 but the ATI drivers have been added to the repo's now and they seem stable enough. ATI doesn't support KMS and plymouth looks ugly, I haven't pushed the 3D capability but compiz looks ok and video plays ok as well.  That said I wish I had bought and Nvidia card instead as there is better support for Nvidia.

---

### Post by Col-1023 on 2010-04-13
Thanks everyone for your replies.

I should clarify some things.

1 - When I get my machine I will install whatever 10.04 iso is out, it will either be the final release, or the version before that.

2 - I intend to use the official drivers from the repos as I want a stable system.

3 - I posted in this thread because it involves lucid which while not quite ready now, will be in a month when I will have my pc.

4 - I had read a couple threads about the hd5750 being unstable, and I was worried that the driver issues would not be fixed until 10.10, as I believe ubuntu gets only 1 driver release per ubuntu version.

So it seams that the hd5750 will be official supported in 10.04, so I will consider getting that card.

---

### Post by dxxvi on 2010-04-13
Just my curiosity, why do you need such powerful video cards in Linux?

---

### Post by Col-1023 on 2010-04-13
I'm a fairly casual gamer, so I may not need such a powerful card, but native linux games are becomming more graphics intensive with every release, and you can play many windows games under wine, and then there are 3d artists who use blender and may need a powerful gpu.

---

### Post by forcecore on 2010-04-13
> **Col-1023 said:**
> I'm a fairly casual gamer, so I may not need such a powerful card, but native linux games are becomming more graphics intensive with every release, and you can play many windows games under wine, and then there are 3d artists who use blender and may need a powerful gpu.

Like first powerful engine Unigine that works fine only with closed drivers only.

[http://unigine.com/download/](http://unigine.com/download/)

---

### Post by realzippy on 2010-04-13
> **dxxvi said:**
> Just my curiosity, why do you need such powerful video cards in Linux?


There is no need to,but:

Compiz with 16x FSAA,8xAF looks really fine....  ;-).
If you want all that linux eyecandy at its max,you
simply have no choice,forget ATI.
No,I am not paid by NVIDIA,but the performance of the ATI driver
is terrible compared to NVIDIA.

---

### Post by Ellipsis on 2010-04-13
I have a 4670 (1GB, Asus one with a massive heat sink attached) I now kinda wish I bought a 5750 since it would have only cost around $50 more at then a 4670. Yet, the 4670 should be able to handle most Linux games at decent graphics (even some newer Windows titles... just not BF:BC2... can't get that to run above 60FPS unless it is set to low and even then there are issues with massive drops in frame rate during a big explosion). 

Anyway if you got the money buy the 5750... it will stay relevant much longer.

As for the Nvidia, bah Nvidia has dropped all pretense at supporting their open-source driver (probably a good thing since it sucked to begin with) and is instead promoting using the VESA driver and downloading the proprietary driver: [http://www.phoronix.com/scan.php?page=article&item=nvidia_kills_nv&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_kills_nv&num=1)

So they aren't in my good books. ATI although having a poorer quality proprietary driver are doing something to support the open-source driver. Moreover, they are actually trying to (slowly) improve the closed source driver's quality.

---

### Post by Reiger on 2010-04-13
Just go for the HD5750 it's a better card than 4670 and the fglrx driver promises support for Open GL 4 for the 5xxx series, too. A few releases from Lucid on (two or three I guess) the Radeon DRM stack should have sufficiently matured to get decent 2D and 3D (Gallium) performance from the open source driver, as well.

---

### Post by rajeev1204 on 2010-04-13
> **realzippy said:**
> but the performance of the ATI driver
is terrible compared to NVIDIA.

Proof? This is just FUD and will give out wrong information to new users .Fglrx isnt as bad as it was or as its made out to be.

---

### Post by rajeev1204 on 2010-04-13
> **realzippy said:**
> There is no need to,but:

Compiz with 16x FSAA,8xAF looks really fine....  ;-).
If you want all that linux eyecandy at its max,you
simply have no choice,forget ATI.
No,I am not paid by NVIDIA,but the performance of the ATI driver
is terrible compared to NVIDIA.

The performance is just fine with the newer drivers.Iam happily using an ATI 4850 and gaming with it.

---

### Post by rajeev1204 on 2010-04-13
> **forcecore said:**
> Like first powerful engine Unigine that works fine only with closed drivers only.

[http://unigine.com/download/](http://unigine.com/download/)

Linux gaming seems to be around the corner then. :) We need more of these companies in addition to id software, although,with zenimax taking over iam not surewhere that is headed.

---

### Post by realzippy on 2010-04-14
> **rajeev1204 said:**
> The performance is just fine with the newer drivers.Iam happily using an ATI 4850 and gaming with it.


Ok,run the desktop cube.On 1 desktop run e.g. quakelive,TV on the second,
some firefox internet flash content on the third,a DVD on the fourth.
All this with FSAA and AF (does this work with ATI?),then rotate the cube (in front of a huge animated skydome backround),and resize the TV window....what happens?
Doubt that it runs "fine".On my friends 4870 it stumbles terribly...

BTW,rajeev,you said it yourself one week ago:

"*since window management **is really bad** with fglrx*"


...or did the fglrx driver improve that much last week?   ;-)

from:

[http://ubuntuforums.org/showthread.php?p=8934718#post8934718](http://ubuntuforums.org/showthread.php?p=8934718#post8934718)

---

### Post by Evzen on 2010-04-15
Take HD5750. Since this monday, Lucid Lynx works just fine with this card (tested on Sapphire HD5750 1GB). Basic displaying is supported in open-source driver (auto-detected) and 3D support can be enabled by installing proprietary fglrx driver (it can be installed by two or three in mouse clicks in GUI)

---

### Post by rajeev1204 on 2010-04-16
> **realzippy said:**
> Ok,run the desktop cube.On 1 desktop run e.g. quakelive,TV on the second,
some firefox internet flash content on the third,a DVD on the fourth.
All this with FSAA and AF (does this work with ATI?),then rotate the cube (in front of a huge animated skydome backround),and resize the TV window....what happens?
Doubt that it runs "fine".On my friends 4870 it stumbles terribly...

BTW,rajeev,you said it yourself one week ago:

"*since window management **is really bad** with fglrx*"


...or did the fglrx driver improve that much last week?   ;-)

from:

[http://ubuntuforums.org/showthread.php?p=8934718#post8934718](http://ubuntuforums.org/showthread.php?p=8934718#post8934718)

Hehe, you searching my threads it seems :D

But if you see, its gaming i talked about , desktop effects suck still i know.

---

