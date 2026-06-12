---
title: "Missing windows XP boot file"
date: 2015-11-11
forum: Installation &amp; Upgrades
---

### Post by alby3 on 2015-11-11
I installed windows xp in addition to xubuntu and windows 7 that was already working in dual boot, after the installation I had to reinstall grub but when I did windows 7 and xubuntu was showing in the boot selection but xp was missing I already tried boot-repair and that's the log: [http://paste.ubuntu.com/13231602/](http://paste.ubuntu.com/13231602/)

---

### Post by yancek on 2015-11-11
So you can boot windows 7 and Xubuntu, correct?  Did you look at the grub.cfg file in the boot repair output?  There is no entry for xp, just for windows 7 and Xubuntu.
Installing xp after windows 7 was a bad idea.  Windows bootloaders are backward compatible so if you had xp and then installed windows 7, the windows 7 would detect xp and you would see it on your menu.   Getting xp to boot windows 7 will involve modifying various boot files manually and booting win 7 from xp, I would suggest you go to a windows forums to look for help.  xp and win 7 have different boot files and you seem to have a mix of the two on the xp partition.  When you chainload to win 7 from Xubuntu, do you see multiple options on the windows menu?

You might try running:  sudo update-grub from Xubuntu and see if you get a positive result, otherwise try a windows forum as this is a windows issue and I doubt boot repair will be able to resolve it.  And you do not have a missing xp boot file, the necessary files are all there.

---

### Post by oldfred on 2015-11-11
Windows only installs boot files to the primary NTFS partition with the boot flag. Since you have the sda1 as Windows 7's boot partition with the boot flag, your XP install added its boot files to sda1.

Does Windows 7 boot or XP? In the NTFS partition with the boot flag is the partition boot sector. And the boot sector has additional boot code including partition size and whether to use ntldr (XP) or bootmgr. Bootmgr is for all BIOS based installs after XP.

You may just need to move XP boot files from sda1 to sda3.
If Windows 7 does not now boot XP the other alternative is to update its BCD with an entry for XP. Normally installing 7 after XP would add that entry automatically. You would have to check on a Windows forum for details of a BCD entry.

       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)

Moving boot files to sda3 will let grub find XP as a separate boot, but then BCD will not boot it. If moving boot files does not work, then you have to update partition boot sector in sda3 with the info it needs to boot with ntldr.


 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR

You show both of these in sda1:

 Windows BIOS Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7/8 (with 7or 8 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

---

