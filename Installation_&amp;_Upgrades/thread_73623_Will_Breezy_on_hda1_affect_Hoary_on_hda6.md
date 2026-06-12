---
title: "Will Breezy on hda1 affect Hoary on hda6?"
date: 2005-10-09
forum: Installation &amp; Upgrades
---

### Post by thumper on 2005-10-09
I currently have Hoary on hda6 (33G) Swap on hda5 (1.1G) and Windows XP on hda1 (40G).

I want to do a fresh install on Breezy over the Windows XP to get:
   hda1 20G / ext3
   hda7 20G /home ext3

Can I still use hda5 as swap with out affecting Hoary?

Will Hoary still be in the GRUB boot menu?  What about if I mark hda6 as bootable?  Will I have to edit /boot/grub/menu.lst to add in Hoary?

I want to be able to mount Hoary to copy across my home data.

---

### Post by darkmatter on 2005-10-09
[QUOTE=thumper]I currently have Hoary on hda6 (33G) Swap on hda5 (1.1G) and Windows XP on hda1 (40G).

I want to do a fresh install on Breezy over the Windows XP to get:
   hda1 20G / ext3
   hda7 20G /home ext3

Can I still use hda5 as swap with out affecting Hoary?

Will Hoary still be in the GRUB boot menu?  What about if I mark hda6 as bootable?  Will I have to edit /boot/grub/menu.lst to add in Hoary?

I want to be able to mount Hoary to copy across my home data.[/QUOTE]

thumper, you shouldn't have a problem with installing over Windows, I've done so in the past.

And to answer you question on hda5. Yes. Breezy should autodetect the swap on install. It is perfectly fine to share a swap partition between Linux installs, as only one OS will be using the swap at any given time.

You do not need to mark Hoary as bootable. Breezy will autodetect and add Hoary to its menu.lst like magic. If, in the off chance, the autodetect of Hoary fails, it can easily by added to menu.lst manually.

Good Luck! If anything does not go according to plan, please post back

---

### Post by az on 2005-10-09
I use hibernation on a desktop.  What that is is instead of shutting down, I click on hibernate and it dumps the contens of all my system's memory onto the swap, then shuts down.  When it boots up again, it detects the presence of the former session on the swap partition and loads it up from there.  You boot in,like, twenty seconds.

In this case, if I were to hibernate my hda6 ubuntu install and then boot into my hda1 install and it would use the swap, all my unsaved data from the hibernation would get clobbered.

But otherwise, you can share swapsapce with other installs.

---

### Post by thumper on 2005-10-10
Well, post install and things seem to be OK.

Breezy did, as **darkmatter** suggested, recognize Hoary.

Now how to copy my Kontact info...

---

