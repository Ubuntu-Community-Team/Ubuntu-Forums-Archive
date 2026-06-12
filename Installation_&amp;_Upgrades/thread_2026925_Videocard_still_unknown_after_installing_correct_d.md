---
title: "Videocard still unknown after installing correct driver"
date: 2012-07-16
forum: Installation &amp; Upgrades
---

### Post by lexaal on 2012-07-16
Hello,

I just installed a Geforce 6600GT on a PC running Desktop 12.04 64BIT.

I Installed the drivers manually by modifying grub from

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text"

installed the drivers and changed it back. This worked perfectly!

Now when i am opening system info (after booting X) it still doesn't show my graphics card. It does show the right amount of memory and CPU but GPU is still unknown.

Can't seem to find out what's going wrong here. Anyone? Does my driver work or doesn't it work? I do think it works because i have more screen resolutions to choose from now, like to be sure though. Dont get it, if it works why doesnt it show up in system details.

I also heard that Nvidia graphic cards do not run very well with distro as mentioned above.

Can anyone confirm if i would make my life easyer putting the 6600GT in the trashbin meanwhile buying a Radeon Card? Or even which model would make my life really easy?

Thanx!

---

### Post by idoitprone on 2012-07-16
> **lexaal said:**
> Hello,

I just installed a Geforce 6600GT on a PC running Desktop 12.04 64BIT.

I Installed the drivers manually by modifying grub from

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text"

installed the drivers and changed it back. This worked perfectly!

Now when i am opening system info (after booting X) it still doesn't show my graphics card. It does show the right amount of memory and CPU but GPU is still unknown.

Can't seem to find out what's going wrong here. Anyone? Does my driver work or doesn't it work? I do think it works because i have more screen resolutions to choose from now, like to be sure though. Dont get it, if it works why doesnt it show up in system details.

I also heard that Nvidia graphic cards do not run very well with distro as mentioned above.

Can anyone confirm if i would make my life easyer putting the 6600GT in the trashbin meanwhile buying a Radeon Card? Or even which model would make my life really easy?

Thanx!

```
lspci -nnk
```

---

### Post by lexaal on 2012-07-16
Thanks a lot, that shows it is installed and it seems to be working fine. Always nice to be sure of things!

One more question, after driver setup had completed, it sais nvidia auto update would automaticaly show up on the first start of X. It did not and i can not find where or with what i can start it manualy. Dus anyone know what went wrong here, or better how to fix this?

---

### Post by bogan on 2012-07-16
Hi!, **lexaal**,

System Details showing Graphics and driver unknown, and a desktop Screen showing as Laptop are known bugs in 12.04 - if it works and you get Ubuntu 3D - ignore it.

The answer to you last query depends on how you installed the nvidia driver and what version driver it is.
 Did you execute a downloaded 'NVIDIA-....-.run' file? or did you use Jockey or Additional Drivers or Synaptic?? to load nvidia-current  or what?

If you did the first, you can run [ from a tty, with an Internet connection] ```
sudo nvidia-installer --latest # will report but not alter
sudo nvidia-installer --update # will report & alter existing
sudo nvidia-installer -f # will report & uninstall & install latest download
```Please Post:```
lspci -nnk | grep -iA2 VGA
sudo apt-cache policy nvidia-current
cat /sys/module/nvidia/version
```In addition, if you are in doubt, running:```
echo $DESKTOP_SESSION
```Will tell you if  you are running ubuntu 2D or 3D, or gnome.

Chao!, **bogan.**

---

