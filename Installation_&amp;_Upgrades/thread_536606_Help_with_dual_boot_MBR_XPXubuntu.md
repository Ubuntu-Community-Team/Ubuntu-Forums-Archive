---
title: "Help with dual boot MBR XP/Xubuntu"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by ThorsDecree on 2007-08-27
I have a real problem here...

I already had Xubuntu installed on /dev/hdb1 when I decided to install WinXP on a new donation hard drive, /dev/hda1

I also have a /dev/hda5 partition I currently use as Win swap, but more on this later

I now CANNOT boot into Xubuntu from hard drive. The CD "boot from 1st hard drive" takes me to Windows's NTLDR bootloader, and only allows for booting XP. How/Where do I install Grub on the windows partition to let me boot into Linux from HD? Right now while I'm trying to fix this I am using a damnsmalllinux liveCD. My other post for help here is on [http://www.hellboundhackers.org/forum/viewthread.php?forum_id=16&thread_id=9733#79240](http://www.hellboundhackers.org/forum/viewthread.php?forum_id=16&thread_id=9733#79240)

I honestly have very little idea for what I am trying to do. All I know is that I want to either be able to boot both Windows and Linux from Grub and not use any other bootloader, or I want to at least be able to get to Grub from NTLDR to boot Linux. All I need is to be able to boot, as right now I cannot!

Thanks for any advice and help, it is really appreciated.

If it is relevant, this is an entirely new computer system from last time I was able to boot Linux from HD (Still used livecd to boot from HDD then). The BIOS is different, it goes straight to NTLDR when there's not a CD in the drive and it won't let me choose a drive to boot from.

---

### Post by scrooge_74 on 2007-08-27
Yours is a common problem, you have already Linux install and then install XP.  Xp will change the MBR and you need to reinstall GRUB

Always put M$ first and then Linux

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28reinstall%29%7C%28grub%29](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28reinstall%29%7C%28grub%29)
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by ThorsDecree on 2007-08-28
I'm getting a lot of good help at hbh, and thanks for the links. I'll check those out. I think I do NOT have a bootloader installed for Linux, so I'm goign to try to install Grub from a liveCD.

Thanks for the links.

---

### Post by ThorsDecree on 2007-08-28
I reinstalled and that installed GRUB, so all's fixed now

---

