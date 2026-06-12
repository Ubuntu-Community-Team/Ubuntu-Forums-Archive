---
title: "Can't Install Ubuntu 10.04 because screen goes black"
date: 2010-09-13
forum: Installation &amp; Upgrades
---

### Post by rodronin on 2010-09-13
Hey

I'm so desperate about my problems with installing ubuntu. I got a Fujitsu Siemens Computer AMD Athlon 64 Processor 3200+ 2.01 GHz and 1,50 gb RAM. I got Windows XP home edition on my computer, but i wanna completely switch to ubuntu.

At first I tried to install it with wubi, but it won't work always the same problem.

Then I tried it with the Live CD and tried demo and not install, but it fails. First there is a purple screen with a keyboard and a little guy in a circle, then there's a _ in a black screen blinking, and after that my monitor goes into standby mode. The CD is still loaded from the harddrive, but nothing happens. It feels like the Screen froze down and I can't see anything, what's going on. 

I tried it with just installing, alternate install, but it's everytime the same problem.

Can somebody please help me :( I just want to get ubuntu and explore it, my only wish :(

---

### Post by sydbat on 2010-09-13
> **rodronin said:**
> Hey

I'm so desperate about my problems with installing ubuntu. I got a Fujitsu Siemens Computer AMD Athlon 64 Processor 3200+ 2.01 GHz and 1,50 gb RAM. I got Windows XP home edition on my computer, but i wanna completely switch to ubuntu.

At first I tried to install it with wubi, but it won't work always the same problem.

Then I tried it with the Live CD and tried demo and not install, but it fails. First there is a purple screen with a keyboard and a little guy in a circle, then there's a _ in a black screen blinking, and after that my monitor goes into standby mode. The CD is still loaded from the harddrive, but nothing happens. It feels like the Screen froze down and I can't see anything, what's going on. 

I tried it with just installing, alternate install, but it's everytime the same problem.

Can somebody please help me :( I just want to get ubuntu and explore it, my only wish :(What graphics card/chip is in your computer? You can check while in WinXP by right clicking the desktop and choosing Properties.

---

### Post by oldfred on 2010-09-13
I have nvidia and my monitor went to standby & had to do this:
boot from the cd, press F6 and then select the nomodeset option.
(I acutally edited my grub.cfg as I use grub2 to directly boot ISO on USB, or in USB's syslinux.cfg or text.cfg)
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
sudo nvidia-xconfig
Or it should be in System>administration>Hardware drivers.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa
    * Radeon: radeon.modeset=0

if you've got an i8xx Intel chipset, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

Lucid 10.04 KMS advanced settings:
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf

use the uvesafb to fix all the problems
[http://idyllictux.wordpress.com/](http://idyllictux.wordpress.com/)

---

### Post by rodronin on 2010-09-14
Thanks the 'F6'-Button solution worked out fine, but now I got another issue going on. I installed Ubuntu 10.04.1 LTS and the installation completed without errors. 

What should i do now, if my screen is still turning black after i have installed it? I can't get to the logon-screen, it's just a black screen with a '_' blinking and then after 10 seconds it goes away. My monitor goes standby and nothing happens. I waited about 20 minutes, but still nothing .. i shut down, and tried it again, but everytime the same issue.


I don't know what i should do know, because the "boot from cd" option also doesn't work. I'm totally finished, because I tried this now 7 times :(

---

### Post by oldfred on 2010-09-14
Do you get the grub menu?

If so press e on the menu and scroll down to the kernel or linux line and change quiet splash to nomodeset.

Once booted in low graphics mode it should after about a minute or two offer to install the nvidia driver.

---

