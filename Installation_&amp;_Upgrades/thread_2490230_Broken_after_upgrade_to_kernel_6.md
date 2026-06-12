---
title: "Broken after upgrade to kernel 6"
date: 2023-08-27
forum: Installation &amp; Upgrades
---

### Post by evadza on 2023-08-27
I have been trying for weeks to get my machine (Dell optiplex 3010) to boot up in the graphical desktop mode like it used to.

First was waiting over 20 hours for boot up, then seeing Loading AppAmour no time limit. So I turn that off. Now I get a terminal login.

So how Do I get the graphical display/desk top back?

---

### Post by ian-weisser on 2023-08-27
First thing to try: Reboot. At GRUB, select an older 5.x kernel to boot into.

---

### Post by evadza on 2023-08-28
Yes I have tried that and get the same result. No desk top. Just a terminal login.

---

### Post by ubfan1 on 2023-08-28
Try the sudo apt upgrade again, and not if any packages are held back.  Sometimes phasing will hold back a package that is needed by the video driver rebuild scripts, the new video driver doesn't get rebuilt, and black screen (happened to me once with Nvidia).  Maybe a desktop component got held back. You can force things, but waiting a bit may also allow the phasing to release the held back file.

---

### Post by ajgreeny on 2023-08-28
Some users when the 6.2.0-26 kernel was released found that most of their GUI packages were removed meaning there was no longer a full, working Desktop Environment left in the OS resulting in a boot to command line.

It might be possible to see what is missing if you run command ```
sudo apt install --reinstall ubuntu-desktop
``` ànd take careful note of what packages are to be installed. Run that command anyway as it will do no harm.

If you use another flavour of Ubuntu with a different DE make the appropriate change to that command, eg reinstall xubuntu-desktop package.

---

