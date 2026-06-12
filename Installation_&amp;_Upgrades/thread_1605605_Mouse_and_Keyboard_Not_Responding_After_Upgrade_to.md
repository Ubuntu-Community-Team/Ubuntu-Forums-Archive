---
title: "Mouse and Keyboard Not Responding After Upgrade to 10.10"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by colsandurz on 2010-10-25
Neither the usb keyboard nor the usb mouse respond after I upgraded a dell machine to 10.10.  

The situation I'm in with this machine is a little hairy: there are no PS/2 ports and the grub splash blows by so fast I can't read anything.  

When I press C of Esc (during the grub splash) nothing happens.

I've similar problems before (on other machines) and playing with the ACPI or USB settings in the BIOS seemed to help.  But with this machine the BIOS doesn't seem to be able to change anything with either of those.

Right now, I'm going to boot the machine with a usb key and I'm going to try to add the default xorg.conf file (since there is no xorg.conf file by default now) and I'm going to change the grub boot splash timeout to longer than 0.

What are my other options if this doesn't work?  Also, reinstalling is not an option for me.

---

