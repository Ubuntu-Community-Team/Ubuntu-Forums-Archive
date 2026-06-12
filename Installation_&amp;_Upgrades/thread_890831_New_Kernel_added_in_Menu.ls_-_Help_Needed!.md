---
title: "New Kernel added in Menu.ls - Help Needed!"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by kpk on 2008-08-15
Hi,
[Me=New2Ubuntu]:confused:
I have a dualboot and I noticed that until today my Boot Menu had the following items:

> title Ubuntu 7.10, kernel 2.6.22-15-generic
title Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
title Ubuntu 7.10, memtest86+
title Other operating systems:
title Microsoft Windows XP Professional

But earlier this morning, I ran an update process which crashed due to an abrupt system restart. However, since I had trouble logging in using the default session, I switched over to the GNOME session (not sure about the name though) and when I restarted the system I was able to see additional items being added to the Boot Menu (as shown below):

> title Ubuntu 7.10, kernel 2.6.22-15-generic
title Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
title Ubuntu 7.10, kernel 2.6.22-14-generic
title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
title Ubuntu 7.10, memtest86+
title Other operating systems:
title Microsoft Windows XP Professional

Could someone throw some light on this? Is this normal? Should I edit the Menu.ls file and delete the additional items or is it better if it is left as is? Also, I did not understand the concept of logging in using a different session that is available in the login page. Apologies if my questions sound weird!

---

### Post by Stemp on 2008-08-15
It's nothing menu.lst show all the available kernels. Just in case version -15 doesn't work you still can switch back to version -14.
These entries are automatically added when a new kernel is installed.

---

### Post by kpk on 2008-08-16
> **Stemp said:**
> It's nothing menu.lst show all the available kernels. Just in case version -15 doesn't work you still can switch back to version -14.
These entries are automatically added when a new kernel is installed.

Thanks Stemp!
Will it cause a problem if I remove version-14 from Menu.lst?

---

### Post by cdtech on 2008-08-16
Removing a kernel version from the menu.lst will not harm your system, as long as you can boot from the latest kernel. Your kernel images are not removed from your system by modifying the menu.lst.

If you want to permanently remove a kernel images (to save space within your /boot partition), it's recommended to remove using the Synaptic Package Manager.

Hope this helps......

---

### Post by grndrush on 2008-08-16
Er, you DO notice, right, that -14 replaced -15, and NOT the other wat around (at least per yours screens). I'd be darned slow removing the last kernel added to GRUB!

Did you do an upgrade which involved a new kernel, or perhaps one involving a dependency change (shudders) necessitating a new kernel flavor?

---

### Post by kpk on 2008-08-18
> **cdtech said:**
> Removing a kernel version from the menu.lst will not harm your system, as long as you can boot from the latest kernel. Your kernel images are not removed from your system by modifying the menu.lst.

If you want to permanently remove a kernel images (to save space within your /boot partition), it's recommended to remove using the Synaptic Package Manager.

Hope this helps......

Sure... :)
Thanks a bunch!

---

### Post by kpk on 2008-08-18
> **grndrush said:**
> Er, you DO notice, right, that -14 replaced -15, and NOT the other wat around (at least per yours screens). I'd be darned slow removing the last kernel added to GRUB!

Did you do an upgrade which involved a new kernel, or perhaps one involving a dependency change (shudders) necessitating a new kernel flavor?

I think it was created when I was trying to upgrade/update... but I am still confused.. I mean I just upgraded to Hardy and I got a third kernel added to the already existing list of 2!:confused: 

Hope I dont mess around and add another one to that list :(

---

### Post by Stemp on 2008-08-20
> **kpk said:**
> I think it was created when I was trying to upgrade/update... but I am still confused.. I mean I just upgraded to Hardy and I got a third kernel added to the already existing list of 2!:confused: 

Hope I dont mess around and add another one to that list :(

Don't worry, when you upgrade softwares only the last version is kept.
But for the kernels it's different, your 2.6.22-15 kernel could be updated (for security reasons) but the new version (2.6.22-16 or 2.6.24-1) will not delete 2.6.22-15.

---

