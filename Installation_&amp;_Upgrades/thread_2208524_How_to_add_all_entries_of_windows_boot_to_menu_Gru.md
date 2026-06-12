---
title: "How to add all entries of windows boot to menu Grub2?"
date: 2014-02-28
forum: Installation &amp; Upgrades
---

### Post by eriic504 on 2014-02-28
My menu grub2:
    [IMG]http://i438.photobucket.com/albums/qq104/eriic504/grub2-1.jpg[/IMG]
    This is my screen after windows loader is selected: 
    [IMG]http://i438.photobucket.com/albums/qq104/eriic504/winboot.jpg[/IMG]
I want to merge all windows boot items (windows 7, windows 8.1 and Ghost program) to Grub2. Please tell me how.

---

### Post by bedfordd on 2014-02-28
did you see [http://askubuntu.com/questions/135272/how-to-boot-into-windows-7-when-grub-is-installed-in-the-windows-partition](http://askubuntu.com/questions/135272/how-to-boot-into-windows-7-when-grub-is-installed-in-the-windows-partition) ?

Mucking around w/ Grub / MBR is not to be taken lightly... Not sure how you get to the other Windows boot options...

---

### Post by Mark Phelps on 2014-03-01
This is an extremely difficult thing to do -- because GRUB basically hands over control to the Windows boot loader in the partition identified in the grub.cfg file.  The Windows loader then takes it from there, puts up the OS selection screen, and handles the rest.

The process involves hand-building individual boot stanzas for each of the options.  This is hard, in and of itself.  Problem is, once you do that, every time you then do an update that changes the kernel version, your grub.cfg file gets overwritten and you have to go back and reapply the customizing you did.  

Plus -- Windows 8 has changed the boot process such that whenever you select an option other than Windows 8, it basically forces a complete cold restart.  As far as I know, there is no way around this. In the end, with the forced reboot, I wasn't saving any time and got fed up with having to maintain it.

I believe that "oldfred" may have the details on how to get this working.  My suggestion is that you leave well enough alone until he responds.

---

### Post by oldfred on 2014-03-01
I do not know any of the new issues with Windows 8. And what is ghost?

But all Windows installed in BIOS mode boot from MBR, then PBR and BCD of only the one primary NTFS partition with the boot flag. All other installs of Windows move/copy boot files from their partition to the boot flag or active partition. So grub does not find any other bootable install of Windows.

If your other Windows installs are in primary partitions you can move boot flag to second install, and run Windows repairs to make that partition bootable. 

Then grub can find second install's boot files and have both in grub menu. Grub does not use boot flag, and just chain loads to PBR or partition boot sector of the Windows install.

If other Windows installs are not primary it is just about impossible to boot directly. Windows will not run repairs to make a logical partition bootable. It can be done if XP is in logical partition, but not sure about newer Windows.

       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)
BIOS/Grub/Ubuntu  boot process
[http://www.thegeekstuff.com/2011/02/linux-boot-process/](http://www.thegeekstuff.com/2011/02/linux-boot-process/)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by eriic504 on 2014-03-03
Thanks for all. This thread can be closed.

---

