---
title: "Acronis replaced GRUB on mbr"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by ashrack on 2006-06-05
On windows I installed ACRONIS TRUE IMAGE. And without my knowledge it also installed ACRONIS BOOT LOADER.

How do I revert back to GRUB being the first thing to boot and not ACORNIS??

---

### Post by gitarzysta on 2006-06-05
Normally there's an unistall feature in Acronis software.
Have you tried it? (I'm not talking about Control Panel uninstall but about boot loader uninstall to go back to the old condition)

By the way: Acronis TI doesn't install anything without your knowledge. You must have positively answered one question too many :cool:

---

### Post by lcg on 2006-06-05
[QUOTE=ashrack]On windows I installed ACRONIS TRUE IMAGE. And without my knowledge it also installed ACRONIS BOOT LOADER.

How do I revert back to GRUB being the first thing to boot and not ACORNIS??[/QUOTE]
The answer is in the [wiki]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub"). I suggest you use a live CD (whether it's an Ubuntu live CD or something else shouldn't really matter).

HTH,
Lars

---

### Post by ghost60 on 2006-07-12
> **ashrack said:**
> On windows I installed ACRONIS TRUE IMAGE. And without my knowledge it also installed ACRONIS BOOT LOADER.

How do I revert back to GRUB being the first thing to boot and not ACORNIS??

I just ran into a similar situation except mine was backwards; I already had Acronis installed w/boot loader and when installed Ubuntu, Grub became the boot loader. This is fine because the rescue boot cd can be used start Acronis in an emergency if Windows cannot be started. FYI, from what I've been able to tell, you can't uninstall the Acronis boot loader once activated, unless you uninstall the whole program (I guess that will uninstall the bootloader, I didn't want to uninstall it just to find out ;) )

---

