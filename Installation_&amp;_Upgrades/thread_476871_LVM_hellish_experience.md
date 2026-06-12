---
title: "LVM hellish experience"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by back.off on 2007-06-17
hi,

Ok with a pure CLI based install CD setting up LVM takes seconds.

Then comes Ubuntu shitty LVM text based editor. First off why on earth Alternate CD doesn't offer the option for CLI installation??? Second when I set up LVs it takes, no kidding, goddamn 5 minutes for each LV.

But the most aggravating thing yet is if you wanna install root (meaning /) on LVM the stupid idiot Alternate CD won't let you continue 'cause complains that / is not defined. And there's not option to set/format the LV's at that stage, something completely baffling.


This Alternate CD should be filed as HUGEbug. I mean why on earth would someone offer a dumbed down rubbish GUI version ?? Incomprehensible.

So far the only work around I've found is to keep an temporary partition for / and hopefully after everything is install create an LV for / and copy and paste from the other one. Of course modifying fstab accordingly.

My conclusion, Alternate CD sux big time as it made me waste a week and almost got me fired.

Anyone with / in an LV? If you have to manage to set it this way could you share what method did you use?

Regarding the initrd image, is there a program for that? I know other distros have a program, or script to create the initrd.

bye

](*,)](*,)](*,)](*,)](*,)](*,)](*,)](*,)

---

