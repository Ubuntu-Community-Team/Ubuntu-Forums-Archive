---
title: "NVidia on Hoary just won't work for me"
date: 2005-04-21
forum: Installation &amp; Upgrades
---

### Post by ChrisTheGeek on 2005-04-21
Since using Hoary I have been completely unable to get the NVidia drivers installed and working.  My machine is a Dell Inspiron 8100 (fairly old laptop) with a G-Force2 Go card.  The NVidia drivers that were in the Warty repository worked *perfectly* on this machine.  However, I'm now running a fresh install of Hoary and I'm having no luck at all.

The problem I get is that after installing the drivers a blank screen appears during system boot up (about when the gdm would usually load).  No cursor or text is displayed, it's totally blank.  The machine has effectively crashed since I can't get to any terminal (Ctrl+Alt 1-7 does nothing).  The only thing I can do is hard-reset, load via grub into recovery mode and uninstall the driver again.

First I tried to install the drivers as per UbuntuGuide from the repository.  I've also downloaded the very latest drivers from NVidia's website and installed them.  Both approaches have led to the problem above.

I thought initially that it might be a kernel problem (I've installed the 686 kernel) but I've now had this problem with both the 386 and 686 kernels so I don't believe it's due to that.

I've tried everything I know and can't get this to work.  I'm even more bemused since the drivers worked so easily in Warty!  Is there some way I can use the Warty drivers on Hoary (even if I have to recompile them against the new kernel?)

Any help is *very* much appreciated.

---

### Post by squallbsr on 2005-04-21
Is the NVidia kernel module being loaded while booting? (lsmod should show the nvidia module)

I have the NVidia driver working properly on my GeForce FX5200 desktop at home on the preview release of Hoary.

---

### Post by ChrisTheGeek on 2005-04-21
While booting with the driver installed I can't get to a command prompt as described.  However, I don't get any errors during the installation so I can only assume that it's at least attempting to load the NVidia module.

---

