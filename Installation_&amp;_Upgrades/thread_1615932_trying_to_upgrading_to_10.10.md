---
title: "trying to upgrading to 10.10"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by tommah04 on 2010-11-07
hey all,

I've had Ubuntu for quite awhile and haven't had any problems upgrading till now.  trying to upgrade from 10.04 to 10.10, it got all the packages just fine but during  the "installing the upgrades" step its stuck at "Installed grub-common" and the terminal says,

"what do you want to do about modified configuration file grub?"

now I've done my fair share of tinkering with my computer so I figured I'd get some input before trying anything and possibly screwing myself by not being able to boot anymore.
any ideas on how to proceed would be great!

thanks!

dual-boot Ubuntu 10.04 amd64/Win7 64-bit

---

### Post by Quackers on 2010-11-07
I don't know what you should do, but I will say that I elected to leave the originals on one of my installations and chose the new ones on another installation. I didn't have any problems. Maybe others can give more specific advice.

---

### Post by tommah04 on 2010-11-07
Thanks for the input ^

sorry for not providing this information, dunno if that changes your input at all, but the choices are

1. install the package maintainer's version
2. Keep the local version currently  installed
3. show the differences between the versions
4. show a side-by-side difference between the versions
5. show a 3-way difference between available versions
6. do a 3-way merge between available versions (experimental)
7. start a new shell to examine the situation

thanks for the help!

---

### Post by oldfred on 2010-11-07
If you do not take the package maintainer version you will not be able to boot until you manually add the new kernel to the boot menu. You would have to use liveCD to edit either menu.lst or chroot into system and add entries to grub2.

Are you using grub legacy or grub2?

The intent is, if you have customized your grub menu to let you keep your customization without overwriting it. I try to remember to back up any system config file that I customize and always take the maintainers version as sometimes the old file as customized does not work. I then can add back my custom settings if I need them, but many times do not need them.

---

### Post by tommah04 on 2010-11-08
so the package maintainer is just the default? and worst case scenerio I have to rebuild my desktop or did I read that wrong?

in any case I installed the package maintainer's version and everything worked out fine.

thanks for your time!

---

