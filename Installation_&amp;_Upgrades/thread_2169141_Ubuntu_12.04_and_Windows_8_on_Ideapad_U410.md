---
title: "Ubuntu 12.04 and Windows 8 on Ideapad U410"
date: 2013-08-20
forum: Installation &amp; Upgrades
---

### Post by DWerk7E on 2013-08-20
I ve recently purchased a U410 laptop with i7, 8gb RAM, 1TB HDD, Windows 8 preinstalled with no SSD disk.

 I ve run the Disk Management tool and show to many partitions as seen in the following picture

[IMG]http://forums.lenovo.com/t5/image/serverpage/image-id/26002i4379B104E2C483F2/image-size/original?v=mpbl-1&px=-1[/IMG]

I would like to install ubuntu 12.04 on my laptop without losing Windows 8.
Since no SSD is present do I still have to use the dmraid util as  suggested in other posts?
Which is the best way to create new partitions? One for keeping my file and one for installing linux? 
I guess the best approach would be to resize the Windows8_OS  partition. Which tool would you suggest to use so I don't end up with  messed partitions?

I ve read in other posts that I will need to change my BIOS to Legacy Mode, is that true?
Should I start the installation and choose the method "Install Ubuntu alongside with Windows" ?  Will this step resize my Windows8_OS partition and leave the rest intact? What would you suggest?

---

### Post by oldfred on 2013-08-20
You do not need to run any dmraid commands to remove RAID unless somehow they implement Intel SRT on one drive.

Use Windows disk tools to shrink Windows and reboot Windows a couple to times so it can run chkdsk to recognize its new size. 
You must turn off fast boot in Windows and/or in UEFI.
Do not turn CSM/BIOS/Legacy on unless you have a system that will not boot the Ubuntu install flash drive in UEFI boot mode either with secure boot on or off.
Better to use the newest version as your have very new hardware. Some disadvantage is that then you will have to upgrade in a relatively short time, but 12.04.2 is not as current for very new systems.

Review the link in my signature for more UEFI info and particularly the first links that have screenshots on installing. You also will need Boot-Repair to fix several things.

  lenovo u310  - install to SSD
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)
> Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather than the F2 I'm used to on other computers.

---

### Post by DWerk7E on 2013-08-21
> **oldfred said:**
> You do not need to run any dmraid commands to remove RAID unless somehow they implement Intel SRT on one drive.

Use Windows disk tools to shrink Windows and reboot Windows a couple to times so it can run chkdsk to recognize its new size. 



I am thinking of using what you suggested. Shrink the Windows8_OS  partition to about 200-300 GB and have the rest as unlocated. Reboot a couple of times.
Then create a new NTFS partition which will be used as storage area on the unlocated space, reboot and shrink the new partition so I can have unlocated space for Ubuntu. 
So the new partition table is 

Recovery Partition 1GB
EFI Partition 260 MB,
OEM Partition 1GB,
Windows 8 Partition 200GB,
Storage Partition 630 GB,
Ubuntu Partition 34GB,
Lenovo Partition 25 GB,
Recovery Partition 20GB

What do you think? Will this work or I might face problems?

> **oldfred said:**
> 
You must turn off fast boot in Windows and/or in UEFI.
Do not turn CSM/BIOS/Legacy on unless you have a system that will not boot the Ubuntu install flash drive in UEFI boot mode either with secure boot on or off.
Better to use the newest version as your have very new hardware. Some disadvantage is that then you will have to upgrade in a relatively short time, but 12.04.2 is not as current for very new systems.

Review the link in my signature for more UEFI info and particularly the first links that have screenshots on installing. You also will need Boot-Repair to fix several things.

  lenovo u310  - install to SSD
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)


Once I finish with partitioning I will boot from my usb flash drive to install Ubuntu.
I guess since I will be using the partition table I ve posted above I should now pick the "Do something else" method and format the Ubuntu partition, right?
When should I run boot-repair? After installation is finished and I reboot again to the LIVE USB ?
Doing what is suggested here ?


[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)

What should I be extra careful for so I don't end up with my Windows useless ?

---

### Post by oldfred on 2013-08-21
That partitioning will work. But you do not have much room for data in the Linux root partition. That is how I configure my system with 25GB / (root) partition and use about 9GB including my /home which is 2GB and mostly .wine for Picasa. But I am aggressive in moving some hidden folders with data like Firefox & Thunderbird to my NTFS data partition so I could use the same email & bookmarks in both systems. Since I have stopped using Windows all my new data goes into the Linux formatted data partition. But I still have not moved my data out of my NTFS data partition. 

Always best to boot installer and Boot-Repair in UEFI mode if at all possible. Its just some systems seem to not let you or users do not know the combinations of settings in UEFI. UEFI is more complex than the old BIOS and many did not understand BIOS.

After install add Boot-Repair to installer (you have to do that every time you reboot installer) or use the remix from the Boot-Repair site that is both an installer but has Boot-Repair built in.

       Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by DWerk7E on 2013-08-21
Where should I put the boot loader on
1) /dev/sda 
or
2) on /dev/sda5 Windows 8 (loader)

---

### Post by oldfred on 2013-08-21
Never on a NTFS partition as that has to have Windows boot code. We filed a bug years ago, as grub nor installer should not even offer that choice.

With UEFI you install grub2's boot loader to the efi partition. I think if you just say sda with UEFI it defaults to the efi partition. Then from UEFI menu it will show all the boot options it finds in the efi partition. Each folder is a different system.

With BIOS you always install to the MBR or sda if first drive, as MBR is the choice for BIOS  to boot. Although with multiple drives you can set other drives in BIOS to boot from.

---

### Post by DWerk7E on 2013-08-21
Finally I was able to have a working system.
When I finished install I was getting a warning *"image failed to verify with **ACCESS DENIED**.."* and Windows 8 was loading OK but no indication for Ubuntu.
I run boot-repair and reboot but now while grub menu was loading neither Ubuntu nor Windows were loading.
I entered BIOS and changed to Legacy Mode and Ubuntu started loading.

On my /boot/grub/grb.cfg I had the following windows entries 

"Windows UEFI recovery bootmgfw.efi"
"Windows Boot UEFI recovery" 
"Windows UEFI recovery LrsBootmgr.efi"
"Windows Boot UEFI recovery bkpbootx64.efi" 
"Windows Recovery Environment (loader) (on /dev/sda3)"
"Windows 8 (loader) (on /dev/sda5)" 

Last one *"Windows 8 (loader) (on /dev/sda5)"* which should be the one to load my Windows was not working and the only one that did work was *"Windows UEFI recovery bootmgfw.efi"*

---

### Post by oldfred on 2013-08-21
No the entries for sda5 and sda3 are BIOS entries and a bug in grub2's os-prober. The others are from Boot-Repair and should work, but the first should not say recovery.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

---

### Post by DWerk7E on 2013-08-22
Thank you for all your replies.

Although Ubuntu has been loading ok today it seems that it fails to load.
When I choose to load it I only get a black screen. Windows are loading without a problem.
I tried using the Ubuntu recovery mode on grub menu which starts and gives a menu where I pick the normal startup which freezes after a point.
How can I identify what is the problem? Can I get a more verbose output during Ubuntu loading just for debugging?
I guess some Ubuntu update or software installation messed it up.

---

### Post by oldfred on 2013-08-22
What video card/chip?

The recovery mode automatically uses nomodeset as a default. Normally  on first boot you install the proprietary drivers if nVidia or AMD. 

Intel is supposed to just work as it only has one open source driver. But some need extra boot parameters and Intel has made a lot of recent changes for new Haswell processors that have improved older one as well. But you often need the newest Ubuntu or may need to install from Intel which may also need the very newest kernel.

---

### Post by DWerk7E on 2013-08-22
It now seems to be working.
I ve loaded up the LIVE usb chrooted to my Ubuntu installation and removed the lm-sensors package since this was the last installed, but I don't think this as something to do with it.

While using the recovery mode and then normal boot it was freezing in the following screen
[[IMG]http://s23.postimg.org/6fofn3ayv/DSC00305.jpg[/IMG]]("http://postimg.org/image/6fofn3ayv/")

---

### Post by oldfred on 2013-08-22
One user recently reported issues with lightdm and went back to gdm. But I do not know details.

---

### Post by DWerk7E on 2013-08-22
I know I ve read about it.
It's really strange though. One moment not working and then working. It's so not Linux ;-)

---

