---
title: "proper backup/restore/replication"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by vangop on 2010-07-07
Hi!
I need an expert advice here.
I've spent a while fine-tuning my system, now I want to backup the things.
My intention is:
1. backup the system so that if anything breaks I could restore to the point
2. replicate the system to other computers (other hardware)

Please suggest a proper way of making a backup/restore in both cases.
I understand that the best way is to use tar to archive the system and then unpack it. I read some tips on that /proc, /dev, /sys and /mnt should be excluded. As I understand I will need to do a fresh install from liveCD and then extract this tar to get my settings/apps back. 
Any tricks regarding other PCs (replication)? 
Will I have to tune permissions? There's a lot of other tricks I might not mentioned, I need somebody with experience give an advice..

---

### Post by tommcd on 2010-07-07
There is **remastersys** which you can add to Ubuntu to: > ... make a full system backup including personal data to a live cd or dvd that you can use anywhere and install. It can make a distributable copy you can share with friends. This will not have any of your personal user data in it. 
See this article from Ubuntu-Geek:
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)
There is also **Clonezilla** which is available as a live CD:
[http://clonezilla.org/](http://clonezilla.org/)
I have never used either of these myself. I have just read about them.

---

### Post by vangop on 2010-07-07
Thanks for the tip, I'll check it.
But I'd like to explore a simple tar solution first. I prefer the simplest solution that I can understand and control :)
Anybody can help with this?

---

### Post by tommcd on 2010-07-08
You may be interested to know that Ubuntu 10.10 will likely have the option to install using the **btrfs** file system. This will give you the option to make system snapshots so you can roll back the system to a previous state if something goes wrong. See these articles:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1010_btrfs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1010_btrfs&num=1)
[http://www.phoronix.com/scan.php?page=news_item&px=ODI1Mg](http://www.phoronix.com/scan.php?page=news_item&px=ODI1Mg)
Phoronix.com follows the development of this stuff closely, so check their site for updates on btrfs if you are interested.
The btrfs file system is available for Ubuntu 10.04, but it is not yet ready for prime time from what I have read.

---

### Post by vangop on 2010-07-09
Thanks for the info! That would be a cool feature, like system restore on Win.
I still want to understand the tar backup/restore/replicate technique in educational purposes :)
Anyone?

---

### Post by tommcd on 2010-07-09
> **vangop said:**
> 
I still want to understand the tar backup/restore/replicate technique in educational purposes :)
Anyone?
There are many tutorials on the net for backing up your system with tar:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
[http://www.aboutdebian.com/tar-backup.htm](http://www.aboutdebian.com/tar-backup.htm)
[http://slashzeroconf.wordpress.com/2008/03/15/script-to-backup-and-restore-linux-system-using-tar/](http://slashzeroconf.wordpress.com/2008/03/15/script-to-backup-and-restore-linux-system-using-tar/)
[http://www.thinkwiki.org/wiki/How_to_copy_a_Linux_installation](http://www.thinkwiki.org/wiki/How_to_copy_a_Linux_installation)

The **rsyc** command can also be used to make incremental backups:
[http://www.linux.com/news/enterprise/storage/8200-back-up-like-an-expert-with-rsync](http://www.linux.com/news/enterprise/storage/8200-back-up-like-an-expert-with-rsync)

---

### Post by bodOrange on 2010-07-10
I would recommend going with rsync rather than tar.  rsnapshot manages rsync incremental backups for you.  Is easy to setup and conserves backup diskspace by using hard links.  By default, it will not cross filesystems, therefore no need to to worry about excluding virtual filesystems (proc, sys, dev etc) from the backup.  If your install is spread across more than one filesystem (say seperate /home) you will need to configure accordingly.

I had to restore an Ubuntu system from an rsnapshot backup recently.  It was straight forward enough:
- Boot from a liveCD
- Partition if necessary
- Format partitions
- Mount partitons
- Restore files using rsync
- Recreate essential device nodes (/dev/null, /dev/console)
- Adjust /etc/fstab if necessary
- Adjust grub config if needed (root partition UUID).
- Reboot

The backup can be restored via rsync from a local hdd, nfs mount (not smb) or via ssh.

If using a db server, avoid restoring your  database directly from your general backup.  Run a seperate job and back up the db's, in the case of MySQL using mysqldump, via a single transaction.  This can also be managed by rsnapshot if you like.

If you do use gzipped tar archives, one corrupted block could render the following archive data useless.  Also with tar, incremental backups are more hassle to restore a particular time point.  It may require several restore operations in the right order.  With rsync snapshots, you're only concerned with one restore operation as each backup appears as a complete snapshot thanks to hard linking.

As far as restoring the backup to a different machine, you should have no problems, unless you try to boot x64 system on incapable hardware.

---

### Post by bodOrange on 2010-07-10
> **vangop said:**
> Thanks for the info! That would be a cool feature, like system restore on Win.
I still want to understand the tar backup/restore/replicate technique in educational purposes :)
Anyone?
Using rsnapshot will give you something very similar to the OS X time machine (without the fancy interface).  It's advisable, though not strictly necessary, to boot in to another environment (liveCD for instance) in order to carry out a full system restore.  Apart from that, restoring files is simply a matter of browsing to the appropriate time point in your backup and copying the files.  Alternatively, use rsync restore them (simplifies preservation of atime/mtime of the restored files).

Bear in mind that tar was designed to be used to archive to tape, hence the name.  It catenates all the files together, writing out to the backup device .  Consequently, to access any file for restore the tar file needs to be accessed sequentially until the file is found.  If you're backing up to an hdd as opposed to sequential access device like a tape, then there is no need to be confined by the limitations inherent in tape backup.  With tar, I am never sure which switches to use when creating/extracting archives, the defaut options wrt preserving owner/permissions etc.

---

### Post by vangop on 2010-07-10
tommcd
Thanks, but the articles are very similar, they just show a general way of doing a backup, not really going into the details if any problems might occur. 
There's an unanswered comment in one of the links - will this work to restore the backup on another system (replication). 
I just want to make sure I'm making a proper backup, so that when I have to use it I don't find out that something is missing. :) Like hardlinks, symlinks, permissions, etc. A list of questions I have:
1. When tar is making a bakup it says 'removing absolute hardlinks' or something. Is that ok?
2. If I replicate the system on another computer, what is the right way of doing it? Should I install the system on that machine 1st (most likely, as I'm excluding /proc /dev /sys) or it is enough to just install grub and the kernel will probe/do all needed stuff by itself.
3. User permissions. I would like to replicate the system fully including user prefs (home folder).
Do I have to do some user manipulation on the target system, like UID/GUID/name tuning. I just saw some reports that people had problems when they created a user with same name as a restored one.
4. any other tricks?

bodOrange
Can you show how you do the actual backup? Is it possible to replicate the system on another PC, I mean I have a vague understanding how linux creates /proc /sys /dev so will I have to install the fresh system and then restore or it is enough to restore and then tune the things?
How did you create /dev/null ... things for instance?

---

### Post by bodOrange on 2010-07-10
> **vangop said:**
> tommcd
Thanks, but the articles are very similar, they just show a general way of doing a backup, not really going into the details if any problems might occur. 
There's an unanswered comment in one of the links - will this work to restore the backup on another system (replication). 
I just want to make sure I'm making a proper backup, so that when I have to use it I don't find out that something is missing. :) Like hardlinks, symlinks, permissions, etc. A list of questions I have:
1. When tar is making a bakup it says 'removing absolute hardlinks' or something. Is that ok?
2. If I replicate the system on another computer, what is the right way of doing it? Should I install the system on that machine 1st (most likely, as I'm excluding /proc /dev /sys) or it is enough to just install grub and the kernel will probe/do all needed stuff by itself.
3. User permissions. I would like to replicate the system fully including user prefs (home folder).
Do I have to do some user manipulation on the target system, like UID/GUID/name tuning. I just saw some reports that people had problems when they created a user with same name as a restored one.
4. any other tricks?

1. I believe tar will strip leading / from filenames.
2. When replicating the system, there's no need to install first if you have a complete backup to restore from.
3. The only reason you'd want to alter ownership of the /home/* directories is if your uid's (in /etc/passwd) don't correspond to the owners of the home directories.  Say you have restored home from some other source or another distro.  If need be you can recursively chown each home directory.
4. Use rsync ;-)  


> 
bodOrange
Can you show how you do the actual backup? Is it possible to replicate the system on another PC, I mean I have a vague understanding how linux creates /proc /sys /dev so will I have to install the fresh system and then restore or it is enough to restore and then tune the things?
How did you create /dev/null ... things for instance?The virtual filesystems (with the possible exception of /dev) contain no 'real' files so no need to backup.  If udev is active, you can not access any underlying device nodes in /dev.
I believe, with the Ubuntu initrd at any rate, you can get away without any device nodes in /dev.  It al depends on the initrd.  It doesn't hurt to create them either way.  [http://www.gentoo.org/doc/en/udev-guide.xml#doc_chap3_sect1](http://www.gentoo.org/doc/en/udev-guide.xml#doc_chap3_sect1) gives some information and how to create device nodes. Obviously this needs to be done when udev is not mounted on the directory concerned.

To list mounted virtual filesystems:
```
 mount | grep -v '^/dev'
```
None of these need be backuped up.  By default rsync does not traverse filesystems anyway.  tar on the other hand does by default.

For rsnapshot/rsync there are plenty of tutorials.  Essentially:
```
aptitude install rsnapshot
```Then define your backup jobs.  There are plenty of options in /etc/rsnapshot.  I generally set global options there then define a conf file for each backup.  My main backup config:
```
include_conf            /etc/rsnapshot.conf #include default config
snapshot_root            /mnt/ext_backup/snapshots/localhost/
rsync_long_args        --delete --numeric-ids --relative --delete-excluded

#cmd_preexec    /path/to/script
#cmd_postexec    /path/to/script

exclude        /home/*
exclude        /*/\$RECYCLE.BIN
exclude        /var/recycle/*

interval    daily    2
interval    weekly    1

backup    /        ./
```
The other thing to bear in mind is how these backups or more importantly the restore process handles links.  Symlinks aren't a problem.  Hard links I'm not so sure.  AIUI when restoring with rsync (or tar for that matter), hardlinks aren't preserved.  So if you previously had 2 hardlinks to one file, after restore you end up with 2 independent files, therefore doubling disk space requirement.  I am not entirely sure about this so worth reading up.  You might want to experiment with [http://www.ipp.mpg.de/~dpc/gnu/findutils-4.1/html_chapter/find_2.html#SEC13](http://www.ipp.mpg.de/~dpc/gnu/findutils-4.1/html_chapter/find_2.html#SEC13)
I keep meaning to do so myself but haven't got round to it.

AIUI the only way to have a block for block copy is to image your partitions.

---

### Post by tommcd on 2010-07-10
I didn't know about **rsnapshot**. Thanks for mentioning it.

As far as hard links are concerned, using **rsync** with the **-H** option will preserve hard links when making the backups. So wouldn't restoring the system with rsync maintain those hard links as well?
I have only used rsync to transfer and backup data. I never used it to backup system files, so I am not sure about this.

BTW, the man page for rsync is very well written and has plenty of examples on using it.

---

### Post by bodOrange on 2010-07-10
> **tommcd said:**
> I didn't know about **rsnapshot**. Thanks for mentioning it.

As far as hard links are concerned, using **rsync** with the **-H** option will preserve hard links when making the backups. So wouldn't restoring the system with rsync maintain those hard links as well?
I have only used rsync to transfer and backup data. I never used it to backup system files, so I am not sure about this.

BTW, the man page for rsync is very well written and has plenty of examples on using it.

Thanks, so it does and I imagine if you use -H when restoring, it will work as  expected. With rsnapshot I have been invoking rsync:
```
rsync -a  --delete --numeric-ids --delete-excluded
```After posting earlier I looked for  files on my system that had more than one hard link:
```
sudo find / -xdev -type f -links +1 -exec ls -li {} \; | sort -n
```There were a few utilities, filesystem  tools and a whole bunch of files from tzdata. I've never had the occassion to choose hardlinks over soft for my own use.  I imagine it's a consequence of easing package management.
So, as expected, the only hardlinks I see in my backups are those between each snapshot. Don't think I will bother with -H switch though.

---

### Post by vangop on 2010-07-10
Thanks for the answers. 
So to sum up. Use rsync to make backups over tar.
From what I've read I need 
```
rsync -aH --numeric-ids --exclude /proc --exclude /sys / /mnt/backupplace
```
I tried but it just makes a copy of the filesystem. Can it be packed into 1 file or I should just tar.bz2 it afterwards? 
For some reason in the copy I see that file owner is root.root.. Is that ok? Can it be caused by the fact that the bak partition is ntfs? (I notice that all files on ntfs are owned by root.root)
I'll prolly read smth on udev to understand how the /dev is created, to clarify the exact procedure to clone the system on a PC with different hardware.

---

### Post by bodOrange on 2010-07-10
Your exclusions are redundant as rsync will stay within the filesystem of the source directory.

ntfs is not recommended as permissions and ownership will not be retained.  The reason all the files on the ntfs partition appear as root:root is down to the default ownership when mounting an ntfs partition.  You can change this via ntfs mount options, but all files will appear with same uid/gid.  Best stick with ext fs for your backups.  Backup to ext2/3/4.  Whether you choose ext3/4 over ext2 depends on whether you want journalling on your backup drive.  Personally I stick with ext3, maybe using xfs occassionally.

I guess you can if you like tar it up afterwards, but then you may as well backup with tar anyway!

I wouldn't bother too much with creating device nodes on dev.  I think I was a little behind the times with my remarks regarding it earlier.  It seems all the modern distros can boot with no device nodes in /dev before udev is up.  If you read that gentoo page regarding udev, it explains the concept very well.  In fact the rest of the gentoo install guide is well worth a read.

HTH

---

### Post by vangop on 2010-07-11
Ok, so I'm back where I started :)
Looks like I can use
```
tar cvpjf /mnt/wind/safe/linux.$(date +%F).tar.bz2 --exclude=/proc --exclude=/lost+found  --exclude=/mnt --exclude=/sys --exclude=/dev
``` 
for backup and then 
```
tar xvpjf BACKUP_FILE -C /
```
For both restore and replication.(fix grub in latter case)
What about the kernel modules. AFAIK kernel probes hardware during the boot, so in case of a system replication to a different hardware I shouldn't have problems, right? Or the modules will not be present on the system, so even if kernel finds that it needs xxx module, it won't be at hand?
Should I install from liveCD 1st then?
In case of a local backup tar is > rsync IMHO.
1. one file, easy to drop to flash/external hdd.
2. no problems with ownership if stored on ntfs partitions.
3. It can be updated I think. So really no advantages in using rsync (unless you need to use network)

---

### Post by bodOrange on 2010-07-11
> **vangop said:**
> Ok, so I'm back where I started :)
Looks like I can use
```
tar cvpjf /mnt/wind/safe/linux.$(date +%F).tar.bz2 --exclude=/proc --exclude=/lost+found  --exclude=/mnt --exclude=/sys --exclude=/dev
```for backup and then 
```
tar xvpjf BACKUP_FILE -C /
```For both restore and replication.(fix grub in latter case)
What about the kernel modules. AFAIK kernel probes hardware during the boot, so in case of a system replication to a different hardware I shouldn't have problems, right? Or the modules will not be present on the system, so even if kernel finds that it needs xxx module, it won't be at hand?
Should I install from liveCD 1st then?
In case of a local backup tar is > rsync IMHO.
1. one file, easy to drop to flash/external hdd.
2. no problems with ownership if stored on ntfs partitions.
3. It can be updated I think. So really no advantages in using rsync (unless you need to use network)
Ubuntu installs a full kernel and all modules.  Module loading is not customised to the machine unless you specifically load, blacklist or otherwise configure module loading.  So it will boot on similar architecture with different hardware fine.  You just need to configure fstab and configure and install grub once you've extracted your archive.
Replicating from tar archive will be exactly the same as with rsync, except the step for copying the files back:
Partitioning
Format
Mount partiton(s) in livecd environment
Copy files from backup (tar or rsync or wherever)
Edit fstab
Edit grub menu.
You might want to delete interfaces in /etc/udev/rules.d/70-persistent-net.rules otherwise you end up with eth1.
Install grub (when replicating a system, I've always chrooted into the new installation from livecd.  Then installed stage1 grub to MBR from there.  But I expect there is an easier way to do this.)

I think your excludes will omit the top level directories.  You  don't really want that.  Maybe --exclude=/proc/* etc.  You might want to  exclude /var/run/ and /var/lock/ too.

I take your points about single file and backing up to ntfs.  If you must go that route, then use tar.  I would be wary using linux ntfs write support for a backup.  I have still encountered problems with ti even in recent versions of ubuntu.

I've never tried updating tar files.  Maybe someone else can comment.

---

### Post by vangop on 2010-07-13
> **bodOrange said:**
> 
You might want to delete interfaces in /etc/udev/rules.d/70-persistent-net.rules otherwise you end up with eth1.
...
I think your excludes will omit the top level directories.  You  don't really want that.  Maybe --exclude=/proc/* etc.  You might want to  exclude /var/run/ and /var/lock/ too.


Thanks for the clarification! Reg. 70-persistent-net.rules - I should delete the file or clear its contents?

About the excludes - all the guides say that one should exclude /proc /sys as those are recreated each boot, /mnt - don't need it, and /dev - udev recreates it and it doesn't make sense on a replicated PC with different hw. 
Can you plz explain what you mean by "omit top level". Will I omit something I need or you think I should keep /sys /dev?

Updating the backup is not an issue, if I can't find a way to do that I can just retar and delete an old bak.

---

### Post by tommcd on 2010-07-13
I just came across a timely article on this subject on HowToForge.com. The article is about backing up or ghosting a computer across a network with a command line program called **netcat**. I am not familiar with using netcat at all. This is the first time I have heard of it:
[http://howtoforge.com/ghosting-the-machine](http://howtoforge.com/ghosting-the-machine)
I thought I would post this as a possible alternative to tar or rsync. It seems pretty simple.
Netcat is in the Ubuntu repos: [http://packages.ubuntu.com/lucid/netcat](http://packages.ubuntu.com/lucid/netcat)

bodOrange,
You are obviously more familiar with this stuff than I am. Have you ever heard of, or used, netcat?

---

### Post by vangop on 2010-07-13
I think netcat is used to copy the data over the net. dd or tar can pipe the data to/from netcat.

---

### Post by bodOrange on 2010-07-18
> **vangop said:**
> Thanks for the clarification! Reg. 70-persistent-net.rules - I should delete the file or clear its contents?

About the excludes - all the guides say that one should exclude /proc /sys as those are recreated each boot, /mnt - don't need it, and /dev - udev recreates it and it doesn't make sense on a replicated PC with different hw. 
Can you plz explain what you mean by "omit top level". Will I omit something I need or you think I should keep /sys /dev?

Updating the backup is not an issue, if I can't find a way to do that I can just retar and delete an old bak.

WRT to the interfaces, don't delete the file!  Delete the line that defines eth0.  By default, udev will create a new interface for new MAC's it sees.  Therefore, if you replicate the backup to _another_ machine, it will likely have a different network cardand if you leave the line intact, udev will create an interface, eth1.  This isn't a problem per se, butyou might have something configured that refers to eth0 and so will not work as expected.  If you're restoring to the original box, then all that doesn't matter.  BTW something I noticed when changing/adding NIC's was that if I just commented the interface lines, udev seemed to still create eth+1.

With the virtual filesystem mounts:
By top level (wrong terminology I know) I meant /mnt, /sys, /proc. You still need the se for mount points, the kernel won't auto create them for you.   My point was: avoid the additional step of recreating these following a replication/restore.  You're backup tool can include the directory less it's contents.

Sorry for the late response.

---

### Post by bodOrange on 2010-07-18
> **tommcd said:**
> I just came across a timely article on this subject on HowToForge.com. The article is about backing up or ghosting a computer across a network with a command line program called **netcat**. I am not familiar with using netcat at all. This is the first time I have heard of it:
[http://howtoforge.com/ghosting-the-machine](http://howtoforge.com/ghosting-the-machine)
I thought I would post this as a possible alternative to tar or rsync. It seems pretty simple.
Netcat is in the Ubuntu repos: [http://packages.ubuntu.com/lucid/netcat](http://packages.ubuntu.com/lucid/netcat)

bodOrange,
You are obviously more familiar with this stuff than I am. Have you ever heard of, or used, netcat?

Never used it myself.  Seems it's a way of creating a pipe between two processes over the network.  It's installed on my ubuntu box so is either a standard unix tool or was pulled in as a dep for something and I can't remeber how to find reverse dependencies with apt :-(

---

### Post by vangop on 2010-08-05
Ok, I now had to restore my backup on 2 other PCs. 
The original was NVidia based, the other 2 where Intel 965GM and SIS.
I had to :
1. install grub (booting from CD )
2. change fstab to match new partition uuids
3. change uuids in grub menu on boot as it was still referring to the old uuids. I actually removed the uuids in the kernel commands and substituted with actual partition names.
4. X server complained on misconfig and suggested to make a new one. Upon reboot I ran update-grub to fix the menus with proper uuids.

All was working fine except for openGL based stuff. compiz-fusion wasn't working (compiz site blacklists 965 intel card, maybe sis is also unsupported..). 
So video confi might be the major issue with replication..

---

