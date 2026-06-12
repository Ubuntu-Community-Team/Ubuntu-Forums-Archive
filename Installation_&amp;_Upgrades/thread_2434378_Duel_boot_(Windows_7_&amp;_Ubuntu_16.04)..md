---
title: "Duel boot (Windows 7 &amp; Ubuntu 16.04)."
date: 2020-01-04
forum: Installation &amp; Upgrades
---

### Post by SUPERFITTER on 2020-01-04
I had a duel boot (Windows 7 & Ubuntu 16.04).  They are on seperate drives.  Windows 7 got corrupted and I reinstalled it on it’s drive. I ran grub repair and I now have a grub menu when I boot the computer.  The problem that I have is, there is no Windows 7 on the grub menu.  Ubuntu shows a Windows drive in Unity and in Gparted, but not the Grub Menu.  I did not change anything on the computer. I ran sudo os-prober in terminal, nothing happened, then sudo update-grub, it showed everything but Windows 7.

 I have run Boot repair, and every solution I could find on youtube and web searchs.  I tried this:

 If boot-repair is not found, then install it :

 sudo add-apt-repository ppa:yannubuntu/boot-repair &&
sudo apt-get update &&
sudo apt-get install -y boot-repair &&
boot-repair

I have run out of ideas, that's why I’m here.
 
 Thank you for any help

---

### Post by oldfred on 2020-01-04
Post link to summary report from Boot-Repair.
I would run each of the install commands separately, not with && as one long line. 
Then if issue on running command it will show, separately.

---

### Post by SUPERFITTER on 2020-01-04
Summary report from Boot-Repair.
[http://paste.ubuntu.com/p/Bphhv4bmmx/](http://paste.ubuntu.com/p/Bphhv4bmmx/)

---

### Post by ubfan1 on 2020-01-05
The paste link does not work, says "The Paste you are looking for does not currently exist."

---

### Post by SUPERFITTER on 2020-01-05
I ran it again and got this:
The current session is in Legacy mode. Please reboot the computer, and use this software in an EFI session. This will enable this feature. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")), after making sure your BIOS is set up to boot USB in EFI mode.

I cannot get it to run in EFI Mode with either Live Disk, Boot-Repair-Disk-64bit  or booted on Ubuntu.

Is there another method to fix this problem

---

### Post by oldfred on 2020-01-05
How did you create live installer? some may create from ISO one that only boots in one mode or the other.
ISO is designed to be booted in either boot mode if correctly created to flash drive or DVD.
Some UEFI only boot an installer with gpt partitioning in UEFI mode.
USB boot issues:
[https://askubuntu.com/questions/1190764/why-doesnt-a-bootable-usb-boot](https://askubuntu.com/questions/1190764/why-doesnt-a-bootable-usb-boot)

UEFI should offer two boot modes, if UEFI Secure Boot is off. One clearly UEFI and one BIOS/CSM/Legacy.
My system has UEFI:PMAP or PMAP. Often where I have pmap is the label or brand of a flash drive.

---

### Post by mörgæs on 2020-01-05
Support for Windows 7 runs out in ten days. Have you considered to erase the entire drive and install L/Xubuntu 19.10 in a single boot?

---

### Post by SUPERFITTER on 2020-01-05
This is all that I could get:

ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda1" dpkg --configure -a
ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda1" apt-get install -fy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda1" apt-get purge -y grub*-common grub-common:i386 shim-signed
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'grub-common' for glob 'grub*-common'
Note, selecting 'grub2-common' for glob 'grub*-common'
Package 'shim-signed' is not installed, so not removed
Package 'grub-common:i386' is not installed, so not removed. Did you mean 'grub-common'?
The following packages will be REMOVED:
  grub-common* grub-gfxpayload-lists* grub-pc* grub-pc-bin* grub2-common*
  os-prober*
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
After this operation, 16.8 MB disk space will be freed.
(Reading database ... 240480 files and directories currently installed.)
Removing os-prober (1.70ubuntu3.3) ...
Removing grub-gfxpayload-lists (0.7) ...
Removing grub-pc (2.02~beta2-36ubuntu3.23) ...
Purging configuration files for grub-pc (2.02~beta2-36ubuntu3.23) ...
Removing grub2-common (2.02~beta2-36ubuntu3.23) ...
Removing grub-pc-bin (2.02~beta2-36ubuntu3.23) ...
Removing grub-common (2.02~beta2-36ubuntu3.23) ...
Running in chroot, ignoring request.
Running in chroot, ignoring request.
Running in chroot, ignoring request.
Running in chroot, ignoring request.
Running in chroot, ignoring request.
Purging configuration files for grub-common (2.02~beta2-36ubuntu3.23) ...
Running in chroot, ignoring request.
Running in chroot, ignoring request.
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for install-info (6.1.0.dfsg.1-5) ...
install-info: warning: no info dir entry in `/usr/share/info/gnash_user.info.gz'
install-info: warning: no info dir entry in `/usr/share/info/gnash_ref.info.gz'
ubuntu@ubuntu:~$


I have tried different ways to get this thing to a full grub menu, including Windows 7.  I get so far in each method and then I cannot continue with the screen that comes up.  I have tried UEFI, UEFI & Legacy and Legacy in Bios.  I have gotten no where in the last 4 days.  When I first dual booted Win 7 and Ubuntu a few years ago I had no problems.  Now I have no idea what to do!

I need win 7 to run windows programs.

---

### Post by oldfred on 2020-01-05
Windows 7 usually is in BIOS/MBR mode. And only boots in BIOS mode from MBR.
And it only boots in UEFI mode from gpt.

If you cannot post a good Boot-Repair summary report post this:
sudo parted -l

---

### Post by SUPERFITTER on 2020-01-05
Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  105GB  105GB   primary   ext4            boot
 2      105GB   500GB  395GB   extended                  lba
 5      105GB   483GB  378GB   logical   ntfs
 6      483GB   500GB  17.1GB  logical   linux-swap(v1)


Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name                  Flags
 1      1049kB  106MB  105MB  fat32        EFI system partition  boot, esp
 3      240MB   500GB  500GB  ntfs         Basic data partition  msftdata

---

### Post by ubfan1 on 2020-01-06
I think Windows 7 needs to be on a primary partition, not a logical one. Ubuntu does not care which type it is on.  It might be possible to note the sectors each partition starts, and recreate the whole partition table using all primary partitions for linux, windows, and swap, using the sector numbers, but I've never tried to do that.

---

### Post by oldfred on 2020-01-06
Windows required boot files in a primary NTFS partition with boot flag.
The main install can be logical if you have the typical Windows 7 boot partition as a primary partition.
And you can put the boot files into the main install and not use a separate boot partition.

It looks like you must have had a separate Windows boot partition and that got deleted. It may have been on sdb? And install in UEFI mode using gpt on sdb erased the boot partition?
But you can convert your logical Windows partition to primary since you have only used 2 of the 4 primary partitions on sda.  But you have Windows in BIOS boot mode on sda & gpt for UEFI boot on sdb.

Before anything else backup partition tables for both sda & sdb drives. These are very small text files. Save to another device.
backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt

One of the options of this is to change a partition from logical to primary, if structure will follow the partitioning rules. Since your logical NTFS is next to the other primary, you should be able to change the NTFS to primary and then the start of the extended partition to after the NTFS partition. You just have to check a box.

To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Windows will not repair a logical NTFS. But once you convert it to primary and make sure it has boot flag (use gparted if it does not), you need to run a full set of Windows repairs from a Windows repair flash drive.

Or you can reinstall Windows. Since system is UEFI, you can install Windows in UEFI boot mode. How you boot install media UEFI or BIOS, is then how it installs.

---

### Post by SUPERFITTER on 2020-01-07
I'm going to install windows again on the windows drive after I go into BIOS and change it to UEFI boot.  After I reboot and check installation, I will hook up the Ubuntu drive.  Will I have a Grub menu or will I have to do something else?

---

### Post by oldfred on 2020-01-07
When you unplug a drive, UEFI typically forgets or changes entry to a default.
Most UEFI find Windows in the ESP, but not anything else.
You can use efibootmgr to add UEFI entry or reinstall grub which uses efibootmgr to add UEFI entry. 
And if you just use efibootmgr, you will need this for grub to find the new UEFI Windows boot:
sudo update-grub

sudo efibootmgr -c  -l \EFI\ubuntu\shimx64.efi -L "Ubuntu" -d /dev/sdX -p Y
sdX is drive, Y is efi partition default is sda and first partition, so only required if not sda1

If ubuntu drive still sdb and ESP is in first partition. My system often promote flash drive to sda, so then every drive moves up a letter. So best to always check.
sudo parted -l
sudo efibootmgr -c -g  -w -L "ubuntu" -l '\EFI\ubuntu\shimx64.efi' -d /dev/sdb -p 1

---

### Post by SUPERFITTER on 2020-01-07
oldfred

I have not tried your method yet.  
I saw this on line and wondered if anyone has tried one of these switch's?  
Would this be easier to have two separate drives. 
 No software problems between two or more hard drives?  Just wondering.  
If anyone has a better method of switching please let me know.
[COLOR=#0000ff]
[https://www.amazon.com/Control-Intelligent-Management-Profile-Bracket/dp/B07ZVTZVYD/ref=sr_1_10?keywords=hard+drive+switch&qid=1578429668&sr=8-10](https://www.amazon.com/Control-Intelligent-Management-Profile-Bracket/dp/B07ZVTZVYD/ref=sr_1_10?keywords=hard+drive+switch&qid=1578429668&sr=8-10)

[https://www.amazon.com/Switch-Module-Independent-Controller-Protection/dp/B07WNDGLJ3/ref=sr_1_14?keywords=hard+drive+switch&qid=1578429668&sr=8-14](https://www.amazon.com/Switch-Module-Independent-Controller-Protection/dp/B07WNDGLJ3/ref=sr_1_14?keywords=hard+drive+switch&qid=1578429668&sr=8-14)[/COLOR]

---

### Post by SUPERFITTER on 2020-01-16
I got rid of windows 7 and  installed Zorin Linux on that drive.  I got the grub menu, but when I  click on Ubuntu 16.04, I get this:

/dev/sda1: recovering journal
   /dev/sdal: clean, 784691/6406144 files, 15396563/25599999 blocks
   Welcome to emergency mode!  After logging in, type “journalctl -xb” to view
   system logs, “systemctl reboot” to reboot, “systemctl default” or ^D to
   try again to boot into default mode.
   Press enter for maintenance
   (or press Control-D to continue):
   root@Dennis1:~#

If I click Control-D, it tries to boot Ubuntu.  Then I end up in the same place, see above.

If I type: journalctl  -xb, I get thousands of pages of info that I do not know what to do  with.  I do not know how copy it to show you this info.  

If I go back to the grub menu, and click on Advanced Ubuntu 16.04, I end up in the same place.

Any  suggestions?

---

