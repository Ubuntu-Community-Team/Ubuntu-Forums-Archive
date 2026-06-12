---
title: "New ssd install"
date: 2013-10-26
forum: Installation &amp; Upgrades
---

### Post by senyamckinney on 2013-10-26
This is my first ubuntu install and I would like my ssd to be ubuntu only. I have read multiple threads suggesting using gparted (with no specific formula for partitions) and others that say ubuntu will partition a new drive automatically. The ssd is 256gb and I would like to optimize ubuntu for a ssd. Are there any hard answers as to which install is best and why?

---

### Post by oldfred on 2013-10-26
The installer will install with default settings for just / (root) and swap. And for a new user that is all that is really required. I had that plus XP on anther drive with a shared NTFS data partition for 3 or 4 years.
But many suggest separate /home to make a clean new reinstall easier as all user settings are in /home. Or separate data partitions. 
Will you also have a rotating hard drive? Then some partitions my be better on it.

If Linux only I now prefer gpt partitioning. But if installing Windows ever, gpt partitioning will only work if booting with UEFI. Ubuntu can boot from gpt partitioning with either UEFI or BIOS, but different partitioning is required.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
    
       Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://wiki.debian.org/SSDOptimization?action=show&redirect=SSDoptimization](http://wiki.debian.org/SSDOptimization?action=show&redirect=SSDoptimization)

    
 With SSD or Flash (trim does not work on flash) drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode for trim to work.

      
 You normally want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD&#8217;s, Journaling, and noatime/relatime 
noatime,nodiratime options in fstab to make the ssd last longer when using a ext4 partition

 Shows both discard & fstrim methods for trim
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

Many now say that new SSD have lives comparable to hard drives and special configurations are not really required.

---

