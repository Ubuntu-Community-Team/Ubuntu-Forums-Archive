---
title: "Installed Ubuntu 10.10 with Windows 7, but the bootloader disappeared..."
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by elymic on 2011-01-06
Dear friends,

I've tried to install Ubuntu 10.10 in a new partition on my new Dell, which came with pre-installed Windows 7. It all went well except for the fact that the bootloader just doesn't function. I was hoping to use my computer as a dual-boot and choose either Ubuntu or Win 7 at start up, but I never get to the bootloader screen and Ubuntu starts automatically. Is there a solution to this problem? I'm a newbie to linux.

Thanks !

---

### Post by Quackers on 2011-01-06
Open a terminal and run ```
sudo update-grub
``` and watch to see if the Windows Loader is picked up as grub.cfg is run. 
If it is, reboot and you should get the grub menu, giving you a choice of OS to boot. Try Windows to see if it boots ok.

---

### Post by kansasnoob on 2011-01-06
Just post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternate instructions:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by presence1960 on 2011-01-06
I believe Dell is one of the vendors who pre-install software which writes to the MBR, therefore writing in the area occupied by GRUB. I am not familiar with the name of the software, but you need to disable it from running or your GRUB will continue to not function. I am going to PM someone who is familiar with this and maybe he can be more specific than I can.

**_P.S. I would still run the boot info script as kansasnoob suggests, just in case it is not that software. At the very least we can get a look at your boot process to make sure it is ok_**

---

### Post by Quackers on 2011-01-06
Dell Data Safe is one of those.

---

### Post by presence1960 on 2011-01-06
> **Quackers said:**
> Dell Data Safe is one of those.

Thanks Quackers. I just PM'd oldfred because I remember from a previous thread that he knows the exact names of the software used by Dell & HP.

---

### Post by oldfred on 2011-01-06
Dell datasafe seems to be the most common one for Dells. 

meierfra. posted some to his web page before. Grub has already fixed flexnet as we have seen some users question why grub gives a warning on sector 32.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
[http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable](http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable)
[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html)
In Windows 7, had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, flexnet and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

---

### Post by Quackers on 2011-01-06
oldfred - a veritable mine of information - and links :-)

---

