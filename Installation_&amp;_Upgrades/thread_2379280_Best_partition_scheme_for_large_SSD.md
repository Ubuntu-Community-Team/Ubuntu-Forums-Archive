---
title: "Best partition scheme for large SSD"
date: 2017-12-03
forum: Installation &amp; Upgrades
---

### Post by pjmlmas on 2017-12-03
I have a laptop with large SSD.(128gigs or 256gigs)
I want to intelligently partition it.
I will only be using it for linux OS.
I will likely have Ubuntu and CentOs (maybe a partition to play with other OS like Arch)
I have read some info regarding the UEFI setup.
I believe I can only have total four partitions?
1st partition primary for boot?
2nd partition primary swap ( for all Linux OS?)???
3rd partition extended
The following logical partitions:
3-1 would be  ubuntu 6-10gig
3-2 would be centos 5-7gigs
3-3 would be fat32 - sharing loading, 5-20 gigs

3-4 would be ext4 - video/pics/audio files, 20-100gigs - how do I back this up??? 
Would this be needed as a partition? Could this be better as memory card( 32-64gig)?
Backup memory cards?

3-5 what of my home directory? should this be on separate partition?

I want to be able to easily backup partitions. Maybe using Clonezilla.
3-6 backup clone for ubuntu (mess with bootup if cloned?)
3-7 backup clone for centos

ANY information(links as well appreciated), especially UEFI.

If any part is unclear,  or needs to be expanded, please let me know.

---

### Post by oldfred on 2017-12-03
If new system it is UEFI. And UEFI uses gpt partitioning by default which has no 4 primary partition limit. Essentially all partitions are primary, and there is a default limit of 128 partitions, which the user can change. (never seen anyone need that many partitions).

If only Linux, you can use gpt with either UEFI or BIOS, if you have correct supporting partitions.

I prefer to have each install in a 25GB / (root) partition and use a large /mnt/data partition that I can use for every install. But I primarily install Ubuntu or flavors thereof, so no ownership or permission issues between installs.

Most desktops do not need /boot partition. Do not confuse /boot as ext4 with UEFI required ESP - efi system partition (FAT32) which does have UEFI boot files.

Only if you have Windows should you use Windows formats as they may need Windows repairs or at least a Windows repair/recovery flash drive to run chkdsk. Only if small partition should you use FAT32, as it has no journal to ease recovery and it cannot have any file over 4GB.

Since 17.04 Ubuntu uses a swapfile by default. Only if swap partition found, then it will use that.

If only 128GB you will not have much room for video & audio files.
I use 128GB SSD as boot & several Ubuntu installs, but have data on HDD ( and more installs).
If just experimenting you can use flash drives for test installs. Slower loading, but once in RAM, just as fast.

       It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot. 
   For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 Do not share across installs, but use data partition(s) instead, if not just one install. 
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found) 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

### Post by Tadaen_Sylvermane on 2017-12-03
If I may, use LVM. It can be a bit of trouble to setup at first but it's a gift from above. Being able to snapshot before doing updates / trying new packages and being able to roll back with a reboot is a wonderful thing. Also you aren't hardlocked into a given partition scheme, just resize on the fly and keep going. It's worth it, even if you only have a single drive in my experience.

---

### Post by gordintoronto on 2017-12-04
+1 for Oldfred on partition sizes. With the sizes PJ suggested, the first time you forget to install updates for a couple of weeks, you'll have a broken system.

---

### Post by mastablasta on 2017-12-07
why complicate? modern PC should handle the other os easilly in virtual box or similar software.

---

