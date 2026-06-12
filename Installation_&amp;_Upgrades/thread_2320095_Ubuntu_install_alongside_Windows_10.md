---
title: "Ubuntu install alongside Windows 10"
date: 2016-04-10
forum: Installation &amp; Upgrades
---

### Post by barryrobinholt2013 on 2016-04-10
Hi, I'm trying to install Ubuntu 14.04.4 alongside Windows 10.  I installed via my Ubuntu USB.  Now the only way that I can boot into Windows 10 is selecting Recover or maintain your system as shown in my pictures.  Once I click this, it repairs my disk then starts Windows 10 but I cannot get Ubuntu back unless I recover via my boot repair disk USB.  Once I run from my repair disk, it shows the screen in my pictures that has a list going--
Ubuntu
Advanced options for Ubuntu
Windows UEFI bootmgfw.efi
.....
.....
When I click one of the Windows boot options, it says cannot load image as shown in my pictures.

While in Windows 10, when I go to advanced startup settings to select which operating system to boot, only Windows 10 is shown.  

I want it so that when I press the power button I have the 2 options of Ubuntu or Windows 10.

Please any help is appreciated, I have been working on this since early yesterday.

Barry

---

### Post by grahammechanical on 2016-04-10
You have not included the URL to the pastebin site so that we can examine the BootInfo summary that Boot Repair provides. Some of us are able to make sense (a little) out of all the information in the Boot Repair summary report.

Nor have you provided details of your hardware. Some manufacturers do not completely comply with the UEFI specification so that even if we install Ubuntu in EFI mode just as Windows 10 is installed in EFI mode we still do not get a Grub boot menu allowing us to select either Windows 10 or Ubuntu. Your machine could be one of those machines.

Regards.

---

### Post by barryrobinholt2013 on 2016-04-10
[http://paste.ubuntu.com/15737730/](http://paste.ubuntu.com/15737730/)

When I tried to install Ubuntu again just now it shows that it is installed but it's not showing up when I boot.  System info attached.

---

### Post by oldfred on 2016-04-10
It says Sony which is one that does not comply with UEFI standard. It uses description to boot and only valid description is "Windows Boot Manager".
Boot repair should have copied shimx64.efi into /EFI/Boot as bootx64.efi. That is a fallback or default hard drive boot entry that should still work. Ubuntu entry will not.

But you also show Windows hibernated, so you cannot boot Windows from grub, not see Windows partition(s) from Ubuntu.
       Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)
More explanation of NTFS driver & Windows hibernation
[URL="http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation"]http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation

[/URL]
  Sony Vaio Pro 13 - To get into  UEFI press this "Assist" button BEFORE starting
[http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio](http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio)
[http://askubuntu.com/questions/644901/booting-a-sony-vaio-computer-running-windows-8-1-in-ubuntu-from-a-usb-drive](http://askubuntu.com/questions/644901/booting-a-sony-vaio-computer-running-windows-8-1-in-ubuntu-from-a-usb-drive)
Issues on rename
[https://bugs.launchpad.net/boot-repair/+bug/1315490](https://bugs.launchpad.net/boot-repair/+bug/1315490) 

[       ]("http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation")
 One Sony user, dual booting, and boot hard drive UEFI entry, not ubuntu
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589) 

    
You may find suggestions on renaming Windows efi boot file. That is old and not required. Many posts have you manually copying Shim to bootx64.efi including instructions in my signature below, but now Boot-Repair should be automatically copying it.

---

### Post by barryrobinholt2013 on 2016-04-11
Thank  you for your reply, I tried about everything that I looked up in forums and got frustrated so I'm gong to leave it for now.  If I want a dual boot system then I will buy a compatible one, Sony makes it difficult.

---

### Post by oldfred on 2016-04-11
Many make it some what difficult.
The work arounds are not all that difficult now that Boot-Repair copies shimx64.efi to bootx64.efi for the fallback boot.

---

