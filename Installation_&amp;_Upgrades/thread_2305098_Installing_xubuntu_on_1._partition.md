---
title: "Installing xubuntu on 1. partition"
date: 2015-12-02
forum: Installation &amp; Upgrades
---

### Post by dave213 on 2015-12-02
Hey guys,

I'd like to use Xubuntu for cryptography stuff and made an issue I guess.
Here a quick overview.
I used Win8 on my 1TB HD and split it into two partition, each 500GB to install Win10 on the 2. partition.
The thing is, that I formatted the 1. partition but it was the primary partition and the second one is the logical one.
I want to install Xubuntu on the first partition but read on the internet that Win10 will be useless if I do so because Windows needs a primary Partition with an installed Windows.
So, what could solve my problem?

---

### Post by grahammechanical on 2015-12-02
Xubuntu, in fact any Linux distribution, does not care which partition it is install on. I would suggest that it is best to install Windows 10 first, both in time and in location. You may find that it needs more than one partition. And then install Xubuntu. I suggest this because there are posts on this forum from users who have upgraded Windows 8 to Windows 10 and found that Ubuntu has been removed because Windows 10 needed the partition. Installing Windows 10 second will most likely remove the Linux boot loader anyway.

Regards.

---

### Post by oldfred on 2015-12-02
Post this from terminal in live installer, if more than one drive include all of them:
 sudo parted /dev/sda unit s print

---

### Post by yancek on 2015-12-02
> I want to install Xubuntu on the first partition but read on the  internet that Win10 will be useless if I do so because Windows needs a  primary Partition with an installed Windows.

You don't need to install windows on a primary partition but you do need the boot files on a primary partition.  So you formatted the primary partition with the boot files on it and windows 8 so you could create a small boot partition in that space and install the windows boot files there.  Haven't installed any windows in over 10 years so I have no idea how that would be done?

---

### Post by dave213 on 2015-12-02
windows 10 is still installed and currently running. My motherboard supports UEFI Bootloader and I read that Xubuntu/Ubuntu 14.04 LTS can use UEFI too, so both would use the same bootloader in a way that both OS will be shown in a boot menu where I can choose one OS to boot, right?

what will this command do? On partition is nothing left except some 150MB big file(s), I assume these files are the boot files for Win10 on the other partition..?

To be honest I dont have a clue how to extract the boot files windows either. :/

---

### Post by oldfred on 2015-12-02
If you are using UEFI you do not have logical partitions.
Windows only boots in UEFI boot mode from drives partitioned with gpt which only has one type of partition. And Windows only boots in BIOS Mode from MBR(msdos) partitioned drives. 

Post the parted partition list, so we can confirm you current install.
If Windows is BIOS then you should also install Ubuntu in BIOS boot mode. But we need to see currrent partition to be able to suggest how to reconfigure.

---

### Post by dave213 on 2015-12-03
Oh okay, thanks for the information. Didnt know that. I read some stuff on the internet and it seems like the internet is full of crap (wrong information) nowadays.

[ATTACH=CONFIG]265909[/ATTACH]

this is the current set up of my Hard drive.
Quick translation:
Bezeichnung = Data system
Groesse = size
Fehlerfrei = error-free
Startpar = starting partition
Versteck = hidden

[ATTACH=CONFIG]265910[/ATTACH]

Here another screenshot of SnippingTool:
As you can see, E: is logical and C: is primary and some files are still on C.

---

### Post by oldfred on 2015-12-03
You show your c: "drive" or first large partition as 100%. Windows does not work well when full. In fast it only works really well if you leave 30% free. Do you have all your data well backed up that is in that partition?

You can copy boot files from first Windows to second Windows. But may not need to. You have the 100MB partition at beginning of drive. Typically that is the Windows Boot partition. If boot flag is on that partition then that is the primary partition you are booting from.

 And you can convert a logical to primary if you do not have more than 4 partition. 
But to install Linux you will need one of the 4 primary to be the extended partition to let you have as many logical partitions as you want.

You can use fixparts to convert logical Windows into primary if it meets all the other rules on partitioning.
       [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

But you need to plan sizes of partitions and whether they can be primary or logical. All Linux partitions can be logical. But Windows has to boot from a primary NTFS partition with the boot flag (set active in Windows).

I am not as familiar with Windows screens. Better to boot Ubuntu live installer flash drive in BIOS boot mode and post partitions from it using live mode. Also good to do that just to confirm Ubuntu works ok on you system before installing.

---

### Post by dave213 on 2015-12-03
Thx for the large amount of help and your explanations, that helped me a lot.

I will show you the terminal output when I am back home. Yesterday I tried Xubuntu and it worked well, but was unsure how to install it, how to make the paritions, etc.

See you later.

Hope you guys can get me through that :)

Ok here we go[ATTACH=CONFIG]265921[/ATTACH]

Does it mean that I can install Xubuntu on first partition without getting any error?

---

### Post by dave213 on 2015-12-04
Some more thoughts?

---

### Post by oldfred on 2015-12-04
When you say first partition you really mean sda2.
Your sda1 is the first partition but is just a tiny Windows Boot partition. 
Do not confuse a Windows boot partition with Linux boot partitions. And with most desktop installs you do not need /boot as a separate partition. But if using full drive encryption that has to have a separate /boot, but also erases entire drive. 

Note that drive in Linux is the entire physical drive, not the Windows definition which is very confusing. A d: drive in Windows can be another partition on first drive or another physical drive with one (or more) partitions.

---

### Post by dave213 on 2015-12-04
Ok thanks for you explanations. Yes I'd like to install Xubuntu on the sda2, not on the boot partitions of Windows.
Can I simply install Xubuntu without getting any errors later on? I want to prevent that because all stuff is on my Windows OS. I do not have any external HD where I could backup all my university stuff.

---

### Post by oldfred on 2015-12-04
If your data is at all valuable, you need to have backups. Flash drives are not expensive and even external hard drives are a lot lower in cost now.
Hard drives fail, usually at just the wrong time. Users make mistakes and erase the wrong thing. And sometimes software does not do what you expect.

If you have no data you cannot live without then you do not need backups, but otherwise you do.
 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
      
 If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

---

