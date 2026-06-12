---
title: "Higher resolution on bootscreen?"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by _sAm_ on 2009-10-01
Is it possible to get higher resolution on the new boot screen(the wallpaper you see before the login window appears)?

It doesn't look good on 1920x1200 screen as it is.

---

### Post by pawhtiobo on 2009-10-01
Hi :)

You have to edit the boot menu.lst and change the ex:. VGA=791 to the resolution you want:

Screen   640x480     800x600     1024x768     1280x1024     1600x1200  
Colors    --------------------------- ------------------------------------------- 
 256     | 769         771          773            775              796  
 32,768 | 784         787           790           793              797  
 65,536 | 785         788           791           794              798  
 16.8M  | 786        789           792           795              799

See also this:

[http://ubuntuforums.org/showthread.php?t=834606](http://ubuntuforums.org/showthread.php?t=834606)

[http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers)

see ya...

---

### Post by cyberkilla on 2009-10-01
I don't understand why they need one for every resolution.

Why can't they make a small Ubuntu logo and centre it in the middle of the screen:P Sure, it might look a little smaller on massive screens, but that is they people buy massive screens - to get more space!:guitar:

---

### Post by gexi on 2009-10-01
will this happen automatically with the the final release, or will non-technical users just have to live with the pixelated x-splash?

just because i think it’s one of those ‹first-impression› things, that could make the non-technical windows-user turn his\her back on ubuntu once again, saying »windows is better« ;)

(of course, this would only be a relevant point if one actually wants popularity. and i think a more popular linux desktop is a better supported linux desktop...)

---

### Post by VMC on 2009-10-01
I'm not sure if your talking about the grub2 screen or the login screen after grub releass. If grub screen then edit "/etc/default/grub" and edit out the # from GRUB_GFXMODE=640x480 and change to desired resolution. Use vbe to test:
```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
```

---

### Post by danwood76 on 2009-10-01
X-splash is run in X and so it should run in the default resolution X runs in.

On both my laptop and desktop this is true and the splash looks nice, much better than the previous Usplash.

---

### Post by gexi on 2009-10-01
> **danwood76 said:**
> X-splash is run in X and so it should run in the default resolution X runs in.

hmm, yeah. maybe it’s just a virtualbox-thing... guestadditions not loaded soon enough or something. actually i can‘t wait to try the beta “for real” as soon as it‘s out (if i manage to find a cdr :) ) ! 9.10 seems to be great so far.

---

### Post by _sAm_ on 2009-10-02
The size is correct, but the resolution on the image is to low so it looks less nice. 

They have changed the "wallpaper" now but this is how it used to look like(so you can understand what picture I am talking about). 

I am not using virtualbox.

---

### Post by frustphil on 2009-10-02
It's even more ugly in my case. From xplash to gdm, my resolution is 800x600(or 600x800, not sure), then a layered explashes(with the smallest one on top) before my wallpaper shows up. Btw, my native resolution is 1024x768. :(

---

### Post by danwood76 on 2009-10-02
Do you both use proprietary drivers?

On both my machines I use the open source ATI drivers which work at the correct resolutions from the point X is loaded.
There might be an issue with the ATI/NV drivers not quite mode settings correctly until after GDM?

---

### Post by tsger on 2009-10-02
> **danwood76 said:**
> Do you both use proprietary drivers?

On both my machines I use the open source ATI drivers which work at the correct resolutions from the point X is loaded.
There might be an issue with the ATI/NV drivers not quite mode settings correctly until after GDM?


danwood,  what is the exact name of the open source ATI driver which you are using?

---

### Post by danwood76 on 2009-10-02
Probably radeon (not radeonhd), its the default for both my X1950 and X200M.

I may be fooling myself into believing its the correct resolution, my laptop I can't test but my desktop screen I can give a poke and it tells me the resolution so I will do that when I get home.

---

### Post by tyk on 2009-10-03
Hi,
I don't know if this is the correct place to post this but I got this problem from the 9.10 beta release. When booting from liveCD the resolution was perfect at 1366x768. I installed on a test partition and when I rebooted the resolution all over went down to 1024x768. By all over I mean, the splash and the GDM/Desktop AND the other installs of 9.04 I have on separate partitions!!
[On the 9.10 beta install I don't have a higher resolution to change to.. while the older 9.04 installs give me the option of 1366x768 and I can change it but it does take some time to rearrange clocks and calendars and conkies etc...]
Since the kernel/install is chosen from GRUB 1.97 which installed with the 9.10 test, I feel the solution might be to change the default resolution of GRUB itself. I will try this and revert.
Cheers.

---

