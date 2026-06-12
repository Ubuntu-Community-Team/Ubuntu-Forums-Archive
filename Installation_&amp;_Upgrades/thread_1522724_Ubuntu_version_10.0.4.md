---
title: "Ubuntu version 10.0.4"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by msultan on 2010-07-02
I am installing on a brand new machine and it seems that the installation goes fine and then when it reboot, the screen is black and nothing comes up.

The machine is a DELL workstation with Quad nvidia NVS 420 in it. I am installing the 64 Bit version.

Any help will be very much appreciated.

Thanks

---

### Post by davidmohammed on 2010-07-02
suggest add nomodeset to your grub settings...

press shift on reboot to display your list of kernels - this is your grub

press e

add nomodeset immediately before quiet splash

i.e. the line should read
.... nomodeset quiet splash --

---

### Post by msultan on 2010-07-02
Tried pressing the "SHIFT" key and I see the word "Grub" and then never gets to see the list of kernels. Also, tried pressing the "e" after I see the grub but still goes to blank screen. Never gives a chance or screen to type anything.

---

### Post by davidmohammed on 2010-07-02
are you sure your computer can use the 64bit version?

Have you tried the 32bit version?

Also, remember to burn the iso at the lowest speed possible.  Installations sometimes fail silently when a CD is burnt at the max speed.

When you use the desktop CD, can you "try without installing" - and see the Desktop start?

---

### Post by msultan on 2010-07-02
Yes. It's is and came with XP 64 Bit.

---

### Post by davidmohammed on 2010-07-02
> **davidmohammed said:**
> ...

When you use the desktop CD, can you "try without installing" - and see the Desktop start?

and you can see the desktop via the desktop CD?

---

### Post by msultan on 2010-07-02
now, Even if I try to reboot with the CD, It come up with the first purple screen and then nothing, not even the chance to run the install or via the CD.

---

### Post by davidmohammed on 2010-07-02
if you dont even see the select language, and install options screen from the desktop CD, then either your CD and/or CD player needs cleaning or you've got a badly burnt CD.  Suggest burning again with the lowest speed available.

---

### Post by msultan on 2010-07-02
Yes. i can run it without installing it.

---

### Post by davidmohammed on 2010-07-02
try booting your liveCD and reinstalling your grub...


 typing

```
sudo grub-install /dev/sdX
```
where X is of course the letter of the drive on which the MBR should be written (eg. sda to use the first harddrive)

then
```
sudo update-grub
```
in order to update the list of bootable systems

you should then be able to shift - and -see your grub when rebooting.

---

### Post by msultan on 2010-07-02
Here is teh error I am getting after botting with the liveCD:

ubuntu@ubuntu:~$ sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$

---

### Post by davidmohammed on 2010-07-02
... must be having a brain fade...

sorry bad advice..

following this [link]("http://ubuntuforums.org/showthread.php?t=1014708") instead.

---

