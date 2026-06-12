---
title: "Ubuntu 12.10 dual boot. Windows 8 Hibernate problem."
date: 2013-03-16
forum: Installation &amp; Upgrades
---

### Post by JubyPW on 2013-03-16
Hi, i'm new here, i've got some problem with Ubuntu 12.10. I recently installed it with wubi form .iso file. Now i've got a problem, when I restarts computer and selecting Ubuntu it says something about Hibernation of Windows. It looks like windows is hibernated, i know, new windows is using hibernation to "fast boot", but someone know how to install ubuntu without removing windows?

I've got both systems x64.


Sorry for my very bad english.

---

### Post by oldfred on 2013-03-16
I do not know wubi, but it does not install from a liveCD anymore but only from inside Windows. And it does not work with gpt patitioning, so if your Windows 8 was pre-installed it is secure boot with UEFI and gpt partitioning. 
If you installed Windows 8 yourself with MBR(msdos) partitioning you should be able to download from inside Windows & install.

       Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)

   wubi only installs as direct download in Windows, not from CD with 12.04
[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)

      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

