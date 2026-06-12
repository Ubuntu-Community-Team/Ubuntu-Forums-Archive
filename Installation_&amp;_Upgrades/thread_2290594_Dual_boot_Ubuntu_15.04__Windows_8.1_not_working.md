---
title: "Dual boot Ubuntu 15.04 / Windows 8.1 not working"
date: 2015-08-13
forum: Installation &amp; Upgrades
---

### Post by chsbrg on 2015-08-13
Bought an Acer Aspire V3-112P-P9Z0 two weeks ago and try unsuccessfully to install Ubuntu 15.04 alongside Windows 8.1 since. Tried other distros (Linux Mint, Manjaro, SuSE) as well cause I found SOLVED threads for them on the internet - but always with the same result: graphical as well as command line installers show that the installation succeeded but during reboot Ubuntu (or the other distros I tried) not even show up in the boot menu. Parameters for the installation are:


[LIST]
[*]500 GB HDD 
[*]GPT 
[*]UEFI = enabled 
[*]secure boot = disabled 
[*](U)EFI partiton = sda2 
[*]fastboot = disabled 
[/LIST]
 
All my mkdir-, mv-, cp- and rm-attempts may have led to a pretty mess. A boot-info output can be found here [http://paste.ubuntu.com/12071453/](http://paste.ubuntu.com/12071453/), the results of a recommended repair (boot-repair) are here [http://paste.ubuntu.com/12071508/](http://paste.ubuntu.com/12071508/). ANY suggestion will be highly appreciated.

Thanks!

---

### Post by oldfred on 2015-08-13
Acer needs you to set a supervisor password and "trust" the Ubuntu boot files. 

You also need to turn off Windows fast startup or always on hibernation. That is different than fast boot in UEFI settings.
       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[URL="http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8"]http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8

      [/URL]
 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
Details on password & trust setting:
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi)
How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3 Supervisory password required
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)

    [URL="http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8"]
[/URL]

---

### Post by chsbrg on 2015-08-14
@ oldfred:

**THANK YOU VERY MUCH!!**! You saved my (digital) life and - less pathetically - at least a huge amount of life time! ;)

The  settings for trusted boot files did it. I'd never figured that out and can't believe that features of  such an importance and reach aren't documented properly. Though most of the online tutors recommend to disable secure boot the parallel installation of a Linux OS often actually seems to work flawlessly with secure boot enabled. With manjaro I opted for secure boot = disabled for installing and opted for secure boot = enabled afterwards to have access to the "select trusted efi file" feature.

Right now I  have to invoke the different boot menus by pressing F12 on boot but  that's fine with me. Just for testing I've installed manjaro on another  partition and I now have access to each of the three installed OS's.

---

### Post by oldfred on 2015-08-16
You are welcome.

I think Acer is the only one that requires a UEFI supervisory password and specifically enabling trust on boot files. 
Some do require passwords to open up more UEFI settings. And may do not require any passwords, but UEFI does seem to require more setting changes than old BIOS used to.

---

