---
title: "Specific Situation regarding Windows 10 Installation and Multiple HDs"
date: 2015-06-25
forum: Installation &amp; Upgrades
---

### Post by drewmcarthur1 on 2015-06-25
I currently run Ubuntu 15.04 on a desktop I built from parts, on a 500gb SSD.  I recently scavenged a 250gb HDD from an old laptop, and have since put that into the computer.  With the new Windows 10 releases for free, I'd like to put that on my computer, to dual boot it with ubuntu.  

I have two options in mind.  One being to format the HDD, and put Windows on that, don't touch the SSD.  This would be easy, I assume I'd format the HDD to NTFS, right?

Another option would be to move backups to the HDD, shrink the SSD's partition and create another, (format that NTFS?) and put Windows on that.  So the SSD would be half Ext4/Ubuntu and half NTFS/Windows, and the HDD would be data/backups.  In this case, would I format the HDD NTFS for Windows compatibility? Or would it be a better idea to also split the HDD into two partitions and give them separate file systems, for performance reasons?  

Which option is better? Is the effort put into changing around partitions and formatting of the latter worth the performance boost from putting Windows on the SSD?

With these different partitions, is there a loss in performance if I were to mount them automatically, if so, how would I make sure that the other partitions aren't mounted until I want them to be?

I've got burg set up now so it looks nice, (almost), but as I understand it, installing Windows will overwrite this somehow.  Could someone direct me towards a blog post or something similar that will walk me through reversing Windows stomping of my bootloader? 

Speaking of my bootloader, I also had a question with having the menu hidden.  Currently, it is hidden, and I don't want it to show unless I press and hold a button.  Right now, i have to press ESC repeatedly, I'd prefer to be able to just press and hold ESC and have burg show up.  Any tips? Here's my burg config:

```
# If you change this file, run 'update-burg' afterwards to update# /boot/burg/burg.cfg.


GRUB_DEFAULT="0"
GRUB_TIMEOUT="0"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"


# If you want to enable the save default function, uncomment the following
# line, and set GRUB_DEFAULT to saved.
#GRUB_SAVEDEFAULT="true"


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
# In the boot menu, use hotkey 'r' to popup a resolution selection menu.
GRUB_GFXMODE="1280x1024"


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


# GRUB_THEME's value can be 'saved' or a specific BURG theme name, you can also
# set it to the pathname of a GRUB2 theme file.
# In the boot menu, use hotkey 't' to popup a theme selection menu
GRUB_THEME="saved"


# GRUB_FOLD's value can be 'saved', 'true' or 'false'.
# In the boot menu, use hotkey 'F7' to show the full list, 'f' to toggle
# between folding modes.
GRUB_FOLD="saved"


# Add user with burg-adduser, then use GRUB_USERS to config authentication.
# The following example means user1 can boot Ubuntu, no password is needed to
# boot Windows, user1 amd user2 can boot other OS. Superusers can boot any OS
# and use hotkeys like `c' to enter console mode.
#GRUB_USERS="*=user1,user2:ubuntu=user1:windows="


# For a complete list of supported variables, refer to this wiki page:
# http://code.google.com/p/burg/wiki/ConfigurationVariables


#GRUB_HIDDEN_TIMEOUT="1"
#GRUB_DISABLE_OS_PROBER="false"

```

---

### Post by oldfred on 2015-06-25
If a new system is it UEFI or BIOS.
I think burg is only BIOS, but do not know burg. I do not think burg has been maintained for years.

With two drives you have two MBRs, so you can have Windows in one MBR and grub in the other MBR if you are booting in BIOS.

You do have to be sure that both systems are installed in the same boot mode, either both BIOS or both UEFI.

Many suggest disconnecting the other drive when installing to another drive to avoid issues. Grub can then find Windows to add to its boot menu. Again not sure about burg.

Post this:
sudo parted -l

Your shared data partition, should be NTFS. But With newer versions of Windows you must turn off fast startup or you will have issues whether UEFI or BIOS.

 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

 Windows 10 Dual boot on Toshiba works - sudodus
[http://ubuntuforums.org/showthread.php?t=2246751&p=13137869#post13137869](http://ubuntuforums.org/showthread.php?t=2246751&p=13137869#post13137869)
[http://www.microsoft.com/en-us/windows/windows-10-specifications](http://www.microsoft.com/en-us/windows/windows-10-specifications)

If BIOS boot:

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by drewmcarthur1 on 2015-06-25
Burg currently works, and is installed on sda(SSD).  it was able to detect and boot windows xp from sdb(HDD), although the OS was corrupted, it was still able to begin booting, the corruption has nothing to do with the current situation as it is an old drive.  This, and the fact that the MoBo has a bios menu convinces me that this is bios, and not uefi.  I've decided to install Windows 10 on the HDD, rather than fooling with partitioning.  I won't be using Windows enough for the performance to be all that different.

Here's the output to ```
sudo parted -l
```

```
Model: ATA Crucial_CT480M50 (scsi)Disk /dev/sda: 480GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  472GB  472GB   primary   ext4            boot
 2      472GB   480GB  8534MB  extended
 5      472GB   480GB  8534MB  logical   linux-swap(v1)




Model: ATA WDC WD2500BJKT-7 (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End    Size   Type     File system  Flags
 1      1049kB  250GB  250GB  primary  ntfs




Model: SanDisk Cruzer Blade (scsi)
Disk /dev/sdc: 4022MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  4022MB  4021MB  primary  fat32        boot, lba




Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: HP DVD Writer 1270e (scsi)                                         
Disk /dev/sr0: 742MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac
Disk Flags: 


Number  Start  End    Size    File system  Name   Flags
 1      2048B  6143B  4096B                Apple
 2      737MB  740MB  2228kB               EFI



```

---

### Post by oldfred on 2015-06-25
I might disconnect Linux SSD, and install Windows.
If not, you must change BIOS to default boot from drive that is sdb, as that is where Windows will install its 100MB boot partition. If default is still sda, it may just overwrite the first 100MB with its boot partition, ignoring Linux partition.

I would suggest 50 to 100GB for Windows and then use rest of drive as a share NTFS data partition. Best to not write into the Windows system partition, and only mount it read only if you do want to access it. With the newer Windows you must have that fast startup or always on hibernation or you will not be able to mount any of the NTFS partitions.

---

### Post by drewmcarthur1 on 2015-06-25
I installed windows 10 on the HDD.  Unfortunately, for whatever reason, grub doesn't like booting the windows partition.  It's on a separate hard drive, so I can just use my BIOS to boot into windows so it isn't that big of a deal.  If you have any input I'll take it, but it isn't too important.  OS Prober found a recovery boot for windows, and I also put in a custom script to chainload windows, but neither worked.  They start booting windows (the windows icon is there, it's loading) then it stops and boots into ubuntu.  Oh well.

---

### Post by oldfred on 2015-06-25
Did you turn off fast start up or the always on hibernation?
Grub cannot restart Windows from hibernation, just full boot.
Somehow Windows boot from BIOS/MBR which loads partition boot sector is different when hibernated. And grub loading is the same as loading from MBR.

---

