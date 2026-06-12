---
title: "Installing Ubuntu On Separate Hard Disk"
date: 2015-03-18
forum: Installation &amp; Upgrades
---

### Post by 11ryanc on 2015-03-18
I have 2 drives on my current setup. Both are 2 TB SATA devices, one from Western Digital, other Seagate. Windows is already setup on the WD, and I'd like to install Ubuntu 14.04 LTS (Xubuntu) on the other device. Now I've dualbooted before via partitions. I know how GRUB works and such. But I do NOT want Linux to in any way modify the opposing hard disk.
So the question is, how would I install Xubuntu onto this drive? Will it any way impact the other devices bootloader, or otherwise any settings? I select either via BIOS to start. Must I uninstall the Windows drive before doing this? Also, in regards to installation. I have an identical Windows install already present on there. I'm fine wiping it in place for Linux. What do I select for installation options?
Finally, on the live USB media I created, I cannot enable my full display size. Being 1920 x 1080. How would I go about installing Catalyst Control? I did it once via command in Manjaro Arch once, not sure about Buntu.

Specs:
-AMD A8 6600k
-Radeon R7 240 (Crossfire)
-ASUS A55BM-PLUS
-8 gigs

Would appreciate any insight, thanks

---

### Post by kerry_s on 2015-03-19
go into "something else" when setting up, just below where you setup your partition you'll see where you want grub installed, select the other drive there. then just boot that drive when booting, on my device i press escape, but it could be f12, f2, i'm sure you know how to access your boot menu.

---

### Post by sudodus on 2015-03-19
*kerry_s*'s method works, but if you want to be sure, that you will not touch Windows by mistake, please remove the HDD with Windows before you install Xubuntu.

- Is Windows installed in UEFI mode? In that case I suggest that you install Xubuntu in UEFI mode too. It will make it easier to switch between the two operating systems.

[https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

- You may want a data partition to be accessed from Xubuntu and Windows. In that case make it with the NTFS file system and give it the label **data**.

---

### Post by oldfred on 2015-03-19
Also if you have two Windows installs, you actually are only booting thru one of them. All boot files for all installs of Windows are in the NTFS partition with the boot flag on the drive in BIOS set as boot.

Only with Something Else install option do you get a choice which drive boot loader is intalled into. If installing to sdb drive, then you must change to that drive on the manual partitioning screen.
Many suggest to newer users that are willing to open case and disconnect drive to do that. Then you know each is installed separately. 

Make good backups of the Windows, and if UEFI the efi partition. Grub will install to that even if you specify a different drive. But it does not overwrite any Windows boot files in efi partition. But if BIOS it will overwrite a Windows boot in MBR.
Best to have a Windows repairCD or flash drive so you can repair Windows if not totally configured correctly after install. Only a few Windows repairs can be made with Linux tools. 

       [URL="http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html"]http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html
[/URL][URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
      [/URL][http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

       Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

            Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)

    
    [URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

[URL="http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html"]
[/URL]

---

### Post by 11ryanc on 2015-03-19
No UEFI here, I had this machine custom built. Partially for that purpose actually. The BIOS remembers the last used disk whenever I boot, so it's easy to select. Only 1 install of Windows is present on the WD.
So I start the installer, and go to something else? Will I need to adjust partition settings manually? Or will Linux just overtake said drive with a click?

---

### Post by oldfred on 2015-03-19
Something Else is totally manual. All the auto install options install grub2's boot loader to whatever drive is sda which usually is a Windows drive. That can be fixed, but better not to have it wrong at beginning.

See example of Something Else. You have to create/select partition for / (root) usually format as ext4 and partition for swap. Often users with a large drive have system work better if they use a smaller / of 25GB and then either /home as a partition and/or data partition(s). If dual booting with Windows a NTFS data partition is often suggested. I had both NTFS & Linux formats for data partitions when I had XP on another drive. But now without Windows the NTFS partition has been retired.

---

