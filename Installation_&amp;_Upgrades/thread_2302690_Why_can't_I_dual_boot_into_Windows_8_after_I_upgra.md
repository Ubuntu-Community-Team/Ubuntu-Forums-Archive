---
title: "Why can't I dual boot into Windows 8 after I upgraded from Win 7?"
date: 2015-11-12
forum: Installation &amp; Upgrades
---

### Post by lownaimail on 2015-11-12
I ran boot repair and here's is the output: [http://paste.ubuntu.com/13239731/](http://paste.ubuntu.com/13239731/)

I don't have a Windows 8 recovery disc. I was never able to boot into Windows after the upgrade. The boot screen only list:

[LIST=1]
[*]Ubuntu
[*]Advance Options
[*]Windows 7
[*]Windows 7
[/LIST]

---

### Post by furtom on 2015-11-12
Have you tried running 

[FONT=Courier New]sudo update-grub[/FONT]

from ubuntu?

---

### Post by oldfred on 2015-11-12
Did you immediately turn off the Windows fast start up setting. That is always on hibernation which grub cannot boot into.
Grub only boots working Windows, so you need a Windows repair disk.

You may be able to temporarily install a Windows boot loader with Boot-Repair in Advanced settings and directly boot Windows. Then turn off fast start up and make repair flash drive.
Then restore grub with Boot-Repair.
       Fast Startup off/hibernation - Windows 8 or 10 UEFI or BIOS boot.
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)


 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by lownaimail on 2015-11-13
I got a recovery cd to run a few commands on the cmd prompt through advance options. That allowed me to boot into windows 7 since the windows 10 reverted back. Afterward, I reinstalled windows 10 and ran a few commands such as bootrec /fixmbr and bootrec /fixboot. This allowed me to get into the other OS which is Ubuntu. There was still some problems regarding the way it sometimes boots incorrectly, but I got into Ubuntu and ran boot-repair and configured the grub using Grub Customizer. Everything is working like new now!

Thank you all for your time.

---

