---
title: "Install on Second Hard Drive/ No Grub?"
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by Calamity Cat on 2013-02-14
I want to install Ubuntu on my second hard drive, but with each time it upsets my windows installation. 

I recently tried unplugging my Windows hard drive before installation, but GRUB still affected the Windows installation.

I know next to nothing about GRUB, but I'm more than happy to simply tell my motherboard to boot from a different hard drive each time I want to change OS. So long as it doesn't interfere with Windows.

I understand further information will likely be required, and I'll make sure to get any PC info you need to help.

All help will be much appreciated!
Thank you :D

---

### Post by tgalati4 on 2013-02-14
You can manage boot flags in gparted.  You can also install grub to the Master Boot Record (MBR) of the first hard disk or the second hard disk.  Windows security programs like to scan the MBR for changes and then change them for you.  How convenient.  This often breaks grub or breaks your second-boot distro.  It's frustrating.

So, you will have to get smart on where to install grub, what Windows is doing to your MBR, how to fix it.  Sometimes I use a USB stick to load supergrub and then choose which hard disk to boot from.  That way Windows can't touch it.

Start by enumerating your drives.  In a terminal, post the output of:

```
sudo fdisk -l
```

That's an "L" not a 1.  Write these down somewhere other than your computer, because you will need to know these then the computer is not booted.

---

### Post by oldfred on 2013-02-14
You have to install grub2 to the second drive. If you disconnect drives you have to be sure to reinstall Windows drive as the first drive. If Windows was the second drive it may have installed its boot files to the first and then when you install Ubuntu it will overwrite Windows boot loader. 

You have to have BIOS set to boot Windows drive when you install Windows to make sure it installs its boot loader to that drive.

With Ubuntu you have to use Something Else or manual install to get a choice on which drive to install the grub2 boot loader into.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

