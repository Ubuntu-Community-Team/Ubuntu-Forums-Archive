---
title: "Which partitioning/volume type suggested for best backup / restore / recovery options"
date: 2016-01-01
forum: Installation &amp; Upgrades
---

### Post by Elishasmantle on 2016-01-01
Hello,

Can someone please tell me what type of installation options are best for :
1) System data files can be backed up on a schedule
2) System ( / , /etc , installed applications, etc...) can be done via snapshots or scheduled back-up?
3) If a crash happens I can either:
a) Use a full disk clone recovery, or partial recovery
b) I can do a fresh install and then use a snapshot or directory backup to restore data to last known good state.

My goal is to get an install and back-up plan going where if I need to re-install i can do my install and data restore and be back up within a few hours.
I don't want to do a re-install and spend days/weeks trying to get all my modified files reconfigured, samba setup, etc...

Can all this be done with LUKS as well?
I'm not fond of disk encryption from my windows experience. I have found on the windows side, encryption is very temperamental and problematic for boot up failures, and decrypting hdd is a long painful process, although if I get my backups setup properly this should not be an issue.

Thank You,

elishasmantle

---

### Post by ian-weisser on 2016-01-02
Some users have had great success doing clone-a-bootable-system backups. Others have not. No GUI for this - shell only.
Some users have had great success doing versioned backups with rsync and rdiff-backup and cron. Others have not. Both GUI and shell interfaces.
Some users backup the data in their /home. Servers back up /var/www and other common service data. Some back up /etc, though this presents difficulties in a debian-based system.
Most backup software will happily backup encrypted files too.

On my business system, I back up data only. I have almost no customizations on it, and simply restore to factory-condition annually.
On my personal system, I back up data. Included in the data is a text journal of all my customizations, sources, links, instructions, reasons. Very useful for uninstalling or troubleshooting a customization later. When rebuilding my system for a new release of Ubuntu, I can pick-and-choose which customizations to include...and test each one.

I think you should decide which backup strategy you want to pursue first. You can always change your mind.
Then we can point you toward more specifics.

---

### Post by Elishasmantle on 2016-01-02
Hello,

What I am looking for is not really a "Cloned" Backup.
I prefer a type of backup like your personal one.
I'm new to linux and getting everything setup and this has included my OpenVPN software with my certs / keys, as well as testing out getting Samba setup, FTP Server, etc... and I am trying to do a .bak of original files before I modify them, takes nots and save HowTO Setup articles and I do not want to lose this information, also do not want to do a new setup for like my OpenVPN, etc... So I am looking for a backup that will restore all my software installed with all required .conf , config files, etc... so let's say if I had a system crash I could do a fresh install and a data restore and I would be back up and running within a few hours or that same day.

I dread the thoughts of a new install and it taking days or weeks to get me back to where I was before the crash.

Thank You,

Elishasmantle

---

### Post by oldfred on 2016-01-03
A new install for me is about an hour. If I have partitioned in advance & have already downloaded ISO. I do have high speed Internet to download updates during install.
I do keep all data on a separate data partition and separately backup /home & the data partition. I use rsync to copy /home to preliminary backup on my other hard drive, but also backup to flash drives & DVDs for most critical data.
I also include configurations and now have most of the customization as scripts. After doing several installs, I realized I was doing the same thing over and over which I thought the computer should be doing. I tried to learn command line ways, not gui ways to configure system and then just copied history from terminal into text file and converted it to a bash script. Now most of my customization is running a couple of scripts which edit configuration files like grub, fstab & /etc/exports. And reinstall all my apps from exported list.
I also backup some system configuration files and copy them into /home, so my /home backup includes those files. 

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)

    
 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&p=7015603#post7015603](http://ubuntuforums.org/showthread.php?t=868244&p=7015603#post7015603)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
of course, do the dry run first 
      
 [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[URL="https://help.ubuntu.com/community/CronHowto"]https://help.ubuntu.com/community/CronHowto
[/URL]
 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[URL="http://ubuntuforums.org/showthread.php?t=1883834"]http://ubuntuforums.org/showthread.php?t=1883834

[/URL]
 Discussion of issues on rsync bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)
Sample rdiff file by TheFu
[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880)
[http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use](http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use)

[URL="http://ubuntuforums.org/showthread.php?t=1883834"]
[/URL]

[URL="https://help.ubuntu.com/community/CronHowto"]
[/URL]

---

### Post by saitoh183 on 2016-01-03
Im also looking for something like Elishasmantle is looking for. On Windows i backup my windows partition and my data (Folder backup)  on a schedule. So far everything i see on Linux seems to be only folder/file base for anthing that uses a schedule. If i want a partition/drive backup, it seems to be only live cd solutions (Clonezilla) with no real means of scheduling. I checked the links above but nothing seems to do the exact thing we need. (im probably wrong but im a newb still...lol). 

What im looking for is a solution that is on a schedule, that if i loose my system drive, i can boot with a live media and restore a image to the new drive and be up and running again. For my data, Fwbackup looks like it would fit my needs. Also i would like to know what i should backup data wise to make sure that when i restore , all my apps are in working order and my service accounts will be back. Here is my disk setup ...maybe it could help with suggestions:

[IMG]http://snag.gy/QlX6j.jpg[/IMG]

Im looking for the best way to backup on a schedule sda,sdd1,sdd5. I think those 3 would be the entire system. Also for restoring a single file, i could mount those images to be able to copy what i need without having to boot my system into a live cd/usb to get a single file.

Thanks! :)

---

### Post by ian-weisser on 2016-01-03
> **saitoh183 said:**
> ...everything i see on Linux seems to be only folder/file base for anthing that uses a schedule.
Perhaps you are limiting yourself to applications that call themselves "backup applications".
Copying an entire drive's files is merely one shell command, easily doable on any schedule you wish in cron.
Copying the entire drive's (or partition's) image is just as easy, one different shell command, optioanally triggered by cron..

There seem two questions here. Backup/restore methods and availability/shortest-downtime methods. It might be wise to separate them.

---

### Post by saitoh183 on 2016-01-03
> **ian-weisser said:**
> Perhaps you are limiting yourself to applications that call themselves "backup applications".
Copying an entire drive's files is merely one shell command, easily doable on any schedule you wish in cron.
Copying the entire drive's (or partition's) image is just as easy, one different shell command, optioanally triggered by cron..

There seem two questions here. Backup/restore methods and availability/shortest-downtime methods. It might be wise to separate them.


I think i need to lose my windows frame of mind ;). I think my real question is what folders and/or files do i need to backup in order to restore my system to its previous working state if i loose the machine altogether. What software would you recommend for the novice. I tried Deja-dup but im not crazy about the scheduling system. 

From exploring, i would say that what i need to back is the entire root and exclude media, mnt, tmp and Downloads folder. But im sure the mass have a more detail and granular scheme. Also i was looking for a software that would allow me to backup certain folder on different schedules (deja-dup cant). Also the "backup" needs to be something done live...no rebooting in a live media.

---

### Post by ian-weisser on 2016-01-03
> **saitoh183 said:**
> what folders and/or files do i need to backup in order to restore my system to its previous working state if i loose the machine altogether

It depends upon your skill level, your organization's policies and culture, the services you are running, your allowable downtime, and your budget.
There are sooooo many options.

If you're looking for restore-to-previous-working-state, then simply run your server in a Virtual Machine, and use the built-in snapshot/restore function.
A simple script can transfer the snapshot to your preferred backup archive,

If you're really asking about backup-full-state, that's harder. Don't use LVM or full-disk-encryption. Backup mostly data in /home and /var/<service>, and system settings in /etc. Never backup /proc nor /tmp nor /run. Backup any special local software in /usr/local and /opt. That's about it. The installer will fill in the rest when it creates your new system. Don't bother backing up applications from the Ubuntu repositories nor /bin nor the rest. After install is complete, just tell the package manager which top-level packages to install (apache2, mysql, etc). If you have hardware changes, you may need to edit /etc/fstab (storage) or /etc/udev (peripherals). Then restore your data and those other dirs/files from backup - mount your backup media and copy them over.

Tip: Backups aren't really backups untill you have tested restoring from them and know they work.

---

### Post by saitoh183 on 2016-01-04
> **ian-weisser said:**
> It depends upon your skill level, your organization's policies and culture, the services you are running, your allowable downtime, and your budget.
There are sooooo many options.

If you're looking for restore-to-previous-working-state, then simply run your server in a Virtual Machine, and use the built-in snapshot/restore function.
A simple script can transfer the snapshot to your preferred backup archive,

If you're really asking about backup-full-state, that's harder. Don't use LVM or full-disk-encryption. Backup mostly data in /home and /var/<service>, and system settings in /etc. Never backup /proc nor /tmp nor /run. Backup any special local software in /usr/local and /opt. That's about it. The installer will fill in the rest when it creates your new system. Don't bother backing up applications from the Ubuntu repositories nor /bin nor the rest. After install is complete, just tell the package manager which top-level packages to install (apache2, mysql, etc). If you have hardware changes, you may need to edit /etc/fstab (storage) or /etc/udev (peripherals). Then restore your data and those other dirs/files from backup - mount your backup media and copy them over.

Tip: Backups aren't really backups untill you have tested restoring from them and know they work.

Your Tip is true :)

I dont use LVM or disk encryption. Are there any hidden directories or files that shouldnt be taken?

I will keep your VM idea for another thread because i thought about using snapshots as a means to backup my server but im afraid of performance issues.

---

### Post by Elishasmantle on 2016-01-05
Hello,

GREAT INFO ian and oldfred. I am considering this resolved at this point because there is so much information here it will take a while to test it all out. 
I think I have all the info I need from looking briefly at it all and see I have several options and ways of doing things.

Thank You both for taking the time to give so much information. I know writing detailed posts can be time consuming. I much appreciate your efforts.

oldfred, I feel exactly like you do. I have been doing Windows IT support for 18 years and it only took about 1 week with Linux to see I was not going to put myself through the headache of not having backups and that I needed and that I was changing config files and knew I would forget some of the paths to these files if my system crashed and I would have to do it all over again from scratch. I like your idea of using terminal commands history for scripts, but am a little confused on that but will look at it in more detail when not so tired as then it may make more sense to me.

Thank You both again. I do appreciate it.

elishasmantle

---

### Post by oldfred on 2016-01-06
Part of issue is there are so many ways and similar applications to do just about anything in Linux. 

If after you have reviewed things and have a general question post again in this thread. I will see it as I use forum search on my username to find threads with new posts that I have previously posted in. If you decide on a specific method and want more info start a thread with that in the title and those that use it will offer to help.

For my home use I have liked rsync. But After reading multiple threads from TheFu on rdiff have thought about changing. But rsync has worked and changing ways is not as easy as it was.

---

