---
title: "linux-restricted-modules-2.6.26-2-generic does not contain fglrx"
date: 2008-06-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by eeclark on 2008-06-23
Comparing previous versions of linux-restricted-modules, I noticed that 2.6.26-2-generic does not contain fglrx (or fglrx.ko).

Will future packages of this name contain fglrx?

---

### Post by soccerboy on 2008-06-23
is that an nvidia drivers module?  If so, I read that nvidia drivers will be included as soon as the kernel development on this version finishes and only bug fixes remain that will need to be done downstream.

---

### Post by eeclark on 2008-06-23
> **soccerboy said:**
> is that an nvidia drivers module?  If so, I read that nvidia drivers will be included as soon as the kernel development on this version finishes and only bug fixes remain that will need to be done downstream.

Nope. ATI
But most likely that is an appropriate answer as well.
Thanks

---

### Post by dinxter on 2008-06-23
in past experience the restricted module package is only upgraded when all of the restricted modules are packaged and ready, including both ati and nvidia. it may be a bug or a restructuring of the method of providing the ati packages but its certainly a change from the usual way of doing things. it does look like its been left out deliberately though to my eyes.

- just to add, the 2.6.26-1 kernel restricted package seems to miss fglrx.ko too, which makes it seem like a deliberate decision rather than an accident

---

### Post by soccerboy on 2008-06-23
I though ATI open sourced their drivers.  If that is the case, I would expect them to be included already, if not soon, like vesa.

---

### Post by dinxter on 2008-06-23
ati, no doubt thanks to amd's new influence, are trying to release specs to strengthen the open source implementation, and indeed actual open sourcing may come more to the fore as they move forward. but they have many legal commitments to third parties contributions in past graphics cards and in the short term future ones, the fglrx proprietary driver will be around for a while :(

---

### Post by soccerboy on 2008-06-23
Good to know.  I am shopping for a new graphics card and was considering ati because of open source but I may go with nVidia since people seem to have better experience with those.

---

### Post by dinxter on 2008-06-23
i would add (to be unbiased!) that nvidia show no signs last time i looked of moving towards open source, unlike ati's shaky inclinations, though nvidia's proprietary drivers seem better than ati's at the moment, having just moved from long term ati user to nvidia in the last 2 months

---

### Post by soccerboy on 2008-06-23
i would love to use open source but I don't want to fiddle extensively especially since the people using it are not going to exactly be skilled in linux.

---

### Post by soccerboy on 2008-06-23
check [http://ubuntuforums.org/showthread.php?t=834321](http://ubuntuforums.org/showthread.php?t=834321) to see if you think the hardware I selected is compatible with ubuntu?

---

### Post by superm1 on 2008-06-30
fglrx is moving into its own package (not in LRM).  Also, it's not compatible with 2.6.26 yet.

---

### Post by tseliot on 2008-06-30
The NVIDIA driver will be available soon. We're working on it.

---

### Post by Nullack on 2008-06-30
tseliot I previously contacted you RE a concern I had, and I'd like to explain it again here.

NVIDIA uses a hack to workaround some x limitations where the driver does not report the correct refresh rate as part of providing dynamic twin view functionality.

I am concerned that other applications such as Compiz are detecting the wrong refresh rate as a result. I have personally set Compiz to a manual refresh rate of 85hz, not 50hz as indicated. My CRT does refresh at 85hz.

Also previously on Hardy your hardy proposed change for the later nvidia driver resulted in bootup messages about loading the nvidia driver more than once.

---

### Post by eeclark on 2008-06-30
> **superm1 said:**
> fglrx is moving into its own package (not in LRM).  Also, it's not compatible with 2.6.26 yet.

What is the package called?

---

### Post by psyke83 on 2008-06-30
> **eeclark said:**
> What is the package called?

Umm, the package doesn't exist yet, so at this point it doesn't matter what it's going to be called. You shouldn't expect restricted drivers to work with the development version - especially so early in development - full stop.

---

