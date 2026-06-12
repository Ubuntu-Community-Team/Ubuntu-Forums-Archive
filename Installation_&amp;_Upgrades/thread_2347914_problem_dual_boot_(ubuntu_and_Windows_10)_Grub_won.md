---
title: "problem dual boot (ubuntu and Windows 10) Grub won't load again!"
date: 2016-12-29
forum: Installation &amp; Upgrades
---

### Post by davidtuti2 on 2016-12-29
Hi,
I have an Acer v5-591G with Windows 10.
I install Ubuntu 16.04 with UEFI mode. The problem was that only boots with Windows Boot.
I follow these tutorial:

[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

And everything is ok. The bad thing is today I boot the laptop and other time I see that only boots with Boot Windows. I enter in BIOS and I see that the boot options are the same that when it works!

Something could help me please?
Many thanks and sorry for my English!

---

### Post by davidtuti2 on 2016-12-29
I pass a chkdsk to UEFI partition and it seems that have a unrecovery error. I boot from usb and I execute grub-repair but not works.  Then I choose reinstall ubuntu 16.04 but when I install it says me:  "unable to install grub in /dev/sda"
  I put you my boot-info. [http://paste2.org/DEOwxHfh](http://paste2.org/DEOwxHfh)

  Please somebody could help me? Thanks and sorry for my English!

---

### Post by oldfred on 2016-12-29
Grub will only boots working Windows.
So you must have Windows fast start up and hiberantion off.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Also generally better to have UEFI Secure Boot off. Again you can boot with Secure boot on, but only from UEFI boot menu, not from grub.

It looks like you have learned that Acer has the unique requirement of setting a supervisory password and enabling "trust" on the Ubuntu/grub .efi boot files.
 
It looks like grub could not write into the ESP - efi system partition your sda1.
It can be corruption of some sort. 
If you can read the files in the partition, back those up.
Make sure you have working Windows repair/recovery drive or installer with repair console.

Either from Windows run chkdsk on sda1, you will have to mount it in Windows.
Or from Ubuntu:
      
 [http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872](http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872)
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

If that does not work then you may have to delete partition with gparted, and then create a new FAT32 formatted partition, set boot flag to make it the ESP, restore folders/files from backup,. and reinstall grub or repair Windows to add entries back into UEFI.
Not sure if you have to enable trust again as it may see new files.

---

### Post by davidtuti2 on 2016-12-30
> **oldfred said:**
> Grub will only boots working Windows.
So you must have Windows fast start up and hiberantion off.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Also generally better to have UEFI Secure Boot off. Again you can boot with Secure boot on, but only from UEFI boot menu, not from grub.

It looks like you have learned that Acer has the unique requirement of setting a supervisory password and enabling "trust" on the Ubuntu/grub .efi boot files.
 
It looks like grub could not write into the ESP - efi system partition your sda1.
It can be corruption of some sort. 
If you can read the files in the partition, back those up.
Make sure you have working Windows repair/recovery drive or installer with repair console.

Either from Windows run chkdsk on sda1, you will have to mount it in Windows.
Or from Ubuntu:
      
 [http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872](http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872)
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

If that does not work then you may have to delete partition with gparted, and then create a new FAT32 formatted partition, set boot flag to make it the ESP, restore folders/files from backup,. and reinstall grub or repair Windows to add entries back into UEFI.
Not sure if you have to enable trust again as it may see new files.

Wow many thanks!
Fantastic clarification!
I did chkdks /r when disk mounted and it says me that it has an unrecoverable error.  When I pass dosfsck it says me:

```
sudo dosfsck -t -a -w /dev/sda1
fsck.fat 3.0.28 (2015-05-16)
/dev/sda1: 342 files, 50672/98304 clusters

```

But not works. Maybe first I should have done dosfsck before chkdsk. 
Other question, when you say that if it doesn't works I must format FAT32 EFI partition and restore folders. How restore these folders?
Anyway I have a clonezilla image of all system. I'm trying to investigate if I only can recover one partition with clonezilla.

Thanks!

---

### Post by oldfred on 2016-12-30
When I have lots of files/folders I use rsync or cp -a. With rsync I use lots of parameters as it is more for backup or copy to flash drive.

I have used Nautilus. Using it with gksudo is not recommended, but can be done. Just have to be careful not to move or delete any important files. All system files are important.

Default mount of fstab in your install is set to hidden (umask=0077). Boot-Repair resets it and older versions of Ubuntu were read/write (defaults). I manually change at end of install, so when I reboot into install it is writeable. 
       # /boot/efi was on /dev/sda1 during installation
14.04 fstab entry defaults
UUID=FD76-E33D  /boot/efi       vfat    defaults        0       1
16.04 fstab entry umask=0077
UUID=68CD-3368  /boot/efi       vfat    umask=0077      0       1

---

### Post by davidtuti2 on 2016-12-30
> **oldfred said:**
> When I have lots of files/folders I use rsync or cp -a. With rsync I use lots of parameters as it is more for backup or copy to flash drive.

I have used Nautilus. Using it with gksudo is not recommended, but can be done. Just have to be careful not to move or delete any important files. All system files are important.

Default mount of fstab in your install is set to hidden (umask=0077). Boot-Repair resets it and older versions of Ubuntu were read/write (defaults). I manually change at end of install, so when I reboot into install it is writeable. 
       # /boot/efi was on /dev/sda1 during installation
14.04 fstab entry defaults
UUID=FD76-E33D  /boot/efi       vfat    defaults        0       1
16.04 fstab entry umask=0077
UUID=68CD-3368  /boot/efi       vfat    umask=0077      0       1

Many thanks again. I've restored /dev/sda1 but same problem. I restore all disks (/dev/sda and /dev/sdb) (the restore image only have windows) and then I've installed ubuntu in /dev/sdb with grub in /dev/sda without problem. Now I can boot and grub appears and everything is ok.

I don't understand what do you say. You say that is better that I modify fstab to put "defaults" instead umask=0077?
I don't know what was the problem, but I know that if other time happens, first of all I'm trying to do dosfsck in EFI partition first.

Thanks

---

### Post by oldfred on 2016-12-30
I do not know for sure why they changed the mount of the ESP.
But suspect it is for security reasons. Linux file systems support ownership & permissions, where Windows files systems do not. So the FAT32 file system is more open to hacking like all Windows systems. I noted that even changing it in fstab & running mount -a does not remount the ESP until I reboot.

But I have multiple entries in my ESP and need to edit them. Grub overwrites my default boot and I want to fix that. I have learned to fix it while still in live installer after install, so I could leave settings as hidden and may go back to that. But often find I still want to backup ESP or do other things & having to reboot becomes a bit of a hassle.

---

### Post by davidtuti2 on 2016-12-30
> **oldfred said:**
> I do not know for sure why they changed the mount of the ESP.
But suspect it is for security reasons. Linux file systems support ownership & permissions, where Windows files systems do not. So the FAT32 file system is more open to hacking like all Windows systems. I noted that even changing it in fstab & running mount -a does not remount the ESP until I reboot.

But I have multiple entries in my ESP and need to edit them. Grub overwrites my default boot and I want to fix that. I have learned to fix it while still in live installer after install, so I could leave settings as hidden and may go back to that. But often find I still want to backup ESP or do other things & having to reboot becomes a bit of a hassle.
Thanks. What is the best method to make backup of ESP?
I'm investigating and I think other possible solution is install grub in partition of ubuntu and modify entries of Windows boot to can select grub of ubuntu

---

### Post by oldfred on 2016-12-30
With UEFI you do not install grub to partition. Boot-Repair suggests one of the work arounds for systems that do not boot well, by just adding an entry to the BCD. Details in link in my signature or in any list from Boot-Repair.

And even with BIOS the install to a partition is not recommended by grub2 as it is forced to use blocklists which are unreliable. And then EasyBCD uses the very old grub4dos which is based on grub legacy. 

I have a partition on sdb for backup. But only consider it a temporary backup or copy of files. Real backup is an image that does not get overwritten on DVD or flash drive.

I already created a mount point /mnt/backup. And partition sdb5 exists. And I have changed fstab so I can read the ESP partition.

fred@Asusz97:~$ sudo mount -t ext4 /dev/sdb5 /mnt/backup
fred@Asusz97:~$ sudo sudo cp -a /boot/efi/EFI /mnt/backup

Noticed root owned backup. Use of sudo did that. So I took ownership.
sudo chown -R $USER:$USER /mnt/backup/EFI

---

