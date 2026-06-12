---
title: "Installing Ubuntu to 2nd hard drive in Win 7 machine w/ legacy BIOS"
date: 2016-03-30
forum: Installation &amp; Upgrades
---

### Post by Ogden on 2016-03-30
I have a Win 7 64 bit machine that is UEFI capable but the OS was installed with the legacy BIOS option.  From what I have read, if I changed to UEFI, I would have to reinstall a Win 7 image which I prefer not to do.  So first question - is this true?  I have a clean 2nd hard drive which I will install Ubuntu 15 on next week with the intention of dual booting.

I have read so many conflicting step by step procedures that my head is spinning since most refer to UEFI.  As best as I can determine for a machine with legacy BIOS, I think I am supposed to set it up as follows assuming the HDD is /dev/sdb:

/dev/sdb1  Mounting point /boot  ...primary partition
/dev/sdb2  Mounting point /swap ...primary or logical partition? (size=4GB or more)
/dev/sdb3  Mounting point /   (root)...primary or logical partition?
/dev/sdb4  Mounting point /home ...primary or logical partition?

Install boot loader (GRUB 2) to /dev/sdb1 ... /boot partition so as to avoid over writing the Windows boot loader.

Then boot into Windows and run EasyBCD to add Ubuntu to Windows boot loader.

Am I on the right track, ill informed, confused?  Any thoughts would be appreciated.  I have until 6 April before I get started.

---

### Post by oldfred on 2016-03-30
With two drives you should not even need EasyBCD.
Keep Windows boot loader in Windows drive and install grub to MBR of Ubuntu drive or sdb, not sdb1.

Do not create a /boot partition. Only required with full drive encryption or LVM. Possibly with server installs, but not normal Desktop installs.

If system is UEFI, I would still use gpt partitioning on Ubuntu drive.
And I would add an ESP - efi system partition for future use. Difficult to add to beginning of drive, later when drive is full of data.
Ubuntu can boot in either BIOS or UEFI boot modes from gpt. 
Windows only boots in BIOS mode from MBR or only UEFI mode from gpt. Changing partitioning in effect erases drive. So yes you would have to back up Windows data & reinstall if you wanted UEFI boot for Windows.

You can install Ubuntu in UEFI mode, but then could only boot from UEFI boot menu or perhaps one time boot key like f10 or f12, check manual. Once you start booting in one mode you cannot switch, so neither grub nor EasyBCD will boot system in different mode.

If you have 4GB of RAM or more, I would just make swap 2GB and put it at end of drive. That may save some partition issues.
I suggest gpt as then you do not have any issue of primary or logical partitions. But if you want MBR, then Ubuntu can boot from either primary or logical partitions.

       I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning. I used gpt with many old versions of Ubuntu with my XP on MBR partitioned drive. But started including both the ESP & bios_grub partitions so drive could be configured for either BIOS or UEFI later.

How you boot install media, UEFI or BIOS is then how it installs. If you use gpt partitioning, you can convert Ubuntu from BIOS to UEFI or vice-versa. With MBR you have BIOS boot only.
      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25 GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical 
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
    
       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

---

### Post by yancek on 2016-03-30
You're needlessly complicating matters by creating a separate boot partition.  There are reasons where it makes sense and is even necessary but for an average home computer user without experience, I would definitely not recommend it.  The swap size should be alright, it all depends upon how much RAM you have and what you use the computer for.  Setting a separate /home partition should be easily done during the install and it is always a good idea to have a partition separate from the filesystem partition on which to keep your data.  You can easily create a separate /home or data partition after the install, your choice.

If your windows system is on sda, then installing Grub to the MBR of sdb would be the simplest.  If windows is sda, just don't install anything related to Grub on sda.  This will be the default so pay attention during the install as you can make a different choice from that default.  You could then select the sdb drive on boot to boot Ubuntu.  It might work with installing it to sdb1 and then configuring EasyBCD to boot it.  EasyBCD is a modification of Grub4Dos which is a modification of Grub so I don't know why you would want to use it unless you are more familiar with it.  It should work with a system as simple as two operating systems.  The Grub installed on sdb should detect your windows on sda.  The link below has detailed instructions on dual-booting windows/Ubuntu.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by Ogden on 2016-03-31
Thanks to both of you for providing a wealth of information and sources.  I think I understand what to do and hopefully the install goes smoothly.

---

