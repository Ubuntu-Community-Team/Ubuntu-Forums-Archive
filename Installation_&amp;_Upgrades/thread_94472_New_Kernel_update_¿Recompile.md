---
title: "New Kernel update ¿Recompile?"
date: 2005-11-24
forum: Installation &amp; Upgrades
---

### Post by feralert on 2005-11-24
Hi people,

A couple of weeks ago i recompiled my kernel to my liking, today i apt-get updated and seems there are updates for the 'Linux kernel image', so if i apply that update, do i have to recompile again? And if so, can i use the same config file or do i need to make all the configuration process again?


Thanks for all possible anwsers.

---

### Post by kairu0 on 2005-11-24
A few weeks ago, you compiled your own kernel. Now, you just downloaded a different compiled kernel.

If you want to use a customized kernel, don't download the updated linux-image because it will just be run in place of the kernel that you compiled.

---

### Post by feralert on 2005-11-24
I think i didnt express myself properly, what i did was recompile the default breezy kernel, so now that there is an update for it is when i dont know if i should download the new revision of it and recompile it or what.

---

### Post by Xian on 2005-11-24
[QUOTE=feralert]I think i didnt express myself properly, what i did was recompile the default breezy kernel, so now that there is an update for it is when i dont know if i should download the new revision of it and recompile it or what.[/QUOTE]
If you download the latest linux-image kernel it will be added to the list of kernels that you can boot from in the grub menu. There is no "update" for your custom kernel but simply an upgrade for a previously existing linux-image installation on your system. The only reason (and this would depend upon what fixes were included) to do another custom recompile would be if the linux-source package version was bumped.

---

