---
title: "Wubi performance"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by shwarto on 2010-10-25
I want to install Ubuntu but not as Dual-Boot (Other OS is Windows XP x64 edition).

Does Wubi perform significantly better than an Ubuntu version installed on VMWare or VirtualBox?

My computer has:
[LIST]
[*]Intel Core2 Quad Q8200 @ 2.33GHz
[*]4GB RAM
[*]An almost empty 450GB HD (defragmented)
[/LIST]

---

### Post by marin123 on 2010-10-25
wubi is way better then running virtual machine... wubi is actually dual booting, but you use windows boot loader instead of grub and you dont have to create a partition for installation (everything is stored on your windows drive)...
ubuntu performs better then wubi just because its installed on ext4 drive, while wubi runs on ntfs...

---

### Post by shwarto on 2010-10-25
I suppose I have a way smaller chance of ruining my system if I use Wubi and not Dual-Booting the normal way.

I need the advantage of installing software and maintaining the changes and also running some 3D applications. My computer is rather strong, I suppose. Would you say running Wubi gains a decent performance experience**[SIZE="3"]?[/SIZE]**

My Windows XP is a 64-bit edition. I need to use an Ubuntu 32-bit edition. Should there be a problem**[SIZE="3"]?[/SIZE]**

---

### Post by Rubi1200 on 2010-10-25
Wubi was never intended to replace a hard-drive install (it is meant as a way for new users to try something different without worrying about things like partitioning etc.) and there may well be performance issues. There are also problems with Wubi updates and GRUB from version 10.04 onwards.

If you have 4GB RAM and 450GB of drive space why not do a regular install?

You could, for example, create a 20GB partition and install Ubuntu there, leaving the rest of the drive free for whatever you want.

---

### Post by shwarto on 2010-10-25
> **Rubi1200 said:**
> If you have 4GB RAM and 450GB of drive space why not do a regular install?

I'm not that familiar with partitioning software. I've never done such a thing and the well-being of my computer is crucial at this time. That's why I'm a bit scared of doing such things as partitioning and dual-booting (regularly) at this time.

I also have an almost full 25GB HD and an almost full 50GB HD on this computer. If I move the contents of one of them to the 450GB HD, would I be able to use the 25GB HD or the 50GB HD without partitioning? Just simply installing to that drive during the regular Ubuntu installation?

---

### Post by Rubi1200 on 2010-10-25
Yes, I think that would be possible.

Ubuntu can format and install with defaults wherever you tell it to.

Just make sure to backup everything (or move it).

In my opinion, unless you plan on installing a LOT of software or saving masses of files, 25GB should be more than enough. A regular default install takes up about 3GB.

Just make sure that GRUB is installed correctly (i.e. to the drive where you install Ubuntu and be aware that GRUB will then run the loading of other operating systems). 

I think it is also advisable to unplug the other drives before installing to the drive where you want Ubuntu installed. That way you should avoid any problems with where GRUB will go.

But, before you proceed, ask questions if there is anything unclear or just if you need more information.

Here are some links which I hope will also be helpful:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) (explains what GRUB is and how it works)
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817) (excellent guide to installing and running more than one operating system)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition) (partitioning guide)

However, if you feel at all uncomfortable with the idea of dual-booting, then take the safer route and install using Wubi.

Here is the guide and other information:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

