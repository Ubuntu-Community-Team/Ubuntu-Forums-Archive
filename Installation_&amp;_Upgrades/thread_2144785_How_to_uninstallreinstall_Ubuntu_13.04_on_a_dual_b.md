---
title: "How to uninstall/reinstall Ubuntu 13.04 on a dual boot machine with Windows 8?"
date: 2013-05-13
forum: Installation &amp; Upgrades
---

### Post by Number703 on 2013-05-13
Computer came preinstalled with Windows 8. I was able to get Ubuntu 13.04 installed and running in a dual boot, but it has a lot of errors, I know from past experience that doing a fresh install can sometimes fix stuff. I've never uninstalled in a dual boot before though, so I'm not sure how to go about it? 

On AskUbuntu I found a thread for uninstalling 12.10 on a Windows 7 machine, one of the answers had: 

[COLOR=#333333][FONT=Ubuntu Beta]**WARNING!** Before you deleted your linux partition note following.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]If you have Windows installed on the same drive run fixmbr first! Then remove Linux partitions (including swap), as mentioned before.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Ubuntu Linux replaces MBR record with its own boot loader. If you just delete linux partitions you'll get unbootable drive. To fix it just boot from Windows 7 installation media, choose "Repair your computer", then "Command prompt" and run bootrec /fixmbr and bootrec /fixboot.


Is this still the same for Windows 8? What does he mean "Windows 7 installation media"? It came preinstalled so I do not have a Windows CD to boot from, so basically I need to get rid of Ubuntu but keep Windows intact and bootable. Thanks.[/FONT][/COLOR]

---

### Post by oldfred on 2013-05-13
I do not know if a fixMBR works with Windows 8 as it does not use a MBR, but uses a boot folder in the efi partition.

Since both boot folders exist and will stay in efi folder, you should just have to from UEFI menu change to Windows as default. But if you used Boot-Repair to rename files for secure boot you have to undo the file rename.
And if fastboot is on, some system cannot directly get into UEFI menu. Can you use a F-key to directly get to UEFI or do you have to go thru Windows or grub menu?

Best to have a Windows repair flash drive, and a full backup of the efi partition and the main Windows install.
 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)


 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

This also should work.
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

 LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

### Post by Number703 on 2013-05-14
Well I got it... sort of. I created a Windows repair DVD+R from eightforums.com. Couldn't really figure out the second set of links for backing up Windows, figured I don't use Windows much anyways so skipped it. Did the OS-Uninstaller, got rid of Ubuntu, then I couldn't boot into Windows, the DVD didn't fix it. Then I just reinstalled Ubuntu and did boot repair, Windows and Ubuntu work now. So, yeah. I was just trying to reinstall so worked fine for that, Idk if somebody else finds this trying to simply uninstall.

---

