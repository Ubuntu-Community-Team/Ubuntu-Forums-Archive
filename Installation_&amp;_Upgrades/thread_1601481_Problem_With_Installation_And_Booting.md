---
title: "Problem With Installation And Booting"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by sampath.soundappan on 2010-10-20
Hi i used to use ubuntu 9.04 on my lap compaq 515,
it worked well. But on upgrading to the higher versions(9.10, 10.04) the system failed to boot. Whenever i tried to install, the laptop would freeze and just show a blank screen.
The Configuration of my system is below
 
Processor-**AMD Athlon X2 64-bit **
RAM-       **1.7Gb**
HDD**-       150Gb**
Graphics Card**-ATI Radeon 3200 HD Graphics** **(256MB)**
 
I would like some one to help me with this problem. Is the problem actually with the operating system?. Does the new versions of ubuntu support this configuration or not?
If there is any other problem please let me know.
 
Im able to use all the versions of fedora in this system. But im a fan of ubuntu and would love to continue using it. Hoping to hear a reply soon.

---

### Post by lemming465 on 2010-10-21
Try an Ubuntu 10.10 live CD.  If that works, there are fairly good odds an installed system would work.

---

### Post by oldfred on 2010-10-22
I have nvidia but the setting may be the same or slightly different - see below:

I have nvidia and my monitor went to standby & had to do this:
boot from the cd, press F6 and then select the nomodeset option.
(I acutally edited my grub.cfg as I use grub2 to directly boot ISO on USB, or in USB's syslinux.cfg or text.cfg)
then
On first boot after install, press e on getting the GRUB bootloader menu. (hold shift key from BIOS if not shown)
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

[http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/](http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/)
[https://wiki.ubuntu.com/X/Troubleshooting/Nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

(from Fedora)
All drivers: nomodeset - this will disable the kernel modesetting feature and drop the user back to the old X.org infrastructure and behaviour. 
nouveau.modeset=1

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset 
    * Generic: xforcevesa or nouveau.modeset=0
    * Radeon: radeon.modeset=0

if you've got an i8xx Intel chipset, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

Lucid 10.04 KMS advanced settings:
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf

---

