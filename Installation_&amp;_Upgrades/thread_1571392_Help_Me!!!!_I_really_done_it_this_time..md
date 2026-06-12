---
title: "Help Me!!!! I really done it this time."
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by BrianXP123 on 2010-09-09
So uh...I installed Ubuntu with wubi.exe so I can dual-boot it. But then I wanted to install a third OS, Kubuntu, for middle school stuff. So I did it with a Live CD. But then, it ruined the boot. I need to go to the Windows Loader...whatever to use Windows Vista and Ubuntu. Plus I don't like KDE that much. So I just simply deleted the partition of Kubuntu to uninstalled it. But that made it worse. It just opens something related to "grub rescue". It's a good thing I still have my Live CD or else I can't reinstalled it. So, I got my 2 other OS back but it's annoying to boot with the loadermabob. It took me 2 days to figure out how to...well you know. Do any of you guys know how to uninstall Kubuntu? I'm really desperate here!!! Thanks. :)

Can you give instructions fit for a 12 year old? Please?

---

### Post by bryanfblareunion on 2010-09-09
I would boot into a live cd, manage partitions, make sure that one is already deleted. Sorry if that's not any help :(

---

### Post by bcbc on 2010-09-09
To replace the bootloader - you can use lilo from a live CD (or just use a windows repair disc - "bootrec.exe /fixmbr" for vista).

For lilo:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
This works similar to the windows boot loader (boots partition marked with boot flag). You can ignore the errors you get when you install lilo - as these refer to using it to boot linux.

This will boot windows directly, and you'll still have the option to boot Ubuntu through wubi.

Then you should be able to reformat and reuse the Kubuntu partition from Windows. That's about it to 'uninstall'.

---

