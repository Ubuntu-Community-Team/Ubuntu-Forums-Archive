---
title: "Add Windows 8 to existing installation"
date: 2015-05-10
forum: Installation &amp; Upgrades
---

### Post by dave181 on 2015-05-10
Hi,

I recently discovered Ubuntu 14.04 when my laptop became too slow. I now have the choice of Ubuntu and Win7 when I boot. I'd like to try and add windows 8 and have the three OS on the same machine. Is this possible and how can I start? Thanks.

---

### Post by ramaswamyps on 2015-05-10
windows 8 loader will remove the grub if ubuntu is the primary boot loader.
carefull before committing
give more details about your system i can try and help you

---

### Post by oldfred on 2015-05-10
Most Windows 7 systems were BIOS, but a few were UEFI. Which is yours?

Windows only directly boots from a primary NTFS partition with the boot flag. A second install of Windows can be in a logical partition but all its boot files will be in the first install's partition. Then you can only boot the  one install from grub, but Windows BCD will have both Windows listed.

       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)

Also with Windows 8, you must be sure fast startup is off or its always on hibernation. And that you fully shutdown. Even if only booting two Windows without Linux you have to do that.

       
 WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast startup
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
If issues you may need these?
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked 
powercfg /h off

---

### Post by grahammechanical on 2015-05-10
I once installed Windows 8 pre-view on a machine with a BIOS motherboard. It will definitely overwrite Grub. The procedure is to create unallocated space for Windows 8 and then use the Windows 8 installer to turn the unallocated space in a a NTFS partition. Then the installer will install Windows 8 in the partition you select.

To re-install grub boot loader run a Ubuntu live session. Use the file manager to open the Ubuntu partition and then run

```
sudo grub-install /dev/sdax
sudo update-grub
```

where x is the partition that Ubuntu is in. Or use Boot Repair.

Regards.

---

