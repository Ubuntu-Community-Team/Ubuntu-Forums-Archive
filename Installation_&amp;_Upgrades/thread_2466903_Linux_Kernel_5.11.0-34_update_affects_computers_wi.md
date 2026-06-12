---
title: "Linux Kernel 5.11.0-34 update affects computers with NVidia."
date: 2021-09-09
forum: Installation &amp; Upgrades
---

### Post by MAFoElffen on 2021-09-09
Yesterday there was a Kernel Update for 5.11.0-34. It doesn't seem to  want to play well with NVidia drivers, touchpads, keyboards, etc. My  main desktop (with NVidia) is one of these also. Reinstalling the 3rd  party NVidia driver with this Kernel does not seem to bring it back.

I'm sure they will have this sorted out soon. (Hopefully)

#### Instructions to boot and be temporarily Normal ####

At BIOS Post, start hitting the left-shift key, so that the Grub Menu Displays...

When it comes up, press <E> key to edit the Grub Boot line. Use  the down arrow until you get to the line that start's with "linux"...

Use the right arrow, until the cursor is where it says "quiet splash".  Delete "quiet". Arrow right of "splash" and add "nomodeset"... 

Press <Cntrl><X> to boot... It should boot normally.

##### Instructions from there #####

You could update/edit your Grub default file, to add nomodeset as a kernel boot parameter, until this gets sorted out (remembering to updaet-grub to pick up that change), select an earlier kernel to boot from each time you boot, or for the time being, change to using the Nouveau driver. 

To do that- At the Desktop,  "Activities", type "Software & Updates"... Select it. "Additional  Drivers Tab" > Nouveau Driver...

For instruction on editing the Grub Default file, check post #1 of my Graphics Resolution sticky in my Signature line.

---

### Post by monkeybrain20122 on 2021-09-09
Can you just boot into the previous kernel and remove the new one? FYI it doesn't have problem just with Nvidia, I experienced touchpad problem (cannot move horizontally) with an old intel machine, just booted into old kernel, delete the new one and don't upgrade kernel (or you can pin it, but I prefer to leave it as is, so I would just upgrade when it got fixed) and that's it.

---

### Post by MAFoElffen on 2021-09-09
I did say you could boot into an earlier Kernel as an "OR", didn't I?

Yes, "you" could delete that Kernel... Or install a mainline Kernel. Both are other options.

But explaining that to new user's, well... LOL. You know. (Keep it simple.)

*** And for me--- Booting from an older kernel doesn't work for me...I think it is also related to:
 linux-generic-hwe-20.04  version (5.11.0.34.36~20.04.13)

Probably, because then there is a mismatch of that with Kernel(?)

So with that installed, the older Kernels do not work for me...

That package also affects additional hardware, besides Video... This, to me, makes me suspect that the new Kernel is not the culprit, but the HWE package for that kernel is...

---

