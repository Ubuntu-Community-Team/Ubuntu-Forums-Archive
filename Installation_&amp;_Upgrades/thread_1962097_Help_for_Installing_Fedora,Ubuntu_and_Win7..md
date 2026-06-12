---
title: "Help for Installing Fedora,Ubuntu and Win7."
date: 2012-04-20
forum: Installation &amp; Upgrades
---

### Post by Nikhil Parmar on 2012-04-20
Hello experts, i m new to Linux world. 
I want help for installation of fedora. Recently I installed FC16 on my  PC which had Win7 already installed(BIOS showed me Both Fedora and  Win7). After few days i decided to install Ubuntu replacing fedora, so i  removed fedora by formatting whole fedora partitn. Then when i  restarted the system,....BANG......No option for Windows 7 [IMG]http://forums.fedoraforum.org//forum/images/smilies/frown.gif[/IMG] [IMG]http://forums.fedoraforum.org//forum/images/smilies/confused.gif[/IMG]  I guess this happened because installed Bootloader on the windows bootloader something like that.

I am purchasing new laptop and i want to triple boot Win7, Fedora and Ubuntu.
Can u help me how do i install these 3 OS so that anytime i decide to  remove or format a particular OS it must not affect other 2 OS and their  BIOS entry(OS LIST IN BOOT TIME) is preserved.

Please Help.
Thanx in advance.          
                                                                                                                                          [[IMG]http://forums.fedoraforum.org//forum/images/buttons/edit.gif[/IMG]]("http://forums.fedoraforum.org/editpost.php?do=editpost&p=1571107")

---

### Post by dino99 on 2012-04-20
here is how to install:


use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

note: both swap & /home partitions can be shared by all the installed Linux distro. So to add a new linux distro, only create/format and set a bootable / , and select  swap & /home partitions without formatting them of course.

More readings with the links below  :)

---

### Post by darkod on 2012-04-20
You will just need to be careful before deleting any partition (formatting).

For example, the laptop comes with win7 preinstalled. You install FC16 and that installs its bootloader on the MBR of the hdd. The grub config files are always on the linux partition. That's why it can't work if you remove the partition.

After FC16, you install Ubuntu and that also writes its bootloader on the MBR.

So, at the end, you have grub2 from Ubuntu on the MBR.

If you delete FC16, no problem. Because the grub2 on the MBR is from Ubuntu, and the ubuntu partition is still there with the config files, it works. But if you delete the ubuntu partition, it will break.

In that case, before deleting ubuntu, you would need to boot FC16 and tell it to install its bootloader to the MBR. Then you can delete ubuntu because the bootloader is connected to FC16 which is still there.

I hope it makes it clearer. You just have to be careful which bootloader is installed, and change it before you delete that OS.

---

### Post by Nikhil Parmar on 2012-04-20
thanx **darkod and dino99** for the clear description. You rock !

---

