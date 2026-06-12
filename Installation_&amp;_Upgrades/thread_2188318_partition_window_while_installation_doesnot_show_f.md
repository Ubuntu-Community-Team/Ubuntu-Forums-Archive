---
title: "partition window while installation doesnot show free space on my secondary drive"
date: 2013-11-16
forum: Installation &amp; Upgrades
---

### Post by neeraj.sarvan on 2013-11-16
i was trying to install ubuntu on my hp laptop alongside windows 8 by booting from a usb drive . while installing partition manager shows just 1 MB OF free space on my secondary drive(say D) in which i want to install ubuntu. how to solve this to proceed with patition ?

---

### Post by oldfred on 2013-11-16
Was Windows 8 pre-installed and using gpt partitioning & UEFI boot, or your install with MBR partitioning and BIOS boot?
Post this from live version of Ubuntu:
sudo parted -l

Use Windows to shrink its partition, but do not create new partitions with Windows. 
And make sure fast boot is off. If UEFI also turn off secure boot.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by neeraj.sarvan on 2013-11-17
yeah i have pre installed windows 8 and ya i was using UEFI boot...

---

### Post by oldfred on 2013-11-17
Important links on installing instructions.
 Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

More info in link in my signature.

---

### Post by neeraj.sarvan on 2013-11-19
thanx for the help successfully installed ubuntu but now the prob is win 8 starts automatically when i start my computer. what if i need to use ubuntu. plz help

---

### Post by oldfred on 2013-11-19
Go into UEFI and select to boot the ubuntu entry.
You should also be able to select that then as the first boot entry so it boots as default.

---

