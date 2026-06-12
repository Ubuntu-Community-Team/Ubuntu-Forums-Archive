---
title: "dual boot windows 8 and ubuntu 13.04 - windows boots sometimes"
date: 2013-10-13
forum: Installation &amp; Upgrades
---

### Post by solow3752 on 2013-10-13
New linux user here. Please excuse me if this is an improper forum for this question.

I installed Ubuntu 13.04 and Windows 8 on my machine. Grub loads and I can boot Ubuntu reliably. When I select to boot Windows from Grub, it boots successfully on about one out of three tries. On the other two tries, the screen turns purple for a few seconds, then the screen turns black, then it turns back to purple with a narrow black band at the top of the screen. And it stays that way. I can force a shutdown by holding the power button and rebooting gets me back to Grub.

Any ideas?

I have already overcome a number of hurdles in this installation process. I don't expect they are relevant but I'd be happy to give details on the history of problems if requested.

Some specs:
[COLOR=#000000][FONT=arial]Sager NP2740
[/FONT][/COLOR][COLOR=#000000][FONT=arial]i7-4750HQ
16 GB RAM
Dual Boot Ubuntu 13.04 and Windows 8
[/FONT][/COLOR]
Thank you.

---

### Post by oldfred on 2013-10-14
Are you booting in BIOS or UEFI mode?

Have you turned off fast boot in Windows. That is always on hibernation that interferes with booting from grub.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)

---

### Post by solow3752 on 2013-10-14
I am booting in BIOS mode.

Yes, I turned off fast boot in Windows. Turning off fast boot was a challenge, because I got into a loop where (1) Windows was hibernated and refused to be booted at all through Grub, and (2) Windows would begin to start but recognize there had been an error and force a restart. That was a bummer and I escaped the loop by changing the UEFI settings temporarily in the setup menu before I got to Grub. So anyways, yes, fast boot is turned off.

---

### Post by oldfred on 2013-10-14
You probably are getting grub after a forced shutdown as it remembers that and gives a grub menu so you can use recovery mode. Often after a forced shutdown you need fsck.

       Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

Then it sounds like video issues.
What video do you have? nVidia needs nomodeset until you install the nVidia proprietary drives. Same with AMD. New Intel often needs a few boot parameters but only video driver is the open source default one.

      
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

