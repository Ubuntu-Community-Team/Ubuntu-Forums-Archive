---
title: "Ubuntu 16.04 GRUB behavior"
date: 2016-05-08
forum: Installation &amp; Upgrades
---

### Post by f00dl3 on 2016-05-08
I have used a setup for a while where I have a CloneZilla cloned drive initially created after every dist upgrade, and then use rsync to do differential backups every week or so. This worked fine in Ubuntu 15.04 and 15.10, but now in 16.04 I am having a weird problem, and it's two fold.  For some reason now that both sda and sdb are bootable, GRUB is acting wonky.   If I have sda (Seagate 2 TB drive) plugged in, it boots fine to sda. If I have sdb (Western Digital 2 TB drive) plugged in, it boots fine to sdb.  If I have both sda (Seagate) and sdb (Western Digital) plugged in, it boots to sdb. This is not what I want - I want it to boot to sda so I can mount sdb just for backups then unmount it after the rsync is done.  If I press and hold shift while booting, it brings up the grub boot menu, but only shows options to boot to sdb. It does not "see" sda if sdb is plugged in, though it boots fine to sda if sdb is not plugged in.  How do I get grub to boot to sda, and then mount sdb when I want?

---

### Post by oldfred on 2016-05-09
A clone as an exact image generally cannot be plugged in at same time for booting as you have duplicate UUIDs which is not allowed.
And BIOS will boot first drive it sees which may not always be the same drive.
And with duplicate UUIDs, sometimes it may be using a partition on one drive and next time a partition on the other drive.

I am surprised it worked for you before.

Unless a business that needs immediate restore capabilities, I find for my desktop that I can reinstall Ubuntu in 10 minutes. So I do not backup Ubuntu, just keep installer available. Yes, as time goes by there will be more updates to bring it back to where it is now.
But I backup /home with rsync and have data in separate /mnt/data partition which I separately backup.

---

### Post by f00dl3 on 2016-05-10
Yeah Ubuntu only takes 10 mins to re-install, but at home I run kind of a jack of all trades learning experience server. I have a OpenStreetMap tile server that takes 36 hours of constant CPU Load average of 4+ to build the 176 GB GIS database for North America. I have set up SNMP, Apache HTTPd w/ PHP7, Tomcat w/ JDBC w/ the HTTPd connector... when I had to install 16.04 fresh, it took me a week to get the computer to where "I wanted it" before I cloned the disk. I simply don't want to spend a week every time a drive fails to get it back up and running - I could be playing Skyrim/Deus Ex in WINE or writing more Java code. Got better things to do.

Is there a way I can maybe boot to the backup clone drive, write a line into grub-update nullifying the boot on sdb, so I can then boot to sda like I want - and if sda fails, be easily able to just toggle that flag on sdb so I can then boot sdb?

I realize that with 2 drives someone could easily suggest I do RAID - but I don't want a RAID setup, because I make frequent changes and sometimes those changes go south - it's good to have a known good image to fall back to, without worrying about my changes propagating both disks.

---

### Post by oldfred on 2016-05-10
It not really grub, but the duplicate UUIDs. Those can be changed, but then you have to reinstall grub and edit any configuration file with UUID, like fstab.

Some like to have a clone or full image on another device.
But I prefer to just use second drive and have another install on that drive. Then I rsync important data, but anything with drive or UUID in settings need to not be rsync'd.

---

### Post by f00dl3 on 2016-05-10
So if I were to do a clean install of Ubuntu 16.04 on "sdb" and then run the following script that rsyncs data, it would probably produce my desired result, right?:


StandbyMount="/media/astump/sdb1"

mkdir $StandbyMount
mount /dev/sdb1 $StandbyMount

rsync -aAXv --exclude={/dev/*,/proc/*,sys/*,tmp/*,/run/*,/mnt/*,/media/*,/lost+found,/etc/fstab,/boot/grub/grub.cfg} --delete-before / $StandbyMount

umount $StandbyMount
rm -fr $StandbyMount

---

### Post by oldfred on 2016-05-10
Would it be easier just to include /home? Or do you have server type data in databases or apache that are in / not in /home?

       Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

---

### Post by f00dl3 on 2016-05-10
Yeah - postgres, mysql, /var/www hosts my media server stuff I stream over SSH to my Android... lots of stuff not in /home. net-snmp configs, etc - Plus I want to make sure OS updates are mirrored over to the clone drive so I don't have to do a massive sudo apt-get update; apt-get upgrade

---

### Post by oldfred on 2016-05-10
What I do not know then is where in each of those may be settings that depend on UUIDs. I know fstab & grub. Grub also has a file on which drive by detail to reinstall grub to which must be updated also.

Related to swap's UUID:
 more /etc/initramfs-tools/conf.d/resume 
My new install this does not show anything:

 more /var/cache/debconf/config.dat  | grep /dev/disk 

With BIOS this showed reinstall, but not sure with UEFI:

 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short

---

