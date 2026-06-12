---
title: "Boot Loader Problem"
date: 2017-12-10
forum: Installation &amp; Upgrades
---

### Post by breweric on 2017-12-10
I am having issues with a dual boot with Windows 10 and Ubuntu.  I installed Ubuntu and rebooted and it always boots Windows 10.  I cannot seem to figure out how to boot to the Grub menu.  Here is the information from the Boot-Repair program.  

[http://paste.ubuntu.com/26153885/](http://paste.ubuntu.com/26153885/)

Thanks for any help.

Eric

---

### Post by yancek on 2017-12-10
Since you can boot into windows, have you tried the suggestion at the bottom of the boot repair output to add Ubuntu to the windows bcd menu.  Use windows powershell from the main menu and make sure you right click and select to run as administrator or the command won't work. If you are then able to boot to Ubuntu, post back for more details.

---

### Post by oldfred on 2017-12-10
What model HP?

HP typically has not been UEFI dual boot friendly. 
Does Ubuntu boot using Escape+f9 and chose Ubuntu entry from UEFI boot menu?

It looks like Boot-Repair copied the /EFI/Boot/bootx64.efi and then made it a copy of shimx64.efi to boot Ubuntu. That is a fallback boot entry.
Does a UEFI hard drive boot entry boot Ubuntu?
 Sony, HP & others workarounds:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114)

---

### Post by breweric on 2017-12-14
So I did find a work around that worked for HP.  It appears I have to hit the ESC key when I boot up the laptop, then select the F9 option to get to the screen for booting Ubuntu.  If you don't do this it appears to auto boot to Windows.  

So not sure why HP architecture is this way, but looks like going to have to deal with it for now.  

I do appreciate the support and if anyone knows of a way around the "ESC" + F9 option.

---

