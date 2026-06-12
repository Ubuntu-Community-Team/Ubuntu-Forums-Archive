---
title: "Multibooting Ubuntu/Win/Mac Bootloader Help"
date: 2012-12-29
forum: Installation &amp; Upgrades
---

### Post by dorruk on 2012-12-29
Hey guys, I'm new with linux and could hardly use the terminal, and currently am dualbooting Windows 7 and 8. I need to install a Linux distribution (Ubuntu or Backtrack) as well as Mountain Lion, each OS in different partitions and keeping my Windows'.

I'd like to display all 4 OS's at the boot. So what should be the steps to follow in order to avoid complications in bootloader? I do not want to just sit there at the end with an unbootable computer. Thanks in advance.

---

### Post by james2b on 2012-12-29
Since you include Windows 8 in your multi-boot setup, then you need to provide more information about your computer hardware and the BIOS replacement called UEFI does have that secure boot feature which can be most often disabled. And you can prepare the drive partitions by shrinking the windows 7 and or 8 from in them with that computer management disk manager tool if needed, and then use a partition tool CD such as GParted to boot to for any other changes on that drive. [http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php) , just burn the image to a CD. Are you sure you can also include the Apple Mac O/S in that system ? For booting you can just put the grub2 on master boot record which should allow all the others to boot. I use windows boot manager with EasyBCD for XP, Vista, Win 7, and Ubuntu, so my other Linux installs I can boot from the Ubuntu grub on it's root partition either directly or by the chainload method, also EasyBCD has neo-grub that works well for Linux and is based on legacy old grub.

---

### Post by oldfred on 2012-12-29
Thread closed.

Hackintosh/Apple EULA violation. 
We do not support circumventing TOS, EULA, etc here. Such threads will be closed and offending users will be penalized with infractions and warnings.

For more information, please see the forum policy: 
[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy). 
If you believe this was made in error, please post in the Resolution Center, which you can find in the previous link.

If you want help just booting Windows & Ubuntu start a new thread.

---

