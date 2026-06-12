---
title: "Dual Boot Install Ubuntu After Windows 10"
date: 2015-09-09
forum: Installation &amp; Upgrades
---

### Post by Idrees_Ibrahim on 2015-09-09
Hello I have installed Ubuntu 14.04 after Windows 10 but I am unable to load Windows thought grub.

I also tried boot-repair but it does not help either, here is my boot-repair url:
[http://paste.ubuntu.com/12320090/](http://paste.ubuntu.com/12320090/)

Thanks in Advance :)

---

### Post by yancek on 2015-09-09
Near the bottom of the boot repair output you will see the quote below.  Windows 8 and later have hibernation set by default so that it appears to be rebooting faster.

> Windows is hibernated, refused to mount. Failed to mount '/dev/sda2': Operation not permitted The NTFS partition is in an unsafe state. Please resume and shutdown Windows fully (no hibernation or fast restarting)

So you need to boot windows and fully shut it down and turn off any 'fastboot' or 'hibernate' options.   This should have been done before installing Ubuntu and is the reason you don't have and can't get a menu entry for windows in Grub.  You might need a windows DVD to repair the master boot record, putting windows code in to boot and then doing a full shut down.  There might be other ways to do this but as a non-windows person, I don't know.  Wait for someone else who uses windows to post.

---

### Post by oldfred on 2015-09-09
While a Windows repair CD or flash drive is preferred and you need one anyway.

But you can put a generic Windows boot loader into MBR with Boot-Repair's advanced mode. Turn off fast startup in Windows and then use Boot-Repair to reinstall grub. Grub only boots working Windows so you need Windows repairs any time it has issues.

       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[URL="http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB"]http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB

[/URL]
 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

[URL="http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB"]
[/URL]

---

### Post by Idrees_Ibrahim on 2015-09-17
Thank you guys, I have Windows 10, by fixing MBR through Boot-Repair's advanced mode I am able to load Windows, and if I fix grub through Boot Repair I can able to Ubuntu fine. What I exactly need now to have a boot menu for selection which OS to load. While experimenting different options I am able to get boot menu but it shows "Ubuntu" and something like "Windows Recovery" and when I click Windows Recovery option my screen scrumbled but nothing happens and I have to restart my PC.

Please suggest what should I do to resolve it?

Thanks,
Idrees

---

### Post by oldfred on 2015-09-17
Did you turn off fast start up (hibernation) in Windows.
Grub only boots working Windows. And no hibernation nor chkdsk needed.

And grub2's os-prober has not been updated to find Windows 10, so the name is wrong. I expect your Windows recovery is really Windows 10. But booting into a real Windows recovery often causes Windows to be reinstalled as boot even if recovery not started.

You can turn off os-prober and add your own Windows boot stanza to grub2's 40_custom file with whatever description you then want. But you still have to have working Windows in bootable mode.

---

### Post by Mark Phelps on 2015-09-18
FastStartup forces Windows to go into hibernation even if you choose Shut Down and when this happens, all open partitions remain mounted, preventing access to those partitions from outside the Windows OS that was running.

There are two ways to disable FastStartup; (1) through the Control Panel, and (2) through an elevated command prompt.

Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup

Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F

In both cases, reboot Windows.

NOW, FastStartup is disabled.

---

