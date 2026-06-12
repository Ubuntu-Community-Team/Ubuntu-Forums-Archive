---
title: "Reinstalled GRUB using Boot-Repair and now cannot get into BIOS or boot Windows"
date: 2014-12-28
forum: Installation &amp; Upgrades
---

### Post by sseritan on 2014-12-28
Hey,

I originally had my 14.04 Ubuntu installed side-by-side with Windows 8.1, and everything worked perfectly. I had to reinstall the Windows partition, which overwrote the GRUB bootloader, so although the Ubuntu partition was intact, I could not get to it. I was reading that you can reinstall the GRUB boot loader with Boot-Repair, so I installed and ran Boot-Repair on Recommended Settings on the Ubuntu Live USB that I had originally installed Ubuntu from. Now, I can boot into Ubuntu just fine, but F2 doesn't get me into the BIOS like it used to, and I see no option to get into Windows. I was wondering why did this happen, and is there I way I can recover those options or undo what Boot-Repair did?

The paste link from the Boot-Repair job (from my Ubuntu Live USB): paste.ubuntu.com/9636870
A little more info:
/dev/sda is my main hard disk. sda1 and 2 are my windows partitions (system and C: drive). sda5 is my Ubuntu and sda6 is my swap for Ubuntu.
/dev/sdb is just more storage for my windows
/dev/sdc was the flash drive that I was running Ubuntu Live from.

The paste link from BootInfo from the Ubuntu on my hard drive afterwards: paste.ubuntu.com/9636922

If anyone could help me understand what happened and how to fix it, I would greatly appreciate it! Thanks!

---

### Post by grahammechanical on 2014-12-28
This I think is the reason why Boot Repair could restore the Grub boot menu with Ubuntu listed but not Windows 8.

> The disk contains an unclean file system [COLOR=#666666]([/COLOR]0, 0[COLOR=#666666])[/COLOR].
Metadata kept in Windows cache, refused to mount.
Failed to mount [COLOR=#BB4444]'/dev/sda1'[/COLOR]: Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully [COLOR=#666666]([/COLOR]no hibernation or fast restarting[COLOR=#666666])[/COLOR], or mount the volume
[COLOR=#AA22FF]read[/COLOR]-only with the [COLOR=#BB4444]'ro'[/COLOR] mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda1 /mnt/boot-sav/sda1

> 1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown [COLOR=#AA22FF]type [/COLOR]OS.

mount: /dev/sdc2 already mounted or /mnt/boot-sav/sdc2 busy
mount /dev/sdc2 : Error code 32
mount -r /dev/sdc2 /mnt/boot-sav/sdc2
mount: /dev/sdc2 already mounted or /mnt/boot-sav/sdc2 busy
mount -r /dev/sdc2 : Error code 32
Windows not detected by os-prober on sda2.

You could try loading into Ubuntu and running

```
sudo update-grub
sudo grub-install /dev/sda
```

Watch the printout and see if Windows 8 is detected. Do this after Windows 8 has been shut down and not put in hibernation. Microsoft gets Windows 8 to boot fast by not shutting it down and only hibernating it.

Regards.

---

### Post by sseritan on 2014-12-28
After completely shutting down the computer and running update-grub, it did find Windows 8! Then the grub-installed worked perfectly.

Thanks so much! :)

---

### Post by oldfred on 2014-12-28
Grub only boots working Windows and will not mount Windows that is hibernated to prevent damage that could not be recovered from since hibernated. And if it cannot mount it, it cannot find the Windows boot files.

You may have to use Boot-Repair's advanced mode and install a Windows boot loader to the MBR, boot Windows and shutdown without fast boot on. Then reinstall grub to MBR. Then grub's os-prober which is part of the update-grub should be able to find it.

       WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked 

And since Windows can get in trouble you need a Windows repair CD or flash drive.
      
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

