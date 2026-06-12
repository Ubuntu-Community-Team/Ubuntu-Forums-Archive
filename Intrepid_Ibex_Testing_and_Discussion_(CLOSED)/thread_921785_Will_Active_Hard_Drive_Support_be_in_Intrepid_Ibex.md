---
title: "Will Active Hard Drive Support be in Intrepid Ibex?"
date: 2008-09-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by thenetduck on 2008-09-16
Hi
I use an IBM ThinkPad and something that is important to me is how my hard drive is handled. Both power, noise levels, load/unload times and having things like Active Hard Drive Protection. Does anyone know if these things are going to be included/updated by default in Intrepid? I really wish IBM would free/open source their drivers for this. (bummer) Anyway, thanks a bunch!

The Net Duck

---

### Post by forger on 2008-09-16
Are you looking for these ?

> **hdaps-utils** - HDAPS (IBM Hard Drive Active Protection System) utilities
**hdapsd** - HDAPS daemon for IBM/Lenovo ThinkPads


The package names are in bold, they are in Ubuntu repositories. But I don't really think they would use it by default, since they seem to be only used with IBM/Lenovo laptops(?)

---

### Post by olskar on 2008-09-16
is this related?

[http://ubuntuforums.org/showthread.php?t=920930](http://ubuntuforums.org/showthread.php?t=920930)

---

### Post by Whiffle on 2008-09-16
Last I checked the utilities are there, but kernel support isn't.  There are drivers out there to support it, and I have had it working.  The problem isn't so much the actual parking of the drives, its everything else that has to be working just right to support that.  I doubt we'll see it in ubuntu anytime soon.

---

### Post by Whiffle on 2008-09-16
> **olskar said:**
> is this related?

[http://ubuntuforums.org/showthread.php?t=920930](http://ubuntuforums.org/showthread.php?t=920930)

Not related.  What the OP is looking for is hdaps, the hard drive protection thing that parks the heads when you drop the laptop.

---

### Post by forger on 2008-09-16
hdapsd:
> 
Description: HDAPS daemon for IBM/Lenovo ThinkPads
 This is a disk protection userspace daemon. It monitors the acceleration
 values through the HDAPS interface and automatically initiates disk head
 parking if a fall or sliding of the laptop is detected.
 .
 This daemon won't work out of the box on a stock Debian kernel, as it
 needs a patch, which is not in the default Debian kernels. Please read
 README.Debian for the source of that patch.
 .
[B] It is recommended that you use this daemon with the hdaps module provided
 by tp-smapi rather the one in the kernel, as this will save you a bit
 power and will work on a wider range of ThinkPads.[/B]


So logically there's a module tp-smapi:
```
$ dpkg -S smapi
linux-image-2.6.27-3-generic: /lib/modules/2.6.27-3-generic/kernel/ubuntu/misc/tp_smapi.ko
```

There's also a package named: tp-smapi-source
> Description: Source for the tp_smapi kernel modules
 The tp_smapi kernel module exposes some features of the ThinkPad
 hardware/firmware via a sysfs interface. Currently, the main implemented
 functionality is control of battery charging and extended battery status.
 The underlying hardware interfaces are SMAPI and direct access to the
 embedded controller
 .
 This package also brings the source for an improved version of HDAPS
 which should work on newer ThinkPads too (the stock kernel version does
 not)
Homepage: [http://tpctl.sourceforge.net/](http://tpctl.sourceforge.net/)


P.S. I am using Intrepid alpha 5 :)

---

### Post by Whiffle on 2008-09-16
Well fancy that.  I wonder if they built it with the HDAPS=1 option, otherwise it doesn't build the hdaps module, only the tp-smapi module.  Doesn't look like it would be too hard to add in later though.

---

### Post by thenetduck on 2008-09-16
> **forger said:**
> hdapsd:


So logically there's a module tp-smapi:
```
$ dpkg -S smapi
linux-image-2.6.27-3-generic: /lib/modules/2.6.27-3-generic/kernel/ubuntu/misc/tp_smapi.ko
```

There's also a package named: tp-smapi-source



P.S. I am using Intrepid alpha 5 :)

so how do I add this module to my kernel in ubuntu? In gentoo I would just re-compile my kernel with the proper module enabled? can I just use the code you provided? dpkg stuff ? 

Thanks ! sorry, I know this might not be a support thread section.

The Net Duck

Please note, you need to unpack the hdaps_ec  not hdaps :)

---

### Post by forger on 2008-09-17
hm.. looks like it has the latest module version:
> $ modinfo tp_smapi
filename:       /lib/modules/2.6.27-3-generic/kernel/ubuntu/misc/tp_smapi.ko
license:        GPL
version:        0.37
description:    ThinkPad SMAPI Support
author:         Shem Multinymous
srcversion:     7774CFE98BA09B3E60EA564
depends:        thinkpad_ec
vermagic:       2.6.27-3-generic SMP mod_unload modversions 
parm:           debug:Debug level (0=off, 1=on) (int)

I think the good way to load extra modules it to add them in /etc/modules file:
```
sudo echo "tp_smapi" >> /etc/modules
```

and you simply reboot :)

---

### Post by Whiffle on 2008-09-17
> **forger said:**
> hm.. looks like it has the latest module version:


I think the good way to load extra modules it to add them in /etc/modules file:
```
sudo echo "tp_smapi" >> /etc/modules
```

and you simply reboot :)

That will not enable HDAPS, the hdaps module must be loaded as well, it is not the tp_smapi module.  

[http://www.thinkwiki.org/wiki/Tp_smapi](http://www.thinkwiki.org/wiki/Tp_smapi)

---

### Post by thenetduck on 2008-09-18
don't add tp_smapi ... you need to add "hdaps_ec" thats the ubuntu way to do it :) just so you know , 

 the net duck

---

### Post by InfinityCircuit on 2008-09-18
[http://article.gmane.org/gmane.linux.drivers.hdaps.devel/1324](http://article.gmane.org/gmane.linux.drivers.hdaps.devel/1324)

It's not mainlined yet--there are still ongoing discussions with the ide developers.  The actual hard disk parking has nothing to do with the version of the hdaps driver you use. (well, you have to use a new version, but the hdaps code does not affect the physical parking).

---

### Post by thenetduck on 2008-09-18
Ok now i'm a little bit confused, 

Which one should I be using for my machine? There are a couple possiblities I can see. Either hdaps, hdaps_ec or tp_smapi ????  or both? All?

Oh dear...

the net duck

---

### Post by InfinityCircuit on 2008-09-18
Active Hard Drive Support = Hard disk parking = you need libata patches, see the post I made above.

If you just want HDAPS, to play with your computer like a lightsaber, then it should work out of the box on anything post-Feisty (I believe).

---

