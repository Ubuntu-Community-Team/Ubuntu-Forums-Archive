---
title: "Athlon XP 2600+"
date: 2005-02-15
forum: Installation &amp; Upgrades
---

### Post by Jesterace on 2005-02-15
I'm tweaking my install of ubuntu and I'm not too sure which kernel i should pick. Should I grab a k7, i686, or stick with the i386? I've noted that the K7 kernel's description i've read athlon/duron so I'm just a little bit unsure which kernel is right for my system.

---

### Post by ubuntu_fan on 2005-02-15
[QUOTE=Jesterace]I'm tweaking my install of ubuntu and I'm not too sure which kernel i should pick. Should I grab a k7, i686, or stick with the i386? I've noted that the K7 kernel's description i've read athlon/duron so I'm just a little bit unsure which kernel is right for my system.[/QUOTE]

Any of them will work,  but the k7 will be optimised for your chip.

a.

---

### Post by Rancoras on 2005-02-15
Yup, the k7 works very well with AthlonXP.

---

### Post by morphodone on 2005-02-15
i would also like to install the k7 kernel but i get this error

The following packages have unmet dependencies:
  linux-k7: Depends: linux-restricted-modules-k7 but it is not going to be installed
E: Broken packages


what to do?

thanks

---

### Post by Rancoras on 2005-02-15
[QUOTE=morphodone]i would also like to install the k7 kernel but i get this error

The following packages have unmet dependencies:
  linux-k7: Depends: linux-restricted-modules-k7 but it is not going to be installed
E: Broken packages


what to do?

thanks[/QUOTE]

Are you running Hoary?  If so, that package may be in flux right now.

---

### Post by Xian on 2005-02-15
[QUOTE=morphodone]The following packages have unmet dependencies:
  linux-k7: Depends: linux-restricted-modules-k7 but it is not going to be installed
E: Broken packages[/QUOTE]
That most likely has to do with today's kernel security upgrade. 
Just wait unit the missing modules are made available and then you can use the newer kernel.

Ref: [Kernel Upgrade Issue](http://ubuntuforums.org/showthread.php?t=15563)

---

### Post by morphodone on 2005-02-16
i'm running warty
i'll just try to install the kernel in a week or so
maybe the issue will be fixed by then

thanks

---

### Post by Xian on 2005-02-16
[QUOTE=morphodone]i'm running warty
i'll just try to install the kernel in a week or so
maybe the issue will be fixed by then[/QUOTE]
The updated linux-restricted-modules are in the repo now. You can safely upgrade.

---

### Post by morphodone on 2005-02-16
[QUOTE=Xian]The updated linux-restricted-modules are in the repo now. You can safely upgrade.[/QUOTE]

thanks, just booted into k7 kernel

---

