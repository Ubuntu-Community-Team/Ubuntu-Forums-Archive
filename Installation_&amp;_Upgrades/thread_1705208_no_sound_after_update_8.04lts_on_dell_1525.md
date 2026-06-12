---
title: "no sound after update 8.04lts on dell 1525"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by allan.w.macdonald on 2011-03-11
I am using 8.04LTS on a Dell 1525.

A recent automatic update resulted in no sound after reboot.

This very annoying failure has occurred in the past.  Previously, when this happened, I would do something like the following (from root)

```

cd /lib/modules/2.6.24-29-generic/ubuntu/sound/alsa-driver/pci/hda
mv snd-hda-intel.ko.REPLACEDBYhsfmodem snd-hda-intel.ko
cd /lib/modules/2.6.24-29-generic/updates
rm snd-hda-intel.ko
rm snd-hda-codec.ko
depmod -a
update-initramfs -u
reboot

```

I put this in a script and ran it with sudo.

Unfortunately, this would not work because, in the latest ```
/lib/modules/2.6.24-29-generic/
``` directory, there ***is no*** ubuntu directory!

I think this fix came from the following page:
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade).  Unfortunately, this page no longer has anything on it!  What the heck?

I don't know what to do!  I have no sound!  Please help!

Thanks in advance.

Allan

---

### Post by mörgæs on 2011-03-12
If you manage to get it working, you will still only have one month of support left for 8.04. Wasn't it better to try a clean install of 10.04 or 10.10?

---

### Post by allan.w.macdonald on 2011-03-12
> If you manage to get it working, you will still only have one month of support left for 8.04. 

I understand that.  I've been waiting until the last minute to upgrade to 10.04LTS.  I am skeptical that these kinds of issues will go away after this upgrade.

If my system can't remain stable with this version, imagine what might happen if I upgrade to 10.04LTS?

Perhaps if I can get this issue solved, my upgrade to the new OS release will be the next step.  I'd rather not try to upgrade the system while it is broken.  I'd rather at least try to get it error free before proceeding.

> Wasn't it better to try a clean install of 10.04 or 10.10? 

I never ever did a "clean install" on this system before.  This system was purchased from Dell with 8.04LTS pre-installed.  I am not sure if a clean install will result in loss of the special Dell repositories for this system.  I am a bit fuzzy how this repository stuff works anyway and if I did a clean install, I'm afraid I'd lose some of that special Dell flavour.

---

### Post by mörgæs on 2011-03-12
If you want to be on the safe side, you can boot a live CD and see how the machine behaves. If it works well, you can install 10.04 or 10.10 next to the existing 8.04, so nothing is lost.

---

### Post by allan.w.macdonald on 2011-03-13
mörgæs,

Is this going to help me with my current problem?  Do you know how I can fix my sound issue?

My question remains - how can I get the sound fixed on *this* system?  Does anybody know why the sound was killed after this kernal update?

Maybe I can revert back to the previous kernel.  Can anybody tell me how to do that?

I still want my system to work now, in its current configuration.  Any help in this area would be greatly appreciated.

---

### Post by allan.w.macdonald on 2011-03-20
Hey, everybody,

Not sure what happened, but a recent automatic update, which included kernel updates, fixed all my problems.  The missing directories under ```
/lib/modules/2.6.24-29-generic
``` are all now back in place.  I now have sound and wi-fi again and my computer is back to normal.  Wonders never cease!

Many thanks to whoever it was out there who fixed this!!!

Cheers,

Allan

---

