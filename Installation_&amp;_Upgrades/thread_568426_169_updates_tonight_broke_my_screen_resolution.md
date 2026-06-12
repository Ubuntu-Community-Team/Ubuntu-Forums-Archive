---
title: "169 updates tonight broke my screen resolution"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by martynp on 2007-10-05
Hello Everyone,

Tonights 169 updates installed fine until I rebooted and got a message saying Ubuntu was running in Low Graphics mode. The screen resolution has been set at 640x480 and there are no other options to select in the Screens & Graphics module. I have selected my Nvidia 6 series driver but still have no other resolutions to choose from.

I am sure this has happened before but I cannot find a fix on the forums.

Could someone kindly help?

Thanks

---

### Post by Pumalite on 2007-10-05
Have you tried:
nvidia-settings

---

### Post by martynp on 2007-10-05
It appears to be a problem with the linux-restricted-modules:

[http://ubuntuforums.org/showthread.php?t=568361](http://ubuntuforums.org/showthread.php?t=568361)

---

### Post by ryno519 on 2007-10-05
> **martynp said:**
> It appears to be a problem with the linux-restricted-modules:

[http://ubuntuforums.org/showthread.php?t=568361](http://ubuntuforums.org/showthread.php?t=568361)

Yes, it is. The restricted modules package for the -13 kernel is being held back. You will have to wait until it's ready before you can install it. On the up side, you can still use the old kernel and everything will run perfectly fine.

---

### Post by martynp on 2007-10-05
Tried selecting the old kernel at the grub but still get the same problem.....

Am i missing something?

Thanks

---

### Post by ryno519 on 2007-10-05
> **martynp said:**
> Tried selecting the old kernel at the grub but still get the same problem.....

Am i missing something?

Thanks

Hmmmm. Might have been one of the xorg updates that gave you that problem. YOU might have to wait for the -13 kernel. Sorry. :)

---

### Post by LavianoTS386 on 2007-10-05
> **martynp said:**
> Tried selecting the old kernel at the grub but still get the same problem.....

Am i missing something?

Thanks

When you get back into xwindows, go to the restricted drivers and select the ones you want.

---

### Post by ladydeth666 on 2007-10-05
Im having the same problem, downloaded updates about 2hrs ago....and havent had video since then.....Im running a MSI Nvidia 8600GTS.  For some reason the low-graphics mode isnt working (I can ctl-alt-del and it will reboot ---but everything is black to me, including the ctrl-alt-F1 - F6)

I tried running the -12 kernel with no luck also.  Did the dist-upgrade and it removed the linux-restricted module.  Now rebooting to see if nvidia-glx-new will fix it....

And back at the low graphics mode.  Vesa and Nvidia drivers not working.....

:(

Will someone post when the new restricted module is put into the repo?  Im having to run it command-line single user mode.

Thanks for any help!

---

### Post by ladydeth666 on 2007-10-05
I can boot the -12 kernel now, after using the config that pops up at boot......basically my xorg.conf looks like this now:

Section "Device"
    Identifier     "Failsafe Device"
    Boardname         "vesa"
    BusID          "PCI:5:0.0"
    Driver          "nv"
    Screen  0
EndSection

Now why does it say boardname vesa? And why the Failsafe Device?  It was always Nvidia Corp before, and never showed a BusID.

I chose the nv driver for various cards like GeForce and Quadro (not going to nvidia, but from the dropdown above the list of manufacturers) and I set it to 640x480.  When it booted, its no longer using the restricted driver (like it was when I first installed Gutsy, when Fiesty wasnt) and the resolution is 1280x1024.

Now to remember how to have it use the .12 kernel at reboot instead of .13 :)

---

### Post by LavianoTS386 on 2007-10-06
^ You updated the Kernel which means you have to reload the restricted modules (your video drivers) again. Normally this wouldn't be a problem if the restricted drivers weren't being held back, like they are

---

### Post by Cannaregio on 2007-10-06
Had same problem with a Geforce 6200 after the heavy update and new generic kernel.

Now the restricted drivers have been released, and you can have your resiolutiion back again.
Unfortunately it seems that the login screen keeps the old  (poor) resolution at start.
Trying to fix this right now. Seems to be a frequent problem, googling around :-)

Found a solution, see the following thread [http://ubuntuforums.org/showpost.php?p=3484653&postcount=15]("http://ubuntuforums.org/showpost.php?p=3484653&postcount=15")

---

