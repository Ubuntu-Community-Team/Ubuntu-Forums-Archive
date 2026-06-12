---
title: "Format windows affect bootloader"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by abdusamed on 2010-11-11
I have grub installed which boots both my ubuntu and windows which are in seperate partition. I'm about to format my windows, will it affect anything? Like though my ubuntu will not be formated nor the bootloder but shouldn't the windows bootloader overwrite somethign and make it default? Thus making ubuntu impossible to boot?

Also I have Burg installed[graphical grub] :)

---

### Post by P4man on 2010-11-11
you should be able to format the **partition** on which windows is installed without problems to grub, burg or linux. Run ```
sudo update-grub
``` afterwards to remove the option from grub menu.

---

### Post by abdusamed on 2010-11-12
> **P4man said:**
> you should be able to format the **partition** on which windows is installed without problems to grub, burg or linux. Run ```
sudo update-grub
``` afterwards to remove the option from grub menu.
 
Shouldn't the windows boot-loader [one comes with windows7] become default after it installs????? Thus only windows boots not ubuntu!?

---

### Post by Elfy on 2010-11-12
> **abdusamed said:**
> Shouldn't the windows boot-loader [one comes with windows7] become default after it installs????? Thus only windows boots not ubuntu!?

Yes it will - but that's not what you asked originally. Reinstalling windows is not the same as formatting the windows partition.

You will need to reinstall grub.

---

### Post by Rubi1200 on 2010-11-12
Just to help you along a little bit:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

