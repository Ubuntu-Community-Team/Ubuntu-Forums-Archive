---
title: "Ubuntu doesn't detect Windows"
date: 2015-09-02
forum: Installation &amp; Upgrades
---

### Post by superpokes on 2015-09-02
I tried to install ubuntu alongside my w10 installation, but I don't get the option in the installer, it says it is not detecting any operating systems.
While messing on the "try ubuntu before installing" thing, I noticed I wasn't able to access neither my SSD nor my HDD. When I click on the SSD (where Windows is installed) from the "files" app, I get this error
> Unable to access "119 GB Volume"

Error mounting /dev/sda4 at /media/ubuntu/96D823FBD823D7EF: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sda4" "/media/ubuntu/96D823FBD823D7EF"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.


Same for my HDD

I attached below a screenshot of my SSD partitions in gparted
[ATTACH=CONFIG]264175[/ATTACH]

thanks for your attention

---

### Post by yancek on 2015-09-02
Windows 8 and later always have 'hibernate' on.  You need to turn it off as explicity explained in the error message.  Anything to do with 'fast boot'.  This varies with manufacturer so you'll have to get into BIOS setup and take a look or post the manufacturer name and someone familiar with it might be able to tell you how to do it.

You also do not have anywhere to install Ubuntu on your hard drive as the space is taken up by your various windows partitions.  You can resize/shrink the main windows partition from the Disk Management tool in windows to about half the current size and use that unallocated space to install Ubuntu.

The second partition on your drive is FAT32 which might be an EFI partition or boot partition.  If it is EFI, then you need to install Ubuntu using EFI or you will have problems.

Ubuntu does detect windows in GParted as all your partitions are windows filesystems.  You probably need to use the manual install option which is referred to as "Something Else" but the reason you don't see it in the installer is because there is no space on which to install Ubuntu.  After reading through your post, I notice that you mention a second drive but provide no information on it.  Where are you planning to install Ubuntu, the SSD with windows or the other drive?

---

### Post by Bucky Ball on 2015-09-02
Welcome. As above. You need to boot into Windows to switch off hibernation and fastboot then boot to the BIOS and switch of secureboot then try again.

When you get to the partitioning section of the install it is best to choose 'Something Else' and partition manually to ensure your Win partitions are not overwritten. We can help with that. 

You are free to 'Install alongside' but it can be problematic. If Ubuntu doesn't see your Win partition, STOP, as you have, which is good. 

It goes without saying that you should have good backups before proceeding, so I won't say it. :D

*** Ok, just looked at your screen shot. Further to what yancek suggests, sda2 is the Win EFI boot partition. You have nowhere to install Ubuntu. You will need to boot into Windows and shrink the Win partition (sda4). DO NOT do it with Gparted from a live session with Ubuntu. Use Win.

---

### Post by superpokes on 2015-09-02
Thanks, I didn't know about windows hibernating, I will try to figure out how to turn it off

I plan on installing it on my SSD, I had shrinked the "big" Windows in my SSD but I "merged" back the unallocated space after seeing it wasn't detecting Windows because I thought I had ****ed up (but that obviously wasnt the problem)

How do I install ubuntu using EFI? What partitions do I have to make manually for this install?

Thank you again for your help

---

### Post by yancek on 2015-09-02
I don't use UEFI myself so will only suggest you read the official Ubuntu documentation on it at the link below.  You should have an option to use UEFI to install or it may be detected and you generally will have the Ubuntu EFI files installed to the already existing EFI partition.  You only need one other partition for "/", root of  the filesystem.  You can always change that later if you want.


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Bucky Ball on 2015-09-03
Partitions you need depends on what end result you are after. Have a look at [this]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352"). If you are using just / (where your OS and personal data goes) and /swap, make the / partition as big as you can and /swap 2Gb.

If you are using a separate /home partition (which is where your personal data would go) make / 20-25Gb, /home as big as you can and /swap 2Gb.

Set the EFI partition (sda2, the small 'boot', FAT partition from memory) to 'Use' but NOT to format. All other partitions apart from the one you are creating, make sure they are all set to 'Do not use' and untick the format box.

Let us know if you hit a wall or have any other questions. Good luck. :)

---

### Post by superpokes on 2015-09-03
> **Bucky Ball said:**
> Partitions you need depends on what end result you are after. Have a look at [this]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352"). If you are using just / (where your OS and personal data goes) and /swap, make the / partition as big as you can and /swap 2Gb.

If you are using a separate /home partition (which is where your personal data would go) make / 20-25Gb, /home as big as you can and /swap 2Gb.

Set the EFI partition (sda2, the small 'boot', FAT partition from memory) to 'Use' but NOT to format. All other partitions apart from the one you are creating, make sure they are all set to 'Do not use' and untick the format box.

Let us know if you hit a wall or have any other questions. Good luck. :)

I followed your instructions and got this

[ATTACH=CONFIG]264210[/ATTACH]

on the efi partition I chose "Use as: FAT32 file system" and "Mount point: /boot". I don't know if that's right or if I should choose "Use as: reserved BIOS boot area"

---

### Post by oldfred on 2015-09-04
Neither.

The /boot is not normally suggested with desktop installs. That is where most of grub and kernels are installed.
The bios_grub partition must be unformatted and is only used if BIOS booting on a gpt partitioned drive. It usually is just 1 or 2 MB for a small part of grub (core.img). If system is asking for a bios_grub you must have booted installer in BIOS mode not UEFI mode. How you boot installer is then how it installs. Reboot and install in UEFI mode.

You should not need to mount the ESP - efi system partition and you can only have one per device. That is the location where the boot loader part of grub is installed. It is more equivalent to the MBR in BIOS boot systems and the core.img part in BIOS boot.

But when you install in UEFI mode, and manually partition you choose the drive like sda on where to install the grub2 boot loader, not any partition in the combo box at the bottom of the partitioning screen. With UEFI system know to install boot files into the ESP.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[URL="http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported"]http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported
[/URL]
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

[URL="http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported"]
[/URL]

---

### Post by Mark Phelps on 2015-09-04
FastStartup is NOT the same as Fast Boot and disabling it in Win10 is done as follows:
1) Get to Control Panel
2) Open Power settings
3) Click on the option to change what the buttons do
4) At the top of the window there's and entry about showing other options, click that
5) Down near the bottom of the window, there's a check box for FastStartup. Uncheck it
6) OK your way all the way out
7) Reboot Win10

At this point, FastStartup is disabled and you should then be able to see your Windows partitions.

---

