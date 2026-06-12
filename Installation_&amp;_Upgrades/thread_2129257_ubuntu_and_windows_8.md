---
title: "ubuntu and windows 8"
date: 2013-03-25
forum: Installation &amp; Upgrades
---

### Post by speedfreak228 on 2013-03-25
i installed ubuntu using wubi on my windows 8 pc. when boot i do not get the option to boot into ubunut. any ideas? my pc is an alieanware mx17rc3 that came with windows 7. thanks

---

### Post by HackerFinn on 2013-03-25
I am not entirely sure about this as I do not use Wubi myself (And I discourage it.).
You should try a full install instead, as that will ensure that GRUB will be installed properly.
I have a tripleboot with Windows 7, Windows 8 and Ubuntu. That is working fine. :)

---

### Post by oldfred on 2013-03-25
Do you have the older BIOS/MBR install of Windows not the new UEFI? 
Wubi does not work with gpt partitions which UEFI requires.

Wubi now has to be installed from inside Windows.
       Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)

   wubi only installs as direct download in Windows, not from CD with 12.04
[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)

   HOW TO Avoid Wubi & Install Ubuntu on USB Drive -
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

If installed, it needs an entry in Windows BCD.
      
 [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[URL="https://help.ubuntu.com/community/Wubi"]https://help.ubuntu.com/community/Wubi

[/URL]
 bcdEdit - bcbc
[URL="http://ubuntuforums.org/showpost.php?p=11927905&postcount=5"]http://ubuntuforums.org/showpost.php?p=11927905&postcount=5

      [/URL]
 From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

    [URL="http://ubuntuforums.org/showpost.php?p=11927905&postcount=5"]
[/URL]

[URL="https://help.ubuntu.com/community/Wubi"]
[/URL]

---

### Post by speedfreak228 on 2013-03-25
> **HackerFinn said:**
> I am not entirely sure about this as I do not use Wubi myself (And I discourage it.).
You should try a full install instead, as that will ensure that GRUB will be installed properly.
I have a tripleboot with Windows 7, Windows 8 and Ubuntu. That is working fine. :)

WHats the best and easiest way to install ubuntu?

---

### Post by oldfred on 2013-03-26
If you have another hard drive, USB drive, flash drive or separate device that can boot from your system, that separates the systems. 
It is not the easiest as you have to use Something else or manual install and be sure to choose sdb to install grub2's boot load into the MBR.
       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

    
More to show Ubuntu install.
 Dual-Boot Windows 8 and Ubuntu 12.10 (BIOS)
[http://www.youtube.com/watch?v=wNCSbTyUzoM](http://www.youtube.com/watch?v=wNCSbTyUzoM)

---

