---
title: "Low graphics mode on Ubuntu 14.04.3"
date: 2015-08-17
forum: Installation &amp; Upgrades
---

### Post by speed2 on 2015-08-17
[COLOR=#111111][FONT=Ubuntu]Hello Ubuntu community. I've been trying to setup / load Ubuntu for a while now, but It won't let me set it up. I get the error "The system is running in low graphics mode" and I have a NVIDIA GeForce GTX 750 Ti graphics card. I put the ISO file on a USB, it's on the USB and all just fine. I tried following guides by doing [/FONT][/COLOR]sudo apt-get install nvidia-current[COLOR=#111111][FONT=Ubuntu] [/FONT][/COLOR]sudo apt-get install nvidia-current-updates[COLOR=#111111][FONT=Ubuntu] in terminal but they don't work. The reason they don't work is because they require me to reboot the computer. When it makes me reboot my computer it's like nothing was done to Ubuntu. I have the same errors, and I have re-do any commands I had to do before I rebooted the PC. In other words when I restart the PC all gets reset back to when I found the error. So whenever I go to load Ubuntu again it just restores back to where the low-graphics mode is. So I was wondering how do I bypass the low-graphics mode when I have the problems that I do?[/FONT][/COLOR]

---

### Post by grahammechanical on 2015-08-18
The Ubuntu live session uses an open source video driver and not a proprietary video driver. When we install and tick the box "Install third party software" we get some proprietary audio and video codecs and a proprietary video driver. So, if the live session works fine and after install we get video problems then it all points to some conflict with the proprietary video card.

A simple solution would be to install without ticking that box. And if that works we can get the audio and visual codecs by installing Ubuntu Restricted Extras from the Software Centre. We can also go to System Settings>Software & Updates> Additional Drivers tab and experiment with proprietary video drivers.

Another option that you might try is to select Advance Options at the Grub boot menu and then select Recovery mode and at the recovery menu select Resume. That may get you to a working desktop and you can experiment with video drivers from there.

Regards

---

### Post by efflandt on 2015-08-19
For some reason the GTX 750 Ti (and likely other cards with new Maxwell chip) do not work with initial nvidia-current (a 304 version) in 14.04 (even though whatever updated nvidia-current of a 304 version works in 12.04). For nvidia graphics on a desktop you typically need to use **nomodeset** kernel boot parameter during install and that should carry over to the installed system. But I read not to do that on laptops with hybrid Intel/Nvidia graphics, so I did not on my laptop.

Since your graphics is not working properly and not sure if you can get to a text terminal from their, I would suggest booting your system in **recovery mode**, in the menu Enable Networking (which also mounts your drive read-write instead of read-only) and once that returns, go to Root Console. Normally when logged in as yourself you would need to use "sudo " prefix for following commands, but in the recovery root console that is not necessary.

Do the following in the root console:```
apt-get update
apt-get purge nvidia*
apt-get install nvidia-331-updates
```Then take a look through /boot/grub/grub.cfg (**less /boot/grub/grub.cfg**) and see if lines that start with linux like this [other than menuentries for (recovery mode)] contain **nomodeset** in them like this (although, they may appear word wrapped depending upon terminal width):```
linux    /boot/vmlinuz-3.13.0-62-generic root=UUID=b226357c-b349-498a-8bba-1ea7bed78d43 ro nomodeset quiet splash $vt_handoff
```If not it would not hurt to add that to /etc/default/grub (**nano /etc/default/grub**) and insert nomodeset in the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" making it **GRUB_CMDLINE_LINUX_DEFAULT="nomodeset quiet splash"**, then Ctrl+X to save and exit. Then run```
update-grub
reboot
```When you reboot you should have working graphics.

PS: Note that if you run any of these commands to use apt-get or to modify root files or update-grub from a normal terminal when logged in as yourself instead of in root console, you would need to use "sudo " prefix (with space after, but no. quotes)

---

