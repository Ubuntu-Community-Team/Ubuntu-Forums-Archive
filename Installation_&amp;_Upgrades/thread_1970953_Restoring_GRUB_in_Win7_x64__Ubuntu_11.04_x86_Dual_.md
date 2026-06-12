---
title: "Restoring GRUB in Win7 x64 / Ubuntu 11.04 x86 Dual Boot"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by avoyles on 2012-05-01
Hey guys, I've got a small problem that I'm hoping I can get some help with.

I've been using Ubuntu for about the past 4 years now, and have loved it, to the point that I only use Windows for MATLAB and similar applications anymore.

I have had a dual boot installation of Win 7 x64 and Ubuntu 11.04 x86 (on a pair of  750 and 320 GB SATA drives, respectively) since shortly after 11.04's release, relying on GRUB for switching between the two.

About a few days ago, in rebooting from Windows back into Ubuntu, I received a "no such partition" (or something along those lines) error in grub, and could not boot into either drive.

I used my Ubuntu LiveUSB to boot, and rand fdisk -l to check for the detected drives. Both were visible, with installed OS's. After running boot-repair with apparent success, I rebooted, but never saw GRUB, instead being booted straight into Windows. Running ext3explorer in Windows, it still detected my Ubuntu drive.

However, in the days since, I still cannot seem to be able to boot into Ubuntu, though Windows is just fine. By disconnecting the Windows drive, the Ubuntu drive cannot boot, and running boot-repair through LiveUSB like this cannot find an installed OS on the drive...

Ubuntu's Disk Utility still sees both drives, and reports both as healthy.

Here is the link to the most recent Pastebin from boot-repair:  [http://paste.ubuntu.com/961504/](http://paste.ubuntu.com/961504/)


Hopefully, someone can be of assistance, as I'm at my wit's end. I hate to have to reinstall, as I have several research coding projects in the works on my Ubuntu drive.

Thanks in advance for any assistance provided!

---

### Post by oldfred on 2012-05-02
Script could not mount your sdb1, so it has some issue. I might try this first.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by avoyles on 2012-05-02
Executing  sudo e2fsck -C0 -p -f -v /dev/sdb1   --

"e2fsck: Bad magic number in super-block while trying to open /dev/sdb1
/dev/sdb1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>"

Executing  sudo e2fsck -f -y -v /dev/sdb1    --

"e2fsck 1.41.14 (22-Dec-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>"


While I don;t remember the exact series of steps, I was able to boot into the Linux drive once at the start of these issues, but haven't been able to since originally running boot-repair.

---

### Post by oldfred on 2012-05-02
This is how to use an alternative superblock

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

### Post by avoyles on 2012-05-02
So, I have tried running both
sudo e2fsck -b block_number /dev/sdb1
and
sudo fsck -b block_number /dev/sdb1

for all of the backup superblocks, and all return the same error:

"fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>"

Thoughts?

---

### Post by oldfred on 2012-05-02
Someone posted these, but they are last ditch.

 redo superblocks:
[http://ubuntuforums.org/showthread.php?t=1681972&page=5](http://ubuntuforums.org/showthread.php?t=1681972&page=5)
Worked for this user:
[http://ubuntuforums.org/showthread.php?t=1684746](http://ubuntuforums.org/showthread.php?t=1684746)
Some additional advanced ways:
[http://animeshdas.wordpress.com/2009/11/18/data-recovery-from-corrupted-ext2ext3-filesystem-having-bad-superblock/](http://animeshdas.wordpress.com/2009/11/18/data-recovery-from-corrupted-ext2ext3-filesystem-having-bad-superblock/)
[http://www.hanksaves.com/hddrecovery/index.php/Welcome_to_Hank%27s_Data_Recovery_Wiki](http://www.hanksaves.com/hddrecovery/index.php/Welcome_to_Hank%27s_Data_Recovery_Wiki)

---

### Post by avoyles on 2012-05-14
Sorry again for the long delay. In case those last-ditch attempts to save the drive fail, I am attempting to recover the data on the drive using gParted and PhotoRec. If those fail, I will attempt the last ditch reformatting of the superblocks, and let you know how that turns out.

I suspect at this point I will need a new drive regardless. Fortunately, I have semi-recent (~3 weeks back) backups of my data, it would just be nice to save a few more recent files, and the convenience of not having to do a reinstall without a full backup of a few tedious-to-build-from-source toolkits.

Thanks again for the continued help.

---

### Post by avoyles on 2012-05-14
No luck with gParted. PhotoRec is currently running.

---

### Post by oldfred on 2012-05-14
I used photorec. It creates a lot of files. I had a folder of text files I use every day and it found all the old copies, partial copies, and some bits that were parts from more than one old copy. Not sure I ever found last saved. I compared several with my backups and got most of my data back. But I had to grep into each file to see what data was from what file.

Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

