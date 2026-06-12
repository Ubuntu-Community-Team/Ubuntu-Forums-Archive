---
title: "Can't reboot Windows after installing Ubuntu"
date: 2017-03-01
forum: Installation &amp; Upgrades
---

### Post by arrigo.benedetti on 2017-03-01
After installing Ubuntu 16.04 on an Intel NUC where Windows 10 was already installed, I am not able to reboot Windows. I have run Boot-repair from Ubuntu and created a pastebin at [http://paste2.org/10xVsXPY](http://paste2.org/10xVsXPY)

Any ideas?

Thanks

-Arrigo

---

### Post by oldfred on 2017-03-01
Boot-Repair is telling you the problem.
> Windows is hibernated, refused to mount.

 	Failed to mount '/dev/sda2': Operation not permitted
 	The NTFS partition is in an unsafe state. Please resume and shutdown
 	Windows fully (no hibernation or fast restarting), or mount the volume
 	read-only with the 'ro' mount option.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Normally I thought NUC were UEFI, then you could directly boot Windows from UEFI boot menu.
But with BIOS you will have to temporarily reinstall a Windows boot loader and turn off the fast start/hibernation.
Then restore grub to MBR and run 'sudo update-grub' to add Windows to grub menu.
Since Windows often turns on fast start with updates, keep both a Windows repair flash drive & Ubuntu live installer handy.

       
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by arrigo.benedetti on 2017-03-01
Thanks, I was able to get into Windows just by running Boot-repair from Ubuntu, then I disabled the fast start and now I can switch between the OSs.

---

