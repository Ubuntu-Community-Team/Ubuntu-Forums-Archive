---
title: "graphics problems transferring hard drives (not xorg-related)"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by Vacri on 2007-09-20
Looking for some help on what to reconfigure here.

Recently I bought a laptop (ibm x30) and was given three more (dell c400) to install for a friend. Both models of laptop are portable/no optical drive lappies.

I've installed ubuntu from USB on the x30 using a netinstall image, and it's absolutely standard from the repositories - I haven't made any modifications at all except to grub to get the boot order correct (taking out the reference to the USB stick).

Now, the c400 laptops will not boot from USB stick or USB optical, and I don't have a PXE environment, so I've installed one of the hard drives on the x30 and installed there, then put the hard drive back in the c400.

The problem I have is a graphics issue outside of X. If you wait for the laptop to boot to gdm, it'll show fine, but the problem is graphics outside of X:
[LIST=1]
[*]The ubuntu progress bar during boot is not shown, just a blank screen. Since it takes a minute or two to boot, and these lappies are going to windows users (windows refused to install on them using methods available), I'd rather not show them a blank screen because it looks like the computer has hung
[*]Changing to a text console (ctrl+alt+f2) shows giant text (dos 40 column style?) and is essentially unusable
[/LIST]

gdm and gnome work fine, look normal, run sweetly for the things I've tried, but outside of X the graphics are haywire.

I did a reconfigure on xorg on a previous test install, and both laptops use the same drivers for X (i810, although the name string is different), so I'm not sure where the problem is. 

Any ideas?

thanks,

- V

---

### Post by dcstar on 2007-09-21
> **Vacri said:**
> Looking for some help on what to reconfigure here.
........
The problem I have is a graphics issue outside of X. If you wait for the laptop to boot to gdm, it'll show fine, but the problem is graphics outside of X:
........
Any ideas?

thanks,

- V

You can set the VGA mode on startup with a "vga=xxx" string in your Grub command line, this might help.

Do a search for details on the various modes.

---

### Post by Vacri on 2007-09-23
Yep, this was the charm. Thanks David, much appreciated.

Table stolen from another linux forum somewhere:

```
Color depth      | 640x480  800x600  1024x768 1280x1024
-----------------+-------------------------------------
256        (8bit)|  769      771       773      775
32000     (15bit)|  784      787       790      793
65000     (16bit)|  785      788       791      794
16.7 Mill.(24bit)|  786      789       792      795
```

Changing from 791 to 773 and doing an update-grub made the machine work correctly.

---

