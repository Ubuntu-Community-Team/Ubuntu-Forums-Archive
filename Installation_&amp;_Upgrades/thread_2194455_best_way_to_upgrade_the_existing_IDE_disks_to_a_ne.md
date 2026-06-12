---
title: "best way to upgrade the existing IDE disks to a new 1 TB Sata disk."
date: 2013-12-18
forum: Installation &amp; Upgrades
---

### Post by aaguile on 2013-12-18
Hello. I want of you some advice about to change my two 80 GB IDE hard disks with dual boot (Ubuntu  13.10 and windows 7) to a 1 TB SATA hard disk with single boot with Ubuntu (Windows will be running as a virtual machine). So I am not sure the way to do a backup of my sd5 disk (where is the \ directory) and restore it when I'll have mounted my new 1 TB Sata disk. What tool to do the backup could I use? Should I use tar to backup? there will be problems as grub is working as a dual boot and my idea is have the new pc just booting with Ubuntu? There wiil be problems for changing IDE to Sata? And what will happen with the type of part. of the disk: now is MBR and with the Sata I want to use GPT?

PD: Is very important to me keep the present Ubuntu configuration.

---

### Post by oldfred on 2013-12-18
I have been using gpt with BIOS booting since 10.10 on smaller drive and newer SSD. Ubuntu will boot from BIOS if you have the bios_grub partition or if UEFI you must have the efi partition.
Windows only boots from gpt partitions directly if UEFI, but I do not know if virtual install then works or not? That should be a separate question in the visualization sub-forum. I have not used virtual installs. Many suggest them for Windows if you system has enough RAM and newer processor. 
[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

You also cannot use any sort of image copy of a partition when going from MBR to gpt. That internal partition structures are too different. You could use rsync or cp -a but have to change UUIDs and a few other settings to correct for new drive.

I generally suggest a new system install, copy /home over to new drive and make a list from dpkg of installed apps to make it easy to reinstall those. You may have a few settings in /etc that you need, depending on if you had to make any system wide changes.  With larger drives I suggest smaller system partition of 10 to 25GB and then have larger data and/or /home partitions. Then boot files are not all over drive and drive has to search entire 1TB to boot.

Because my backup assumes I will do a new install, that would be the same things you need.
 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

   Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
      
 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

I install gdisk but have used gparted to create my gpt partitioned drives.

 If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....


       
 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by aaguile on 2013-12-19
Hi Oldfred (viejo Fred in spanish:) ). Thanks a lot for your detailed help. I was reading each paragraph three or more times trying to understand all the concepts you touch. I didn't think that were so difficult keep the configuration of my present Ubuntu. In fact, the reason why I want to avoid a reinstall is that I   have Joomla installed wit some local sites, so PHP, MySQL and other applications have specia lconfigurations were I spent a lot of time. I'll be following your advice using rsync.

---

### Post by oldfred on 2013-12-19
I might houseclean old install before copy.
       RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.

Since you will be partitioning in advance, your new partitions will have different UUID. You then have to update fstab and grub with new UUID. And install grub to new drive. If gpt you must have the 1 or 2MB unformated partition with the bios_grub flag for grub to install. You should be able to update fstab and then boot to grub menu even if it has old UUID, and then with e manually edit the one boot stanza you use to boot with to the new UUID. Then once booted run sudo update-grub to update everything.

  
# To clear cache and get new view:
sudo blkid -c /dev/null -o list
This shows a booted drive's fstab, you have to mount new partition & edit copied version.
sudo cat /etc/fstab



Grub also remembers which drive to reinstall into. So you need to change that. You can only do this after booting new drive's copied install.
      
 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

You should review these also:

 more /var/cache/debconf/config.dat  | grep /dev/disk
UUID in grub, fstab &
more /etc/initramfs-tools/conf.d/resume
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid

I also not know about your database and Joomla configurations. Do they have anything specific to UUID or device like /dev/sda1?

---

