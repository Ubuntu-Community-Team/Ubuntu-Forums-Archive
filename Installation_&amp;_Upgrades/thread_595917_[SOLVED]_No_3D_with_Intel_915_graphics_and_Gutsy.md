---
title: "[SOLVED] No 3D with Intel 915 graphics and Gutsy"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by mal on 2007-10-29
I am having a lot of trouble getting desktop effects to work following a new install of Gutsy and any help would be appreciated.

I have a Pentium 4 CPU on an Intel 915GAV motherboard with 1Gb of memory.

I had an Albatron GF6600 128M PCI-E video card, but with desktop effects enabled (Compiz Fusion), I get glitches on the screen giving a poor quality display. This remains unresolved ([see my previous post]("http://ubuntuforums.org/showthread.php?t=584776")), so I decided to take it out and try the on-board Intel graphics hardware.

Attempts to configure this using the new "Screens and Graphics" tool failed to produce a combination that works with 3d acceleration,  So I decided to try the LiveCD to see if it could detect and configure the Intel hardware. Sure enough, this worked quite well, with desktop effects enable by default, so I copied the xorg.conf file to my Gutsy partition and rebooted.

Unfortunately, still no 3D acceleration!!!

Why would this work with the LiveCD and not with an installed copy of Gutsy?

I guess I could try another fresh install of Gutsy with the on-board video active, but this is a pain in the butt and should not be necessary.

There seem to be a few other posts with similar problems, but I haven't seen any solutions that worked for me, so it would be great if someone out there can suggest a way forward.

Thanks,

Mal

---

### Post by daengbo on 2007-10-29
When you used "Screens and Graphics," did you identify the driver by the chip, on the second tab? What exactly were the modes offered and which ones did you try? Please elaborate.

---

### Post by mal on 2007-10-29
> **daengbo said:**
> When you used "Screens and Graphics," did you identify the driver by the chip, on the second tab? What exactly were the modes offered and which ones did you try? Please elaborate.

daengbo,

I actually tried various driver selections on the second tab, including the "intel experimental" driver, the i810 driver and I think there was an i915 option.  The LiveCD automatically selects the "intel experimental" driver.

The only modes that were offered were on the first tab related to the screen selection.  Here I have been choosing my LCD monitor (Benq FP71E) and have tried different vertical refresh rates.  I don't recall any other choices.

There have been some posts suggesting that either enabling or disabling xserver-xgl could be a factor.  This is not installed on my machine and I have not yet tried it.

I also tried installing modules i915 and drm, based on another post, but this also did not seem to make any difference.

Thanks for your help.

Mal

---

### Post by daengbo on 2007-10-30
Have you installed 915resolution and worked with that? I think the new Intel driver doesn't require it, but the old one (i810) did, so you may need to  (or may have) change(d) something in the BIOS list of supported resolutions. Try a search on 915resolution and see if some of the advice works for you.

---

### Post by mal on 2007-10-30
> **daengbo said:**
> Have you installed 915resolution and worked with that? I think the new Intel driver doesn't require it, but the old one (i810) did, so you may need to  (or may have) change(d) something in the BIOS list of supported resolutions. Try a search on 915resolution and see if some of the advice works for you.

915resolution is not in the Gutsy repositories.  However, I will do some research on this to see if it could help.

Thanks,

Mal

EDIT: Correction - I have since discovered that 915resolution is in the Gutsy repositories.

---

### Post by mal on 2007-11-01
An update:

I have checked the kernel modules that are loaded on my system and compared this with the modules that are loaded when I run the LiveCD.  The main difference seems to be that the LIveCD loads i915 and drm modules and these are not loaded on my installed system.

With the LiveCD, lsmod includes these lines:

```
i915                   25856  2 
drm                    83348  3 i915
```

When I added these modules to /etc/modules and rebooted, I still could not get 3D acceleration and I got the following lines in lsmod:

```
i915                   25856  0 
drm                    83348  1 i915
```

I assume that this means that these modules are not being used by my installed system.  What does this mean?

The other thing I tried was to load xserver-xgl, but this also failed to give me 3D.

I have not yet tried installing 915resolution and I have not yet resorted to a fresh install.  Perhaps I'll try these options soon.

Mal

---

### Post by mal on 2007-11-04
Another update...

I gave up and re-installed Gutsy with the on-board 915 graphics in operation.  This got desktop effects working.

However, there is a big downside - the system has become extremely slow for certain activities, including: painting the gdm login screen and logging in to the desktop.  It was also painfully slow during the recent update - it got stuck updating scrollkeeper and I eventually had to kill the process.  I had much the same problem trying to install Google Earth.  I eventually killed this after it had been running for about an hour and had only got about 10% through the process!!

I found the much same problem when I reverted to my old Feisty partition, so this is not a new problem with Gutsy.

At this point I am ready to give up on compiz fusion on this machine.  I will go back to my nvidia card and turn off desktop effects.  :(

Mal

---

### Post by mal on 2007-11-05
OK - some information that might be useful to others having problems with Intel graphics with Gutsy:

I increased some bios video memory allocations and the speed problems were fixed.  The actual settings might depend on your motherboard, but it should be pretty easy to figure out.

I also discovered why I could not get 3D graphics working after taking out my nvidia card and falling back to the on-board Intel graphics - I just needed to remove the nvidia-glx-new driver.  Clearly, having this package installed when not using an nvidia card is bad news!!

Hope this helps someone.

Mal

---

### Post by daengbo on 2007-11-05
Glad you worked it out.

---

### Post by hihihi on 2007-11-11
GOOD NEWS!

TRY THIS TO GET BOTH CARDS WITH GLX:

[http://ubuntuforums.org/showthread.php?p=3752404#post3752404](http://ubuntuforums.org/showthread.php?p=3752404#post3752404)

GOOD LUCK

---

