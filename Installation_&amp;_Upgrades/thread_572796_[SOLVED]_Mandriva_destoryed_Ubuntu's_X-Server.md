---
title: "[SOLVED] Mandriva destoryed Ubuntu's X-Server"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by JawsThemeSwimming428 on 2007-10-10
I just tried resizing my Ubuntu (Feisty) install with the Mandriva 2008 LiveCD Partitioning tool that is found in the Installation program. I think it is DiskDrake. I resized Ubuntu from 36 to 25GB and installed Mandriva on the other 10GB. When I rebooted the only options that came up on the Mandriva boot screen were Mandriva and Mandriva in safe mode. I found the Boot Manager utility and tried to add my Ubuntu installation to the boot menu and it seemed to work. However once I rebooted and selected Ubuntu it failed to start the GUI. I got my systems terminal after I viewed an error about x's configuration. How do I get my GUI back?

---

### Post by taurus on 2007-10-10
Try to reconfigure it again with

```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by JawsThemeSwimming428 on 2007-10-11
I did that and I still could not get it working. The output of the error is as follows;

(==) Using config file: "/etc/X11/xorg.conf"
FATAL: Could not load /lib/modules/2.6.22.9-desktop586-1mdv/modules.dep: No such file or directory.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module.
(EE) NVIDIA(0): ***Aborting***
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found


What should I do now?

---

### Post by gaussian on 2007-10-11
> **JawsThemeSwimming428 said:**
> I did that and I still could not get it working. The output of the error is as follows;

(==) Using config file: "/etc/X11/xorg.conf"
FATAL: Could not load /lib/modules/2.6.22.9-desktop586-1mdv/modules.dep: No such file or directory.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module.
(EE) NVIDIA(0): ***Aborting***
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found


What should I do now?


Somethign really strange is going on here: it seems that you are running something Mandriva mixed with Ubuntu. This is the giveaway in the error message: /lib/modules/2.6.22.9-desktop586-1mdv/modules.dep

The mdv-part there means Mandriva. My guess is that you have only one /boot partition and you have Mandriva and Ubuntu kernels and initrd's mixed up there and you are actually trying to run Ubuntu with a Mandriva kernel.

What to do: a short term solution could be to identify a ubuntu kernel (not vmlinuz (sp?) which is a symlink to a kernel) and modify the grub.lst entry for ubuntu boot to that. Hope this helps.

---

### Post by AdamWill on 2007-10-12
Yup. You're trying to boot Ubuntu with the Mandriva kernel. That's not going to work right :)

If you have trouble getting your menu.lst right, post it here and I'm sure we can help.

Sorry that Mandriva does not detect Ubuntu and add it to the bootloader - I know this is a bit antisocial. This was on the planned feature list for 2008 but was cut due to lack of time. :(

---

### Post by JawsThemeSwimming428 on 2007-10-12
I am not sure how to do that. Ubuntu doesn't boot to a GUI. Mandriva runs fine, can you tell me how to repair the menu.lst from inside Mandriva? I'm not very familiar with this so if you could be as detailed as possible that would be great! Thanks.

---

### Post by louieb on 2007-10-12
Use the configfile option and have Mand... Grub program load Ubuntu's menu.lst  Scroll down this page it explains how to use a configfile. Absolutely the most trouble free way to dual boot 2 Linux distros. [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

