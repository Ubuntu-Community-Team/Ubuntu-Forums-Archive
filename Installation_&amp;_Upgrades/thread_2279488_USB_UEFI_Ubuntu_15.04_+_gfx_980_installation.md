---
title: "USB UEFI Ubuntu 15.04 + gfx 980 installation"
date: 2015-05-23
forum: Installation &amp; Upgrades
---

### Post by bamarcus-c on 2015-05-23
Goal: To install Ubuntu 15.04 Desktop edition on PC with Nvidia GTX980 in UEFI mode.
 
Notes:
[LIST=1]
[*]Tested on Ubuntu 14.04.2 Desktop and Server edition. 
[*]Assumes previous knowledge of UEFI booting USB Pendrive with info found [here]("https://help.ubuntu.com/community/Installation/FromUSBStick"). 
[*]See Following references regarding **nomodeset** kernel instruction:
[http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it) 
[/LIST]

Procedure:

[LIST]
[*]Boot into the menu of a Ubuntu 15.04 installation USB pendrive. 
[*]Select "Install Ubuntu" and press 'e' to enter edit mode. You'll be able to edit the boot parameters of the grub bootloader. 
[*]Move  the cursor to end the line starting with "linux /boot/vmlinuz-.." and add  nomodeset to the line. (note: Don't be alarmed if the line wraps to the  next line. A backslash '\' will indicate the line is wrapped ) 
[*]Press F10 to boot and install your system. 
[*]Before  rebooting edit /etc/default/grub and change it to reflect the following  change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

sudo nano /etc/default/grub
```
Change the following line to:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [highlight]nomodeset[/highlight]"
```
and update Grub2:
```

sudo update-grub
```
[/LIST]

I hope this helps someone.

---

### Post by Vladlenin5000 on 2015-05-23
Hi and welcome.

Thank you for this guide. Just a question: Have you installed the recommended nvidia drivers? The *nomodeset *parameter is necessary to have video with those nvidia chips that aren't correctly supported by the open source *nouveau* driver, such as your GFX980. Not a Linux specific issue: [https://forums.geforce.com/default/topic/778461/gfx-980-w-drivers-causes-intermittent-loading-quot-no-signal-quot-issue/?offset=2](https://forums.geforce.com/default/topic/778461/gfx-980-w-drivers-causes-intermittent-loading-quot-no-signal-quot-issue/?offset=2)
The *nomodeset *parameter is to be removed after a successful driver installation.

---

### Post by bamarcus-c on 2015-05-23
> **Vladlenin5000 said:**
> Hi and welcome.

Thank you for this guide. Just a question: Have you installed the recommended nvidia drivers? The *nomodeset *parameter is necessary to have video with those nvidia chips that aren't correctly supported by the open source *nouveau* driver, such as your GFX980. Not a Linux specific issue: [https://forums.geforce.com/default/topic/778461/gfx-980-w-drivers-causes-intermittent-loading-quot-no-signal-quot-issue/?offset=2](https://forums.geforce.com/default/topic/778461/gfx-980-w-drivers-causes-intermittent-loading-quot-no-signal-quot-issue/?offset=2)
The *nomodeset *parameter is to be removed after a successful driver installation.

Once the system was installed I used the recommended Nvidia Proprietary drivers with the Additional Drivers tool in Unity dashboard. (15.04 only)

I believe that you'll need another ppa (possibly xorg-edgers) for 14.04 as there were no suggested drivers.

Also thanks for your additional comments.

---

### Post by Vladlenin5000 on 2015-05-23
> **bamarcus-c said:**
> I believe that you'll need another ppa (possibly xorg-edgers) for 14.04 as there were no suggested drivers.

Indeed. The driver in 14.04 (trusty) repos is up to 331 only, not recommended for that 'beast'.

---

### Post by bamarcus-c on 2015-05-24
It's a great GPU. I sold my R9-290X to get it.

---

