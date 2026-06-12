---
title: "Ubantu 14.04 installation error in lenovo laptop"
date: 2015-06-23
forum: Installation &amp; Upgrades
---

### Post by divyang2 on 2015-06-23
Hello,

I try to install Ubantu 14.04 alongside with windows 8 but its is giving me some error    I want to install ubantu alongside with windows 8. Please help me to solve the issue.


[ATTACH=CONFIG]262813[/ATTACH]

---

### Post by RobGoss on 2015-06-23
Hello and welcome. What are the specs for your machine? it will be most helpful if we know what your working with

How did you install your Ubuntu distribution DVD or USB drive and please give us a small detail of the process of creating your installation

---

### Post by oldfred on 2015-06-23
It looks like you are in Window and installing Wubi??
Wubi does not work with pre-installed Windows & UEFI because of the gpt partitioning.

       Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

      
 Backup efi(ESP) partition and Windows partition before Install of Ubuntu. Only one efi partition per hard drive.
Better to use Windows to shink Windows NTFS partition & reboot to let it run chkdsk and repair itself to its new size. And make sure fast startup is off in Windows. Usually better to also turn off secure boot.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)


 Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

---

### Post by hakuna_matata on 2015-06-24
> **divyang2 said:**
> 
[ATTACH=CONFIG]262813[/ATTACH]
IMHO it looks like a [Dynamic Disk]("https://msdn.microsoft.com/en-us/library/windows/desktop/aa363785%28v=vs.85%29.aspx#dynamic_disks"). For "Dynamic Disks" please read [this]("http://askubuntu.com/a/437831").

---

### Post by divyang2 on 2015-06-24
Hello I am using Ubuntu ISO file & then use wubi for installation of ubuntu.. Can't I use wubi for installation inside windows ?

---

### Post by divyang2 on 2015-06-24
I am using windows 8 64 bit.  I am using ISO file Ubuntu & then use wubi for installation..

---

### Post by sudodus on 2015-06-24
As *oldfred* wrote in post #3, wubi is no longer developed and no longer supported. I also suggest that you use another method to try and install Uubtnu.

But there are still people around who know about it, and who might be able to help you, if it is really important for you to use wubi instead of a dual boot system or a virtual machine.* hakuna_matata* who has replied in this thread knows how to use wubi. If you describe your system with more details, for example if your computer runs in UEFI mode, it makes it easier to help.

---

### Post by hakuna_matata on 2015-06-24
> **divyang2 said:**
> then use wubi for installation.
If there is a Dynamic Disk as I assumed, there is _no_ advantage in using Wubi because it is _impossible_ to install Ubuntu with Wubi! [Here]("http://askubuntu.com/questions/179215/why-cant-i-install-ubuntu-or-wubi-on-a-windows-dynamic-disk") is an example for your error message regarding Wubi. This example was on Windows 7 but unfortunately, it is also possible to create Dynamic Disks on Windows 8, even if you use [GPT]("https://en.wikipedia.org/wiki/GUID_Partition_Table").

IMHO you want "Ubuntu alongside Windows", which is not Wubi, but the question if a "Dynamic Disk" is present is also important.
   
But, maybe my assumption is wrong. So, can you check in Windows Disk Management if a "Dynamic Disk" instead of a "Basic Disk" is present?

If yes, here are [some solutions]("http://askubuntu.com/a/179309").

---

