---
title: "Not enough space on /boot, New rcS.d ???"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by Fifilein on 2007-05-09
Hi,

i do want to upgrade to 7.04, but i do have one question in advance, and one problem.

i heared that there is some kind of new "startup" system, so that the whole rcS.d stuff is obsolete; is this true? because i am using a fully encrypted system and i do have the startup scripts in this directory... if the upgrade would mess with that i will have a problem.

i also wanted to start the upgrade, but i got a problem; i do not have enought space on /boot and i can't make enough space (partition to small). i do have a rescure system on my machine (hda5 is rescue /) where i would have enough space.
could i temporarely move the /boot to the "rescue /" (including kernel images and grub, would i need to do anything else then cp?), do the upgrade and change it back afterwards? or would this completely mess up the "rescue /" (i don't know if a /boot has to be something special)

thanks a lot for your help,

kr
christian

---

### Post by jpeddicord on 2007-05-10
The new init system is not 100% in place yet, so the rcS.d scripts are not yet completely obsolete. Even once Ubuntu hits the point that they are "obsolete," there will still be backwards compatibility for it. Your upgrade shouldn't have too many problems.

As for /boot, a safer solution would be to uninstall the older kernels that you never boot. You can uninstall these in Synaptic, and removing the old ones will save you pain from trying to copy and rescue /boot to another drive.

Jacob
UAResolved

---

### Post by Fifilein on 2007-05-13
> **jacobmp92 said:**
> The new init system is not 100% in place yet, so the rcS.d scripts are not yet completely obsolete. Even once Ubuntu hits the point that they are "obsolete," there will still be backwards compatibility for it. Your upgrade shouldn't have too many problems.

As for /boot, a safer solution would be to uninstall the older kernels that you never boot. You can uninstall these in Synaptic, and removing the old ones will save you pain from trying to copy and rescue /boot to another drive.

Jacob
UAResolved

Hallo Jacob,

sorry for my reply in answering, i was concentrating on the problems of my desktop machine which i am also moving to ubuntu... actually i am only getting frusted with the migration of outlook2whatever.

good to know that the bootup script is still in place, so no worries here...

concerning /boot; the only thing i can do, i can delete ALL kernels (and i am not sure if even this will help; but this might be a risk for the next bootup, won't it be?

kr
christian

---

