---
title: "upgrade+reboot=no graphics at all"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by Criminel on 2010-11-01
Hi,
I've installed 10.04 on two different PC's (using two different live cd's) and after updating the software and rebooting the same error came up: in both cases the computer start and then a black screen appears asking me to enter the user and password like those old DOS systems (that is: ALL graphics are gone leaving me with nothing but a useless text prompt).

Sorry about my poor english.
Help is extremely welcome.

---

### Post by oldfred on 2010-11-02
Does any of these work?

startx
or newer:
sudo service gdm start
sudo /etc/init.d/gdm start

It is likely to be a video issue.
What video do you have?
sudo lspci | grep VGA

On first boot after install, press e on getting the GRUB bootloader menu. (hold shift key from BIOS if not shown)
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
Or it should be in System>administration>Hardware drivers.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset 
    * Generic: xforcevesa or nouveau.modeset=0
    * Radeon: radeon.modeset=0

The nVidia nForce is not a graphical chip, but a chipset, so using the fix for the nvidia graphics card did not work.
The generic one did.

---

### Post by extremejosh on 2010-11-02
OK, im not using 10.04 im using 10.10 but im having pretty much the same problem i want to play some games so i really need the 3d acceleration and all ive tried install the nvidia drivers everyway i could. but still everytime i reboot i get the terminal no gui im still a big linux noob so dont know much bout what im doing im trying to learn though have a thread with my problems on it [http://ubuntuforums.org/showthread.php?t=1611450](http://ubuntuforums.org/showthread.php?t=1611450)
so i hope someone can help me i been looking every where for answers

---

