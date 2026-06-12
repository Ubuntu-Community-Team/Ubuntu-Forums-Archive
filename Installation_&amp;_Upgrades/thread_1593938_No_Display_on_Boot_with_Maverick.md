---
title: "No Display on Boot with Maverick"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by TyIzaeL on 2010-10-11
Hello.

I just upgraded my laptop to 10.10 and now when I boot the display doesn't show anything. This laptop worked flawlessly on 10.04. I can tell the underlying system is fine, because if I type my boot password the hard disk activity picks up like it is continuing to boot, and CTRL+ALT+DEL reboots the computer as one would expect.

When I boot using an old kernel (a leftover from 10.04 I think) via GRUB the system boots normally. What can I do about this?

My laptop is an HP Elitebook 2730p. According to the specs it uses an Intel GMA 4500MHD for graphics. I am using the 64-bit version of Ubuntu.

---

### Post by Cpierce on 2010-10-11
Interested in seeing how to fix this. I lost the startup screen when I updated from 9.10 to 10.04. The same thing happens if I restore using clonezilla. It is not that big a deal, but it isn't "right" either.

---

### Post by TyIzaeL on 2010-10-11
I didn't lose just the boot screen. My display isn't showing anything at all.

---

### Post by Cpierce on 2010-10-13
Bump. Help please

---

### Post by oldfred on 2010-10-13
My nvidia would just turn off monitor. Settings for several different video cards.

I have nvidia and my monitor went to standby & had to do this:
boot from the cd, press F6 and then select the nomodeset option.
(I acutally edited my grub.cfg as I use grub2 to directly boot ISO on USB, or in USB's syslinux.cfg or text.cfg)
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

[http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/](http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/)
[https://wiki.ubuntu.com/X/Troubleshooting/Nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
sudo nvidia-xconfig
Or it should be in System>administration>Hardware drivers.

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

---

### Post by sdellutri on 2010-10-30
I can confirm the same problem with the same laptop.
I have HP 2730p tablet.   Worked fine with 10.04.
Put fresh install of 10.10 and now I have no video at all.
Not via LCD panel nor via external monitor.

Do I have to blow away the partitions and re-install 10.04..or is there a work around for this?

I attempted this

```
Older Intel video card: i915.modeset=1 or i915.modeset=0
```
but it didnt help

Very disappointing.

---

