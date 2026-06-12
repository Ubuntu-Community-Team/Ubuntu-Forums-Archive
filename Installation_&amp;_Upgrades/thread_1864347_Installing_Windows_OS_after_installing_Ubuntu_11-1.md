---
title: "Installing Windows OS after installing Ubuntu 11-10"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by Chuo FPS on 2011-10-18
Hi,

I've just bought an Asus K53E laptop which came with Windows 7 OS preinstalled. Rather stupidly, I now realise (I live in Japan and everything was in Japanese!), I completely deleted it when I installed Ubuntu 11-10 OS. But I would now like to partition my HD to install an older version of Windows XP alongside Ubuntu. I need to use Windows for Empress presentations, as there are always interface problems between the computer and slide projector.

Is it possible to install Windows on an unpartitioned HD that is running Ubuntu? I tried simply inserting the Windows CD but it stops after a couple of minutes claiming the HD is unsuitable/infected etc. I guess I'd need to partition the HD first - how do I do this, from disk utility or by using the Ubuntu start-up CD and partitioning from there by reinstalling Ubuntu alongside Ubuntu, as it were?

I'd be grateful for any advice, though I have the feeling it can only be done in reverse order, i.e., installing Ubuntu alongside a Windows OS that is already installed.

Thanks for any help

---

### Post by MarinePride on 2011-10-18
Windows wants to be the only operating system on your hard disk and will not offer any type of dual boot option when powered on.  Ubuntu, on the other hand, will offer you the option to boot into Windows or Ubuntu.

---

### Post by Norwal on 2011-10-18
> **MarinePride said:**
> Windows wants to be the only operating system on your hard disk and will not offer any type of dual boot option when powered on.  Ubuntu, on the other hand, will offer you the option to boot into Windows or Ubuntu.

What MarinePride is saying is true.  Windows will not allow another non Windows OS to dual boot.  You will need to install Windows 1st and then Ubuntu second. Check the following link:  [http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/)

Good luck.

---

### Post by oldfred on 2011-10-19
You do not have to install Windows first, but sometimes it is a bit easier.

Windows does have to have a primary NTFS partition with the boot flag, or unallocated space with a primary partition available to install. It will overwrite your grub2 boot loader in the MBR so be prepared with a liveCD or boot repair disk to fix the grub2 boot loader.

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Older but discusses the issues, reinstall grub2, not other alternatives:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
Do not use the dd to back up MBR, best just to reinstall:
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

---

### Post by Norwal on 2011-10-19
Good to know Oldfred. Thanks

---

### Post by Chuo FPS on 2011-10-20
Thanks for the help. Oldfred's solution seems the wisest, but it also sounds like the most complicated and I could probably do it, but it'd take me hours to do it right. I'll try from the beginning again, reinstalling Windows and then partitioning at the beginning of installing Ubuntu alongside it.

As I've just spent a week organising the settings (bookmarks, mail folders, OOO menus, etc.), I was wondering if there's any way of saving everything I've set up so far so that when I reinstall Ubuntu a second time I can continue with the settings I've got now?

Thanks again

---

### Post by oldfred on 2011-10-20
The vast majority of your settings are in /home (all user settings). If you made any system wide settings they are in /etc (wireless config, network, video etc).

I always plan a new install if my system crashes so my backup is /home and a some configurations settings.

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by Chuo FPS on 2011-10-20
Many thanks once again, oldfred, your answer is perfect. Thanks for all the help.

---

