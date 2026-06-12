---
title: "Lost Windows 8 Bootloader"
date: 2014-01-25
forum: Installation &amp; Upgrades
---

### Post by haveguitarwilltravel on 2014-01-25
Hello, I may have ummm installed Grub on the windows 8 bootloader.. so I can't get back into Windows.. which I wouldn't really mind that much because I just need to put some pictures on an SD card for my girlfriend, but when I try to access my windows files from Ubuntu I get this error > Error mounting /dev/sda4 at /media/tacorhoads/3630B01030AFD4E1: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda4" "/media/tacorhoads/3630B01030AFD4E1"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.



I would prefer access to my Windows again, but if the at the least I just really need to access the filesystem to transfer some pictures over before my gf gives me the "I told you so" because I should've never transferred the darn pictures from the SD card in the first place... haha any suggestions how to mount the drive or fix the bootloader?

Mucho Gracias,
haveguitarwilltravel

---

### Post by The Cog on 2014-01-25
Grub can often find the windows bootloader. As a first step, I would try running this command to re-scan the disk, and then rebooting to see if windows then appears in the grub boot menu:
```
sudo update-grub
```

---

### Post by haveguitarwilltravel on 2014-01-25
Well Windows 8 is listed as an option in grub but when I select it it takes me back to the grub menu as if it just were refreshing the page, I presume because I installed windows on the windows 8 bootloader, any ideas?

---

### Post by ajgreeny on 2014-01-25
Was windows shut down properly when you installed Ubuntu and/or grub on the machine.  Win 8 by default shuts down to a form of hibernation which can cause problems when dual booting, and as the error messages say
 > The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option. my guess would be that you did not shutdown the windows OS fully, hence Ubuntu and grub think it is still in use.

I don't like pointing you to a search page but there are so many references to this problem and I don't have time to research them all, so I'm afraid I am going to tell you to look at the page here and see if you can find an answer.
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=windows+8+hybrid+shutdown+problems&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=windows+8+hybrid+shutdown+problems&as_qdr=all&sa=Google+Search&lang=en)

Very good luck.

---

### Post by haveguitarwilltravel on 2014-01-25
Thanks for the reply ajgreeny, I was actually able to partially solve my issue (well the retrieving files part) I could mount the drive in read-only state by opening a terminal and firing up > sudo mount -o ro /dev/sda4 /mnt sda4 being the name of my specific partition for anyone reading this in my situation.. now the next step is figuring out how to boot into windows, if anyone has any ideas let me know.. I'll keep researching. :D

---

### Post by oldfred on 2014-01-25
WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

Do not know how safe any of this is. Usually better to use Windows repair flash drive.
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)
User who fixed Windows 8
[http://ubuntuforums.org/showthread.php?t=2171156s](http://ubuntuforums.org/showthread.php?t=2171156s)

---

### Post by haveguitarwilltravel on 2014-01-25
Thanks for the reply oldfred, however none of that information is quite what I'm looking for, unless I'm just not comprehending it all correctly.. just to reiterate what happened was I went to install Ubuntu, and on the partition editor menu I chose to install grub on the "windows 8 bootloader" using the dropdown menu at the bottom of the partition editor, versus just installing on my hdd that it had pre-selected for me.. so in doing that grub loads up fine and gives me an option to boot windows 8 but when I select to boot windows 8, no error, no nothing, it just refreshes the grub menu so to speak, any information on fixing this would be much appreciated.

Sincerely,
haveguitarwilltravel

---

### Post by oldfred on 2014-01-25
You never install grub into a Windows partition as that breaks Windows. Windows has to have its boot code in the PBR or partition boot sector of its NTFS partition.

To confirm what is where.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[sehttps://help.ubuntu.com/community/Boot-Info](sehttps://help.ubuntu.com/community/Boot-Info)

I would like to be sure this is the issue, but if you want to read ahead or know that this is the issue.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

