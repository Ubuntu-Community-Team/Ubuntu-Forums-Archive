---
title: "Problems with instalation"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by philipthehat on 2010-08-30
Hi 

I am fairly new to ubuntu and linux so would appreciate some straightforward advice please on my install problem.  

I recently pulled together a "recycled" Pc for my son based on an asus k8vse motherboard with a HD is from a different machine.   The HD is an older IDE drive so I have set it as master with CD drive as slave on the secondary IDE socket on the motherboard.  The bios can see it and all seems fine from that side of things.  

When I try to boot the install of 10.04 from the optical drive the following happens....

- cd spins up and I get the couple of lines of text at the top of the screen introducing the linux instal
- get the logos at the bottom of the screen, suggesting instalation has commenced.
- after about 10 seconds I get a flashing cursor in the top left corner, the cd stops spinning and thats it...  it all freezes

I have also tried with ubuntu 9 cd - same problem but this time I get a load of code running down the screen before it freezes with the flashing cursor.   Im pretty sure both the cds are fine since I have used them on this old laptop - no problemo

Some similar threads suggest that there may be some issue with some of the cards on the board??? graphics cards??   SOrry if this is something that has already been posted.

I would appreciate some ideas / pointers about what I do next please.  Like I say I have a pretty basic understanding!!



Cheers

Phil

---

### Post by oldfred on 2010-08-31
As the CD starts can you press f6 for parameters or f4 for minimal video?

Also Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

If it is video:
Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa

---

