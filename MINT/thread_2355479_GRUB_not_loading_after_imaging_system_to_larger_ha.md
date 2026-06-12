---
title: "GRUB not loading after imaging system to larger hard drive"
date: 2017-03-13
forum: MINT
---

### Post by brendand2 on 2017-03-13
Hi,
I imaged a system from a 1TB to a 4TB drive. I followed online instructions on converting MBR to GPT and then used boot-repair to reinstall GRUB. But GRUB will not boot. Here is the boot-repair log: [http://paste2.org/yLN4wg3m](http://paste2.org/yLN4wg3m)
Does anyone have any suggestions on why the system will not boot?

---

### Post by oldfred on 2017-03-13
Moved to Mint since not Official flavor.

I am not seeing anything really wrong.
But imaging from MBR to gpt is not recommended. Not sure if it would work the way you did it or not.

I find since most have issues like you have, it just is easier to do a new install to a new drive and then copy data. Good way to test that your backup procedures have all your data, anyway.
With larger drives ( I have a 1TB drive and find that large), I prefer to have separate / (root) & /mnt/data and then additional roots, specific data and other partitions. Backing up one huge partition can be a bit more difficult.

I also prefer to partition in advance. And since most now have new UEFI systems, configure for UEFI and if desired also BIOS. I normally add both the ESP & the bios_grub so drive can be easily converted from UEFI to BIOS or vice-versa without major reconfiguration of drive.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
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

---

### Post by brendand2 on 2017-03-13
Backup procedures? #-o#-o#-o#-o#-o#-o#-o#-o

---

### Post by oldfred on 2017-03-13
Everybody has their own preference.
 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup) 

I prefer just using rsync which is not really backup unless you have multiple copies in various places so it is versioned.

I find install easy enough with Linux to just do an install, restore /home and I prefer to have /mnt/data for all my data, so /home is tiny.
Anything I manually edit in /etc, I copy to /home so it also gets backed up but not automatically restored as it may or may not be the settings in a newer install.
      
 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

### Post by brendand2 on 2017-03-13
Thanks

---

