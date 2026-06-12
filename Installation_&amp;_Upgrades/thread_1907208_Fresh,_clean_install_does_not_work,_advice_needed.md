---
title: "Fresh, clean install does not work, advice needed"
date: 2012-01-10
forum: Installation &amp; Upgrades
---

### Post by PandaFace623 on 2012-01-10
Hello,

I am trying to install a 64-bit version of 11.10 on a freshly wiped SSD. The installation appears to go very traditionally. However after the reboot I see this (see attached photo). It gets to the 5 dot screen and just hangs there, all off center like. I've tried installing this in various ways but get the same result every time.

What advice can be offered here?

Many thanks

---

### Post by oldfred on 2012-01-11
Likely a video issue, possibly some other parameter & it just hangs at that point. Use shift from BIOS and e on grub menu to remove quiet splash to see entire boot process. It may tell where it hangs. Or it may be a BIOS setting.

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Resetting an out&#8208;of&#8208;range resolution (does not include grub's set gfxmode=640x480)
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution)
Repair grub's video mode and other settings
[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by PandaFace623 on 2012-01-11
Thanks for your great reply. I've taken a look into all your suggestions and found that nomodeset fixed the issue.

---

### Post by oldfred on 2012-01-11
I should have said try nomodeset first.:) Glad you got it working. 

If you have an nVidia card, just install the proprietary drivers that Ubuntu suggests.

Change status to Solved in thread tools.

---

