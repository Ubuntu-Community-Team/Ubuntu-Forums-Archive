---
title: "Installing/booting Ubuntu 11.04 without touching Windows 7 MBR"
date: 2011-08-05
forum: Installation &amp; Upgrades
---

### Post by Objekt on 2011-08-05
What is the "recommended" method for dual-booting Ubuntu and Windows 7, if one cannot allow the disk's MBR to be overwritten or changed in any way?

Before now, I have either installed GRUB/GRUB2 to the MBR, or else installed Ubuntu and Windows to two different hard drives.

The machine in this case, a Samsung NP300-V5A-A02US notebook PC, has only a single hard drive.  I cannot allow any alteration of the MBR, because then the Samsung backup/system recovery software (Samsung Recovery Solution 5) will no longer work.

Any suggestions?

A thousand apologies if this question is redundant, but I couldn't find an existing discussion with anyone asking quite what I wished to know.

---

### Post by Furball588 on 2011-08-05
You could use wubi to install...

I pretty sure there is a way to boot linux from the Windows bootloader though...although I'm not sure if there's a preferred cookbook method to accomplish it.  Below are a couple of links on attempts to do this....YMMV

[http://forums.techarena.in/operating-systems/1241600.htm](http://forums.techarena.in/operating-systems/1241600.htm)

[http://ubuntuforums.org/showthread.php?t=1608567](http://ubuntuforums.org/showthread.php?t=1608567)

---

### Post by YesWeCan on 2011-08-05
I'm not sure there is a recommended method. Grub and Ubuntu just assume your original MBR is unimportant. ;)

I can think of three alternatives:

1) Boot off another drive, such as a USB stick. You can now get those really tiny sticks that hardly stick out at all. Keep one plugged in at all times. Install Grub to it and boot off it.

2) You can install Grub's boot code to a linux primary partition and then boot this partition by setting the boot flag in the MBR OR add the boot code to your Windows boot-loader (recommended).
The grub program has to be forced to do this [COLOR="Navy"]sudo grub-install --force /dev/sda4[/COLOR]
It is unreliable because the boot-code uses an absolute sector address to find the core.img file inside the /boot directory, and from time to time it is possible for this address to be changed. If that happens, Grub will not work and you need to reinstall it.

3) You can do 2) but make it reliable by manually relocating the Grub files. This is complicated and fiddly to do and requires knowledge of dd and ghex.

---

### Post by YesWeCan on 2011-08-05
You could use Wubi as suggested.

You could use VirtualBox - which works really well but limits your graphical performance a little. Not good for 3D gaming. [http://www.virtualbox.org/](http://www.virtualbox.org/)

You might want to check out EasyBCD. Someone told me that it can boot Ubuntu without needing Grub but I am not so sure about that. [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by Objekt on 2011-08-05
Virtualization is not quite what I want.  I'd rather use Ubuntu in "real" mode.  Perhaps the EasyBCD approach will work.  The question is whether EasyBCD messes with the Windows boot stuff sufficiently to break Samsung Recovery Solution 5.  The worst that can happen is that I have to restore the disk using e.g. Clonezilla.  I always save an image of the disk just as the machine came out of the box, first thing, before doing anything else.

That aside, I did get Natty working in Virtualbox.  Once I installed the Guest Additions and turned on 3D accel, I was able to run with Unity on the virtual machine.

---

