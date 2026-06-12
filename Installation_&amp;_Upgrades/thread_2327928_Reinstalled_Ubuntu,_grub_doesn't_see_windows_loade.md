---
title: "Reinstalled Ubuntu, grub doesn't see windows loader only windows recovery"
date: 2016-06-15
forum: Installation &amp; Upgrades
---

### Post by ayazkhan-bayanov on 2016-06-15
I have just reinstalled my Ubuntu, and something went wrong as after I ran boot-repair, I cannot see my windows loader, but only windows recovery.
Also when I'm trying to access the windows partition from ubuntu, this message appears:
```
Error mounting /dev/sda2 at /media/ayaz/E41ED4DD1ED4AA36: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda2" "/media/ayaz/E41ED4DD1ED4AA36"' 
exited with non-zero exit status 14: 
The disk contains an unclean file system (0, 0).Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

```
here are the report urls that are saved after boot-repair
[http://paste.ubuntu.com/17381025/](http://paste.ubuntu.com/17381025/)
[http://paste.ubuntu.com/17381545/](http://paste.ubuntu.com/17381545/)

---

### Post by oldfred on 2016-06-15
Is this the newer Windows 8 or 10?
Then you have to have fast start up off. That is always on hibernation. And the Linux NTFS driver cannot mount the NTFS partition if it is hibernated or if it needs chkdsk.

If  a BIOS install, you can use Boot-Repair to temporarily install a Windows type boot loader to MBR, boot Windows, turn off fast start up and then use Boot-Repair to reinstall grub to MBR.

       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold"]http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold

      [/URL]
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 
    [URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold"]
[/URL]

---

