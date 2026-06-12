---
title: "Installing Ubuntu with UEFI on blank HDD (no previous Windows)"
date: 2014-07-28
forum: Installation &amp; Upgrades
---

### Post by tagy011 on 2014-07-28
I need instructions how to manually partition with adding EFI partition so that it can be installed under UEFI PLEASE . 
This is a blank HDD , never had win.

---

### Post by tagy011 on 2014-07-29
i created FAT 32 partition with mount point /boot/ efi/  , i ran the boot repair and placed grub into sda6 which is fat 32 partition i checked witrh gparted and partition is flagged bootable size 480 mig used 980 kib   so i imagine boot loader is under that partition  . However when i go into Bios and change boot to "UEFI  only " i get error no OS installed , what am i doing wrong ? Uubuntu still boots under Legacy tho ...

---

### Post by oldfred on 2014-07-29
UEFI requires gpt partitions.
Most BIOS boot installs are MBR(msdos) partitioning although Ubuntu will boot from gpt partitioned drive with BIOS or UEFI if correct partitions are on drive, bios_grub for BIOS or an efi partition for UEFI boot.

If you convert drive from MBR to gpt it will erase drive so make sure you have good backups.

Gparted will default to MBR, so you have to tell it you want gpt.
       I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....
I also install gdisk which is a command line tool for partitiong like fdisk is for MBR, but I have not used it to create partitions but do use it to view partition tables and check partitions. Good to have if you have gpt partitioned drive.
      
    
      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[URL="http://ubuntuforums.org/showthread.php?t=2021534"]http://ubuntuforums.org/showthread.php?t=2021534

      [/URL] UEFI install,windows 8 with Something Else screen shots (you can ignore the Windows instructions, but follow just the Ubuntu install part).
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

    [URL="http://ubuntuforums.org/showthread.php?t=2021534"]
[/URL]

---

