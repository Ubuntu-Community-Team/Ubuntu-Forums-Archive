---
title: "Dual boot after fresh install - Win 10 do not boot"
date: 2015-10-12
forum: Installation &amp; Upgrades
---

### Post by stefano.campanini on 2015-10-12
Hi 

I've just installed ubuntu 15.04 along side existent  windows 10 .
After that I was not able to see the grub menu, so I executed this in windows:

```
bcdedit /set {bootmgr} "path\EFI\ubuntu\shimx64.efi"
```

After that, I can see the grub menu, ubuntu starts correctly, but windows do not start. Selecting windows on grub menu, windows suggest me to "fix" the boot part... because it is not able to start.

I attached an almost complete bootInfoscript Result of my notebook.

Any ideas ?
I'm trying to doanlad Boot-Repair-disk utlity, but it is downlading very slow ( 1 day ... )

Stefano

---

### Post by oldfred on 2015-10-12
The bootinfoscript is the same as the first third of the Summary Report from Boot-Repair.
If should only take a few minutes to download even on a slower Internet. It is not large.

Most often the issue is that users leave Windows fast startup on. Grub only boots working Windows, or Windows that is not hibernated nor needs chkdsk. So with UEFI you need to directly boot Windows from UEFI or one time boot key, often f10 or f12.

       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

Often best to have Windows repair disk:
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

