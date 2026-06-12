---
title: "Installing Ubuntu in uefi - How to revise GRUB script"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by Robing Goodfellow on 2014-04-18
Short version: how does one revise the GRUB script when running the installation disk?

Detailed version: I've been a Debian and Ubuntu user since Maverick. My trusty old HP laptop died, wife bought me a spiffy new Toshiba Satellite P75 A7200. It's a monster, I love it. But it has windows 8 on it, so it's uefi. When I tried to install Ubuntu last month when we first got it, black screen, no action. Did some research, that appears to be common with the video setup in this model, something about the new Intel onboard chip. Anyway, the general consensus seems to be follow a procedure such as found at [ https://coderwall.com/p/ydbldg]("https://coderwall.com/p/ydbldg") . I figured I'd wait until Trusty was released and give it another go, but am not sure what they mean by / how to revise the GRUB script. A little help or a pointer to a tutorial would be greatly appreciated.

regards, Richard

---

### Post by oldfred on 2014-04-18
You only need to add boot parameters to grub menu.
With UEFI boot the installer uses grub menu and to add boot parameters you have to press e on menu item, scroll to linux line and replace quiet splash with nomodeset or other boot parameters specific for your computer.

Boot-Repairs ppa for trusty is not yet working. But you probably do not need Boot-Repair with trusty anyway. There are several ways to install Boot-Repair indirectly.

Best to have both a good full image backup of Windows and an Windows repairCD. Some users are reporting that a reinstall of Ubuntu says replace previous install (does not mention Windows) and overwrites the entire drive. Not sure if installer bug, or if Windows has turned on fast boot (hibernation) or needs chkdsk. If either hiberfil or chkdsk flags are set Ubuntu will not see Windows. 

Be sure to use Windows own disk tools to shrink Windows, but not to create any new partitions. And immediately reboot to run the chkdsk it needs. Make sure fast boot is still off, Windows likes to reset things its way.

       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)


 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Some of these issues may not now apply with trusty. Intel & AMD have lots of changes to kernel, support software and video drivers that only now are in trusty.


 [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by Robing Goodfellow on 2014-04-18
Marvelous, thanks!

---

