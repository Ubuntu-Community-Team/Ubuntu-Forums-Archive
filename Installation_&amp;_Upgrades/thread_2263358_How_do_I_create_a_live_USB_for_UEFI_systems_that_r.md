---
title: "How do I create a live USB for UEFI systems that reads and saves changes?"
date: 2015-01-31
forum: Installation &amp; Upgrades
---

### Post by sdgiffin on 2015-01-31
I have a 16 GB USB stick which runs a live boot of Ubuntu 14.10 with antivirus software, and a few other tools I installed which (obviously) needs to be kept up to date as I use it to boot and clean infected Windows machines.

To make it, I used **[FONT=courier new]usb-creator-gtk[/FONT]**, a fresh ISO for Utopic x64 Desktop (downloaded from [The Official Site]("http://www.ubuntu.com/download/desktop")), and a 4 GB persistence file which **[FONT=courier new]usb-creator-gtk[/FONT]** creates automatically when the option is selected. Nothing fancy, nor anything complicated.

When this is used on (old school) BIOS systems, it's all there. I can update the antivirus software and the changes are saved in the user persistence file (**[FONT=courier new]casper-rw[/FONT]** I believe?) However, when used to boot UEFI systems, none of that is there and any changes made are not saved.

It's like I have two environments on this stick: The UEFI version which is the same as the default ISO, **DOESN'T** save changes and is R-O, and the BIOS version which has my tweaks and custom apps, **DOES** save changes and is R-W.

So - how I do get the UEFI version of the live environment to save any changes made or even better, how can I get the UEFI and BIOS versions of the live environment to share the same environment?

---

### Post by sudodus on 2015-01-31
You have to enter the boot option **persistent** also in the grub configuration, that is activated in UEFI mode.

Do it 

- either during booting (add it to the end of the linux line in the grub sub-menu, press E)

- or by editing the file **grub.cfg** in order to get persistence every time without entering that sub-menu

---

### Post by sudodus on 2015-01-31
See this link near the end of post #1, the chapter **Enjoy**
[URL="http://ubuntuforums.org/showthread.php?t=2259682"]
One pendrive for all PC (Intel/AMD) computers[/URL]

---

### Post by ajgreeny on 2015-01-31
See [http://ubuntuforums.org/showthread.php?t=2165496](http://ubuntuforums.org/showthread.php?t=2165496) for another info thread with same details.

---

