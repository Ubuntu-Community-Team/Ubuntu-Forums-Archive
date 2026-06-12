---
title: "Windows 8.1 isn't shown in GRUB after installation Ubuntu 14.04"
date: 2015-03-15
forum: Installation &amp; Upgrades
---

### Post by Dmitriy_Persiyanov on 2015-03-15
Hi. I installed Ubuntu 14.04 according to [this]("http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html") manual. But after rebooting I see only Ubuntu in GRUB list. Here is my [BootInfo]("http://paste.ubuntu.com/10603989/") and as I can see all partitions are okay. So I think there is easy fix, but I don't want to worsen the situation. Please help me.

---

### Post by ajgreeny on 2015-03-15
I don't think much of that guide, which to my eyes is more confusing than helpful, though I didn't read from start to finish. I think you have run up against the problem of installing Ubuntu in legacy BIOS mode not UEFI but the report available by running Boot-repair from my signature will help.  Don't simply accept the default repair; show us the link to pastebin that you get and someone will undoubtedly come back with an answer.

Better guides and info about UEFI installation are at:-
[UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295")
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2015-03-15
If you are booting into Ubuntu try this:

sudo update-grub

Did you leave Windows hibernated (fast boot) or change sizes of the NTFS partition from Ubuntu installer, not using Windows and rebooting immediately so it can run chkdsk. After any resize Windows NTFS partitions need chkdsk. 
Grub can only boot working Windows, and the Linux NTFS driver only mounts a valid NTFS partition.

 WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast startup
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
If issues you may need these?
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavailable, make sure fast startup is unchecked 
powercfg /h off

---

### Post by Dmitriy_Persiyanov on 2015-03-15
Thank you!
I have gained the result via ```
sudo update-grub
```.
But I have a question: Why didn't boot-repair do this job? And what does ```
sudo update-grub
``` do that boot-repair don't?

---

### Post by oldfred on 2015-03-15
If you reinstalled grub to MBR, it should have run the update-grub as part of the reinstall.

It looks like you just loaded Boot-Repair, but told it not to make any fixes.

> The settings chosen by the user will not act on the boot.


---

