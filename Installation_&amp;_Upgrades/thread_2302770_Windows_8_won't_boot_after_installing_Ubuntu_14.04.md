---
title: "Windows 8 won't boot after installing Ubuntu 14.04 (boot info url included)"
date: 2015-11-13
forum: Installation &amp; Upgrades
---

### Post by joni4 on 2015-11-13
I received a computer with Ubuntu installed beside Windows 8 (8.1 I think). I'm trying to load Windows now but on first load I get a strange message from the windows bootup:

"[FONT=arial]One Key Recovery partition has damaged, so do not launch the main application."

After clicking OK (the only button), the machine reboots and brings me back to the initial menu to choose an OS.

I ran boot-repair but the result was the same.

On second load of windows after boot repair I just get a blank screen with some strange colored lines on it and the computer needs to be forcefully turned off.

Boot repair url: [/FONT][http://paste.ubuntu.com/13246436/](http://paste.ubuntu.com/13246436/)

Last note, after boot repair completed, I got this message:

[FONT=arial]You can now reboot your computer.[/FONT]
[FONT=arial]Please do not forget to make your BIOS boot on sda (500GB) disk![/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]The boot files of [The OS now in use - Ubuntu 14.04.3 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

[FONT=Verdana]Any help would be appreciated.[/FONT][/FONT]

---

### Post by oldfred on 2015-11-13
If Ubuntu boots ok, ignore the far from start of drive warning. That applies to some very old BIOS, or perhaps some full installs to external USB drives. But make sure drive is set to AHCI in BIOS not IDE or the old BIOS compatibility mode.

You show your Windows boot files in sda1 which is FAT32 and shows some DOS boot files. Windows installs boot files to the NTFS partition that has the boot flag. And newer copies of Windows only boot from NTFS. Although Windows installer can be FAT32.

You already have bootmgr in sda2, I might copy or use Windows repair tools to create a BCD in sda2 and move boot flag to sda2.
You may need to temporarily install a Windows boot loader to sda with Boot-Repair to make sure Windows boots ok or use f8 to make repairs. Better to have a repairCD or flash drive as grub only boots working Windows and most Windows repairs cannot be done from Linux.
After Windows is working use Boot-Repair to restore grub to MBR of sda.

With two drives often better to have Windows fully on one drive, or it boots without other drive at all. And have Ubuntu fully on other drive. Data partitions can then be on either drive and if NTFS, used by both systems.

Not sure about sda3, It says Xenix or code 2. If NTFS it should be code 7.
You can use Disks in Ubuntu and change to NTFS, do not format, just change code or type to NTFS.

---

### Post by grahammechanical on 2015-11-13
> The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda3': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

did you see that message. Windows 8.1 is in hibernation. Putting Windows into hibernation is the method Microsoft uses to give Windows 8 a fast (seemingly) start up time. There are precautions we have to take when installing Ubuntu on a machine with Windows 8 pre-installed. Here is one of them:

> 
[LIST]
[*]In your firmware, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows 8, also [disable Fast Startup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"). 

[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You need to somehow load Windows 8 and disable Fast Startup and then load Ubuntu and run

```
sudo update-grub
```

I think that the procedure would be to use Boot Repair (Advanced options) to install a generic boot loader that will let you boot Windows 8, then to disable Fast Startup. Then to use Boot Repair to re-install Grub again.

Regards.

---

