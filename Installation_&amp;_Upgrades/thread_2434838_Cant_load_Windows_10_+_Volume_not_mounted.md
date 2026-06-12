---
title: "Cant load Windows 10 + Volume not mounted"
date: 2020-01-11
forum: Installation &amp; Upgrades
---

### Post by stefanosapergis on 2020-01-11
Hello. I just installed Ubuntu on my Windows 10 Xiaomi laptop via USB stick and i cant boot on Windows 10. It says Preparing automatic Repair. I tried a lot of things i found on the web, and i still cant resolve it. Any suggestion?

---

### Post by oldfred on 2020-01-11
Did you turn off fast start up in Windows? Or does Windows need chkdsk?
Grub only boots working Windows, which also means hibernation must be off. So you may have to boot from UEFI boot menu, same key as you used for Ubuntu installer.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by stefanosapergis on 2020-01-11
> **oldfred said:**
> Did you turn off fast start up in Windows? Or does Windows need chkdsk?
Grub only boots working Windows, which also means hibernation must be off. So you may have to boot from UEFI boot menu, same key as you used for Ubuntu installer.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Yeah but i cant get to Windows 10. So i cant understand how to solve it.

---

### Post by oldfred on 2020-01-11
If an UEFI install, you just boot Windows from UEFI boot menu.

But if an old BIOS/MBR install and only one drive, you only have one MBR to boot from.
So when grub does not boot Windows, you have to temporarily restore a Windows boot loader, fix Windows, then restore grub boot loader.
You may be able to use Boot-Repair's advanced option to choose Windows & MBR. But often better to use Windows repair flash drive and fixMBR command.
Then use Boot-Repair or manually commands from live installer to restore grub boot loader to MBR.

---

### Post by dragonfly41 on 2020-01-12
> [COLOR=#000000]It says Preparing automatic Repair[/COLOR]

I have seen that on occasions. I just wait for some time until auto repair concludes in Windows then I shutdown and boot into whatever OS.

---

