---
title: "Problem installing Dualboot (Win7/Ubuntu 12.04) - No bootloader"
date: 2012-10-14
forum: Installation &amp; Upgrades
---

### Post by dk88x on 2012-10-14
I have the following problem.

1. I install Win 7 without any errors.
2. I install Ubuntu (Install Ubuntu alongside Windows 7) without any errors.
3. Reboot
4. Dos screen and then a black screen - No boot loader or error message of any kind...

What can I do? I tried re-installing grub multiple times and also boot-repair. No solution...

I just re-installed my whole system, so as of now I have an untouched system after only installing Win 7 and Ubuntu.

Can anybody help me, please?

Thank you very much!

---

### Post by dk88x on 2012-10-14
With boot-repair I just set the boot flag to Win 7, so I was successfully able to boot up and use Windows. Any idea how to fix Ubuntu and/or the boot loader?

---

### Post by oldfred on 2012-10-14
Welcome to the forums.

With two systems you should get grub menu, but it may be a video issue. Lets look at how your system is configured. Please post the link that creating BootInfo from Boot-Repair creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by dk88x on 2012-10-14
Thanks for your reply.

Here is my Boot Info link:

[http://paste.debian.net/200379](http://paste.debian.net/200379)

---

### Post by oldfred on 2012-10-14
You have grub installed to the PBR not the MBR. The boot loader has to be in the MBR or sda not a partition's boot sector or sda7.

Grub can be in a PBR but is not recommended and Windows is not normally able to boot Linux.

You can use Boot-Repair to install grub2's boot loader to the MBR or sda.

If you have moved boot flag and are in Ubuntu you can easily install grub to sda.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

But move Boot flag back to sda1 or sda2. Windows uses boot flag to know which partition's boot sector or PBR to find more boot code. Windows only boots from, repairs boot, or installs to a NTFS formated primary partition with the boot flag. Grub does not use boot flag and will boot or chainload to any Windows partition with boot files.

You should have Windows repairCD also.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by dk88x on 2012-10-14
I moved the boot flag back to Ubuntu and got the above mentioned black screen again.

[http://paste.debian.net/200418](http://paste.debian.net/200418)

---

### Post by oldfred on 2012-10-14
Boot script looks ok. If Windows boots from grub menu then booting thru grub is ok and it is probably a video issue or other boot paramter.

Have you tried adding nomodeset to the Linux line in grub? What video card/chip do you have.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I have nVidia and have to use nomodeset on first boot. The newest installer has options to include proprietary drivers that eliminates the need for nomodeset. But once I install the nVidia driver from the Ubuntu pop-up, I have no issues. 
Not sure about other video systems.

---

### Post by dk88x on 2012-10-15
I've just added nomodeset with boot-repair, but nothing changed. 

When installing or booting from live cd, I always add nomodeset, because otherwise the resolution will bet set at 640x350.

I also think there is a problem with grub. The grub menu is never shown in bios, and even when I press the Shift button - as suggested in the tutorial - no grub menu is opened...

---

### Post by oldfred on 2012-10-15
Are you pressing & holding shift key from BIOS screen? Some say press many times, but just once does not work.

Grub remembers key strokes before menu appears. Second line is recovery mode so one down arrow should give recovery mode. Press down arrow key once from BIOS and see if you boot from recovery mode.

---

