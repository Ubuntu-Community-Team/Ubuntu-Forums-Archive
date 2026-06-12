---
title: "Unable to locate a medium containing a live file system."
date: 2013-04-29
forum: Installation &amp; Upgrades
---

### Post by sentrix on 2013-04-29
Yesterday, I 'd hard-restarted my ubuntu and it stopped working (went to grub BASH-like line) so I decided to remove the whole installation from my computer and install the 13.04 version again.
However, after the initial purple screen appears, it breaks with the following announcement: Unable to locate a medium containing a live file system.

I tried three different versions (12.04, 12.10, 13.10) with two different CDs and three different Flashes for each. However, this did not resolve my problem.
My configuration is as follows: 

Sony Vaion VGN-FW41E
Intel Core 2Duo CPU T6400 2.00Ghz

After I first installed my ubuntu few months ago, I also upgraded from Windows 7 to Windows 8 (64b).

Does anyone know how to solve this? Thanks.

---

### Post by oldfred on 2013-04-29
Is Windows 8 still in hibernation? Its standard setting is always in hibernation.
       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

What video do you have?
Did it install and not boot or have you not gotten installer to boot?

      
 Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by sentrix on 2013-04-29
I got the installer to boot, displaying the initial purple screen with dots turning white. Switching fast startup off did not work for me.
I use an ATI Mobility Radeon HD 4650. The driver seems to be up-to-date. Any thoughts?

---

### Post by oldfred on 2013-04-29
What version are you installing. 
You may need legacy drivers if installing the newer versions of Ubuntu.

 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1)
On the proprietary driver side, the AMD Catalyst 12.11 Beta Linux graphics driver was used. For this initial testing, three discrete graphics cards from the AMD Radeon HD 5000/6000 series were used, since pre-HD5000 graphics cards are now on the Catalyst Legacy driver and the latest-generation Radeon HD 7000 series hardware still doesn't fully work with the open-source Gallium3D "RadeonSI" driver.

---

### Post by sentrix on 2013-04-29
I tried to install 13.10 version. I will try your advice tomorrow. Thanks for the reply.

---

### Post by sentrix on 2013-05-01
So this solution did not work for me. I'm getting really frustrated, after four days trying to download different drivers, switching CDs and even reinstalling my current Windows operating system, I was unable to find a solution.

---

