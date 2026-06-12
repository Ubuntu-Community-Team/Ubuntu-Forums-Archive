---
title: "Enabling restricted nvidia driver"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by iamvlad on 2007-11-23
Hello,

After searching this forum for a while I saw that many people have problems with their nvidia videocards, however I didn't find a post that resolved my issue yet.

I just installed Ubuntu 7.10 on my computer. This is my first experience with linux.

I have a Geforce FX 5700, I can change the resolution from 640X480 to 1600X1200, but when I try to change the Visual Effects (under Appearance) it says that the nvidia driver needs to be enabled. After clicking enable it gives the error: "the software source for the package nvidia-glx-new is not enabled"

If I go to restricted drivers manager it does the same thing.

In terminal if i run "sudo nvidia-settings" it returns "sudo: nvidia-settings: command not found"

Thanks in advance for your help,
V

---

### Post by sirdilznik on 2007-11-24
In Synaptic you need to enable restricted drivers.  In synaptic:

Settings > Repositories > Ubuntu Software 

Check the box next to Proprietary drivers for devices (restricted).  You might as well check the universe and multiverse repositories too.  Apply changes and then search for "nvidia".  You should be able to find a package called nvidia-glx-new.  Install that.  You may also need to adjust your /etc/X11/xorg.conf afterwart though there ate utilities that do this automagically.  Once that is all set you will need to reboot (or load the module and restart X).

You are currently probably running on generic vesa drivers.  The nvidia drivers will allow you to do opengl 3D.  Note that there is a conflict with nvidia drivers and the kernel used in 7.10 by default (2.6.22).  The drivers will fail to load if splash is enabled (as it is by default).  You can bypass this be doing one of the following:

1) Disable bootsplash (delete "splash" from the main boot line in /boot/grub/menu.lst)
2) Compile a custom kernel and use something other than 2.6.22 (2.6.21 or 2.6.23 for example)

---

