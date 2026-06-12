---
title: "Permissions for sources list files"
date: 2014-01-19
forum: Installation &amp; Upgrades
---

### Post by samwillc on 2014-01-19
HI,

I used this guide:

[http://askubuntu.com/questions/243387/how-can-i-backup-my-programs-applications-so-that-after-i-reinstall-a-new-one](http://askubuntu.com/questions/243387/how-can-i-backup-my-programs-applications-so-that-after-i-reinstall-a-new-one)

...for a quick reinstall so I didn't have to manually get all my software again one by one. However, I just dragged the sources.list and sources.list.d folder onto an external drive (via opening nautlius as standard, not via 'gksudo nautilus') and hoped I could just drag them back to the right place on once ubuntu was reinstalled. Wrong!

My permissions on these files are now all screwed so the steps from 6 onwards on the link above fail miserably. I have two questions then:

1) What are the correct permissions for the sources.list file and sources.list.d folder (and contained files)?
2) Can I run deja-dup as root in the first place to just make a backup of /home/ **and** /etc/apt/ so a reinstall would be a bit less painful.

I will look into clonezilla as that seems like a decent option but any help with the above would be most appreciated, thanks.

Sam.

---

### Post by TheFu on 2014-01-19
Backups as root are a must.  Without root, the permissions will be screwed.
Restoration as root is also a must. Without root, the permissions will be screwed.

Running any* GUI tool as root is dangerous. Don't do it. ....  [*] for certain values of "any"; gui tools often leave files behind with settings. Often, those settings will be stored under your userid, not /root/, so accessing them later as your normal ID will fail.

/etc is tiny and there are lots of things you want in there, not just /etc/apt/  Grab the entire thing in your backup process.

Oh and the permissions in /etc are root.root and 644. Which explains why you could copy, but not put them back under your normal userid.

Clonezilla rocks for many purposes, but it just isn't needed for Linux backups. It is extremely wasteful when you just need to install a basic system, put the settings back from /etc/, your data back where it goes (often /home ; occasionally /var) and tell the box to install all the old packages via dpkg --set-selections.  My profile has links to how I do this with scripts that I use.  

I use apt-cache-ng to prevent multiple downloads of the same package over the internet. It also means that reinstallations are much, much faster as almost every needed package is local already. That tool has a few issues, but seems to work well enough.

---

### Post by ajgreeny on 2014-01-19
If what you want is the packages you have previously installed to your system so that you can install them again to the new one, this is one situation where it is probably quicker and easier to use the terminal to copy what you want from your filesystem to a usb disk with command ```
cp /var/cache/apt/archives/*.deb /media/path/to/usb
```, and then copy them back to the filesystem of your new installation with ```
sudo cp /media/path/to/usb/*.deb /var/cache/apt/archives/
```
This is something I have done a lot and continue to do when necessary as it can save a lot of time downloading masses of packages that you have already in /var/cache.

---

### Post by samwillc on 2014-01-19
> **TheFu said:**
> Backups as root are a must.
Restoration as root is also a must.

/etc is tiny and there are lots of things you want in there, not just /etc/apt/  Grab the entire thing in your backup process.

Oh and the permissions are root.root and 644. Which explains why you could copy, but not put them back under your normal userid.


Thanks, that's helpful.

> **ajgreeny said:**
> If what you want is the packages you have previously installed to your system so that you can install them again to the new one, this is one situation where it is probably quicker and easier to use the terminal to copy what you want from your filesystem to a usb disk with command ```
cp /var/cache/apt/archives/*.deb /media/path/to/usb
```, and then copy them back to the filesystem of your new installation with ```
sudo cp /media/path/to/usb/*.deb /var/cache/apt/archives/
```
This is something I have done a lot and continue to do when necessary as it can save a lot of time downloading masses of packages that you have already in /var/cache.

Thanks for the info.

What about the /etc/ folder in this situation? How do you reinstall all the packages after the archives have been copied to the new install?

---

### Post by ajgreeny on 2014-01-19
After copying all the archived *.deb files back to your new filesystem you simply install them in the usual way, using software-centre or better, I think, synaptic, or terminal with **sudo apt-get install packagename**.  If you used the set-selections system etc etc that is shown in your link you can also do that to reinstall the packages.  All my copying suggestion will do is allow you to avoid downloading all those packages again.

Synaptic is always the first application I add to any *ubuntu system nowadays if it's not in by default as it is so much better, in my opinion, than software-centre.

---

### Post by samwillc on 2014-01-19
Ok, thanks. I am still working on a way to get a decent backup solution. I admit I don't use automatic stuff, I just manually backup every week or so, nothing much changes on my system once it's set up. OSX time machine was perfect for me but the whole lockdown on mac stuff really puts me off.

---

### Post by TheFu on 2014-01-19
> **ajgreeny said:**
> Synaptic is always the first application I add to any *ubuntu system nowadays if it's not in by default as it is so much better, in my opinion, than software-centre.

+1 - for desktops. I find software-center to be toooooo dumbed down to be touched. My systems are mostly servers, so GUI tools don't fit very often.

---

### Post by TheFu on 2014-01-19
> **samwillc said:**
> Ok, thanks. I am still working on a way to get a decent backup solution. I admit I don't use automatic stuff, I just manually backup every week or so, nothing much changes on my system once it's set up. OSX time machine was perfect for me but the whole lockdown on mac stuff really puts me off.

If you like "time machine" - check out "back-in-time" - .... this is suitable for individual user backups. Not so much for system stuff. For the system stuff, rbackup, duplicity, and rdiff-backup (all using librsync) are great choices.

We all start out doing backups manually. I would use ZIP files, then just a weekly rsync mirror to another partition in a different system. Did that manually every week for about 6 months ... nothing bad happened, so I got lazy. It happened monthly, then quarterly then .. some system changes prevented backups and I didn't have enough room to backup everything.
**Then it happened.**
A HDD failed. It was being merged with 2 other partitions on different HDDs using LVM into a single file system.  I lost all the data on all three of those disks.  That lead to ....
**I got backup religion.**
Never looked back. I am not afraid of a hardware failure anymore.  I am not afraid of accidentally deleting a file or having a program corrupt a file. My backups are THAT good.  I might loose 23 hrs of data that changed - worst case.  Doing backups the correct way is actually easier and automatic.  I check that backups finished on every box daily, but that's it. I get an email with any failures from each backup task. The backup storage is managed automatically. It is extremely efficient in time and storage. Most backups take 1-3 minutes and just 5MB of storage.  I know each backup set can be used to restore a system in about 30 minutes - had to do this a few times over the years.  Most of my systems have 60 days of backups, a few have 90 days. That means any backup during that time for any file can be restored. 1 file or a million. Doesn't matter. I can restore. 

If a box gets a virus and we don't notice for a week or two, I can drop back and see exactly what changed.  Backups are NOT just for HW failures, they are a critical security tool as well.

Also, I sleep very well too. ;)

While I'm here, rsync is a great tool and makes a mirror copy when that is needed. Let there be NO mistake, a mirror is NOT a backup. It fails on some of the most important parts of a good backup. There are more complex ways to get rsync to make a good backup tool, but most people are happy to use a derivative tool, based on rsync or librsync, to perform their backups.  Anyone using rsync for backups probably really wants to use rsnapshot or rbackup or back-in-time instead. Each of these will create timestamped backups that can be restored after a virus hits and more than 1 backup has happened since the attack. If you only have a mirror, then the modified file will likely be pushed to the backup storage BEFORE realizing that a virus has been successful.  Please learn from this.

Still, only you can decide what you need to protect your system(s). What works for others is NOT necessarily the best answer for you.  Starting with a simple backup script is 10% of the effort.  Backups aren't really the point. Don't loose sight of the real goal - restore.

---

### Post by ajgreeny on 2014-01-19
I find rsync or grsync ideal for backups to an external hard disk.  It does all my /home very regularly, but I don't bother with anything else very often, except for the contents of /var/cache/apt/archives which are copied occasionally to a folder in my /home and therefore backed up with the rest of my /home.

---

### Post by samwillc on 2014-01-22
Thanks everyone, gives me somewhere to start.

---

### Post by samwillc on 2014-01-23
Hi everyone,

Sorry to resurrect this but still not quite sure what to use here for a backup. Say I use sublime text 2, that is in /opt/. This would also involve changes in, for example:

```
sudo sublime /usr/share/applications/defaults.list
```
[FONT=verdana]
So I could double click files and they would open in sublime text 2. If I only backup /home/, /etc/ and /opt/, then what about the little changes here and there such as the above? I use things like ruby version manager (for sass) and python (/usr/bin/python).

If I was to backup the above folders, then reinstall ubuntu (or elementary os), then restore these folders, surely there would be gaps here and there for 100% similar functionality to before the reinstall? [FONT=verdana]This is where my confusion arises. I want to be able to restore and get going will minimal fuss. 'Back in time' seems ok for just the home folder but is it suitable for my needs? I also saw luckybackup but really not sure which to go for here.[/FONT]

I think I need some more advice here if possible. I am a single user only on this machine and will only be backing up to an external HDD via USB.

Thanks.
[/FONT]

---

### Post by TheFu on 2014-01-23
> **samwillc said:**
> Hi everyone,

Sorry to resurrect this but still not quite sure what to use here for a backup. Say I use sublime text 2, that is in /opt/. This would also involve changes in, for example:

```
sudo sublime /usr/share/applications/defaults.list
```
[FONT=verdana]
So I could double click files and they would open in sublime text 2. If I only backup /home/, /etc/ and /opt/, then what about the little changes here and there such as the above? I use things like ruby version manager (for sass) and python (/usr/bin/python).

If I was to backup the above folders, then reinstall ubuntu (or elementary os), then restore these folders, surely there would be gaps here and there for 100% similar functionality to before the reinstall? [FONT=verdana]This is where my confusion arises. I want to be able to restore and get going will minimal fuss. 'Back in time' seems ok for just the home folder but is it suitable for my needs? I also saw luckybackup but really not sure which to go for here.[/FONT]

I think I need some more advice here if possible. I am a single user only on this machine and will only be backing up to an external HDD via USB.

Thanks.
[/FONT]

For tools installed with synaptic/software-center or apt-get install and maintained that way, all you need is a list of packages. Already covered above.
For tools installed with a .deb file that YOU found on the internet - keep that .deb always. I don't install that sort of software, unless there is ABSOLUTELY NO OTHER CHOICE. Using a PPA is preferred, vastly.  This is like MS-Windows and a major failure for maintainability, IMHO
For tools that you compile and install using some other tool, well, then you've accepted the responsibility to manage that software manually going forward. Honestly, this is one of the reasons I stopped using Window and Slackware. ;)
For settings that get changed - where are those made?  /etc and ~/ somewhere.  Those areas should be in your backups.
For data, it is simple - you need to backup where ever that data resides.  If that is in /usr/local/ or /var/www  or /opt/ then those places need to be included. Only you KNOW where data is stored, not anyone else.
For databases, be certain to quiesce the DB to avoid DB corruption. MySQL has a dump method and those dumped files are safe to backup. For SQLite, I usually just shutdown the process using a specific DB file. Being unavailable for 2 minutes as a system backup happens is not a hardship for my users. I do this with my blog every night, for example.

I use rvm too.   My /home backup gets everything, so nothing special is needed.
On servers that don't have rvm, I'll grab a list of gems (gem list --local), so I can reinstall them later.  In theory, the .Gemfile and bundle would handle it, but just grabbing everything in /home is much easier.   

For perl, I use perlbrew - it is similar in goal to rvm. Grabbing a list of CPAN packages is handy.

While I'm at it, I grab the current hardware on the system too with **lshw**.  That way if something fails and it isn't notices immediately, I can find the date it happened in the backups.

These last few things happen via scripting and the output is shoved into a file in ~root/backups/.  I backup /root, just like it was a HOME.  Some of the data is sensitive, so putting it into /root is just a tiny bit safer than under my HOME.  After all, the backup job is already running as root away. ;)

So, my blog has a number of articles about backups - including a real script that I use to backup systems with rdiff-backup. There is also an exact command used to backup a largish server with lots-o-storage. It is basically the output from the script in 1 line starting with "rdiff-backup."  The key thing about most Linux backups is that the target storage needs to be Linux permissions capable.  NOT NTFS. NTFS will lose the user, group and other important permissions.

rdiff-backup is MY tool of choice. You'll need to decide if it is worth your time or not. There are many great tools out there.  Just be certain that the solution you end up with supports versioned backups. A mirror just isn't enough for many reasons.

Anyway, hope this helps.

---

### Post by samwillc on 2014-01-24
> **TheFu said:**
> For tools installed with synaptic/software-center or apt-get install and maintained that way, all you need is a list of packages. Already covered above.
For tools installed with a .deb file that YOU found on the internet - keep that .deb always. I don't install that sort of software, unless there is ABSOLUTELY NO OTHER CHOICE.
For tools that you compile and install using some other tool, 
For settings that get changed - where are those made?  /etc and ~/ somewhere.  Those areas should be in your backups.
For data, it is simple - you need to backup where ever that data resides.  If that is in /usr/local/ or /var/www  or /opt/ then those places need to be included.
For databases, be certain to quiesce the DB to avoid DB corruption.

I use rvm too.   My /home backup gets everything, so nothing special is needed.
On servers that don't have rvm, I'll grab a list of gems, so I can reinstall them later.  In theory, the .Gemfile and bundle would handle it, but just grabbing everything in /home is much easier.


Makes sense :)

> **TheFu said:**
> 
So, my blog has a number of articles about backups - including a real script that I use to backup systems with rdiff-backup. There is also an exact command used to backup a largish server with lots-o-storage. It is basically the output from the script in 1 line starting with "rdiff-backup."  The key thing about most Linux backups is that the target storage needs to be Linux permissions capable.  NOT NTFS. NTFS will lose the user, group and other important permissions.

rdiff-backup is MY tool of choice. You'll need to decide if it is worth your time or not. There are many great tools out there.  Just be certain that the solution you end up with supports versioned backups. A mirror just isn't enough for many reasons.

Anyway, hope this helps.

The permissions info is good to know. I usually use FAT32 on external drives as I never have single files that are that large. This has really helped, thanks.

Sam.

---

### Post by TheFu on 2014-01-24
> **samwillc said:**
> The permissions info is good to know. I usually use FAT32 on external drives as I never have single files that are that large. This has really helped, thanks.

FAT32 fails in the permissions department too.  If you want to use either NTFS or FAT32 for the target storage, use duplicity or something based on it.  Restores will be more of a hassle than with the other tools, but backup "sets" don't use the file system to store metadata about the owner, group and file permissions in duplicity.  Like I said, the downside is restore. With rsnapshot or rdiff-backup, restoring the most recent backup is just a copy - 1 file or an entire directory structure.  With duplicity - you'll have to open the tool and click to the file to be restored using the tool. Looking at the backup files on the file system is next to useless. The names mean nothing and end with numbers since everything gets chunk-ed to a specific file size.  Doing that is handy for remote backups to cloud storage, not-so-great for a 5 second restore of a corrupted file.

Pros and cons. Glad it helped.

---

### Post by samwillc on 2014-01-24
> **TheFu said:**
> FAT32 fails in the permissions department too.  If you want to use either NTFS or FAT32 for the target storage, use duplicity or something based on it.  Restores will be more of a hassle than with the other tools, but backup "sets" don't use the file system to store metadata about the owner, group and file permissions in duplicity.  Like I said, the downside is restore. With rsnapshot or rdiff-backup, restoring the most recent backup is just a copy - 1 file or an entire directory structure.  With duplicity - you'll have to open the tool and click to the file to be restored using the tool. Looking at the backup files on the file system is next to useless. The names mean nothing and end with numbers since everything gets chunk-ed to a specific file size.  Doing that is handy for remote backups to cloud storage, not-so-great for a 5 second restore of a corrupted file.

Pros and cons. Glad it helped.

The external drive can be any format I choose, so I could go for ext4, it's purely to backup linux and to restore to linux (I will not need to pull files from this to other computers). I've got other flash drives for things like pictures, photos, vids, stuff I move around to different computers that permissions are not important. However, I need the permissions to persist for the backup so I would presume ext4 would be safe. Please correct me if I'm wrong, but otherwise, you've been a great help, thanks.

---

### Post by samwillc on 2014-01-25
> **TheFu said:**
> Running any* GUI tool as root is dangerous. Don't do it. ....
[*] for certain values of "any"; gui tools often leave files behind with settings. Often, those settings will be stored under your userid, not /root/, so accessing them later as your normal ID will fail.

Ok, so I installed 'back in time' and am ready to backup so I can test  this first hand. @TheFu I remembered you mentioning the above. This may be a simple question but there are 2 options,  run and run (as root). Now I want to backup:

/home/
/usr/etc/
/usr/share/bluej/
/opt/

So how do I go about this with this program? /home/ doesn't need root, but the others do. So if I backup as root, all the files in my home directory will have different ownership if I try and restore? Does this mean I need to run the program twice, once normal, and once as root to backup my desired folders?

I want to backup, then reinstall straight away to test I've got this down correctly before I make various changes (rvm, python etc.). The whole thing is so confusing. I appreciate the help and hope to get a good method in place soon so I can get on with some actual work at some point and stop adding to this thread!

Sam.

---

### Post by TheFu on 2014-01-27
If you are new to Linux and don't have a good grasp of permissions and ownership, then making Back-in-Time work for full system backups will not be easy.  It is great for backing up directories all owned by the same user - 1 user's HOME - but not much else.  As I said before, using a GUI program with sudo will modify settings files. Back-in-time DEFINITELY does this.  If you still think this is the tool to be used, please check out their website and guides.  I used Back-in-Time on my Mom's linux system for a few years for local backups.  It was easy for her to understand. For the real, remote, backups, I used rdiff-backup. 

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) has some other options and some discussion links at the bottom.  From that last post, I fear your restore attempts will fail. Not all the concepts necessary to be successful seem to have "clicked" yet. We'll get there. It takes a little time.

Are you avoiding CLI programs?  Eventually, you will need to make backups run from the root crontab and GUI tools can't do that. Best to start with a little script now, I think.

When the root userid backs up files, the original ownership, group are maintained.  When a non-root userid backups up files, the process owner takes control of the file ownership.  Only the root userid (or an equivalent, but that is a different technique) can do this.  Even /home needs to be backed up as root, if there is more than 1 userid on the system.  The /home directory has specific ownership and permissions that cannot be for a single end-userid.

So, just to get you started .... I have no idea if this is all that needs to happen. Usually I shutdown a few services before doing a backup and capture some other system, package, data before starting ... anyway, here's a script to get you started:

```
#!/bin/bash
# #######################################################
# 
#  Backup_to_xyz.sh
#  Purpose: Capture important system files, settings and 
#           back them up to local directory. This is a simple script.
#  Author: jdpfu.com
#  Date: 1/27/2014 (last update for ubuntu forums)
#  Date: 10/23/2011
#  Date: 10/22/2010 
#  Date: 3/1/2007 (original)
# #######################################################
TARGET_DIR=/Backups  # set this to your backup partition location. Must be mounted already and appear as a local file system.
RETAIN_DAYS=30D
RDB=/usr/bin/rdiff-backup
MKDIR=/bin/mkdir
RM=/bin/rm

INCLUDE="--include /etc \
--include /home \
--include /usr/local \
--include /usr/etc \
--include /usr/share/bluej \
--include /opt"

EXCLUDE="--exclude-special-files \
--exclude **/.cpan \
--exclude **/.cache \
--exclude **/.kde/share/apps/kpdf \
--exclude **/.gkrellm2 \
--exclude **/.miro/icon-cache \
--exclude **/.miro/mozilla \
--exclude **/.smplayer/screenshots \
--exclude **/.mozilla-thunderbird \
--exclude **/.vlc \
--exclude **/*.mp4 \
--exclude **/.mozilla/firefox/*/chrome/sagetoo \
--exclude **/.mozilla/firefox/*/sessionstore \
--exclude **/.mozilla/firefox/*/Cache"

# Remove all flash files and cache
$RM -rf ${HOME}/.macromedia/* ${HOME}/.adobe/*

# ensure the target directory exists - manually need to ensure this area has enough storage.
$MKDIR  -p "$TARGET_DIR/$HOSTNAME"

#### Do the backups
$RDB $EXCLUDE $INCLUDE "$TARGET_DIR/$HOSTNAME"

#### Delete backups over X days old
$RDB --remove-older-than $RETAIN_DAYS --force "$TARGET_DIR/$HOSTNAME"

```

I didn't run it - my system is different. Use sudo to run this and be certain to meet the prerequisites in the script. Anyway, this should get you started.

---

### Post by samwillc on 2014-01-27
Hi,

Last night I decided not to use 'back in time' or 'luckybackup' (or any GUI) for the reasons you gave before. I wrote this (.myBackup.sh saved in home folder - set as 755) before reading your post above so I could test things out:

```
#!/bin/sh

DEST_DIR=/media/eOS_BACK/

dpkg --get-selections > package_list
sudo rsync -av --delete /home/sam $DEST_DIR
sudo rsync -av --delete /etc $DEST_DIR
sudo rsync -av --delete /usr/share/bluej $DEST_DIR
sudo rsync -av --delete /opt $DEST_DIR
```

Ran it with my external HDD mounted and got a copy going (with preserved permissions as far as I can see). Ok, its basic but it's a start! I haven't tried rdiff yet.

The obvious problem I see with my code is that this is just a mirror, and not incremental. And --delete serves little purpose to me as sometimes I want to keep files on the external drive, old invoices for example, i.e. a proper archive, not merely synced with current files.

So I was reading this:

[http://www.mikerubel.org/computers/rsync_snapshots/#Rsync](http://www.mikerubel.org/computers/rsync_snapshots/#Rsync)

...and got a bit lost. What I was maybe hoping to achieve in the future was something more like this, with identical folder structure:

(1st backup)
24-01-2014 (folder)
 - sam
 - etc
 - usr/share/bluej
 - opt

(2nd backup)
27-01-2014 (folder)
 - sam
 - etc
 - usr/share/bluej
 - opt

With the 2nd backup only containing links to the original files in backup 1 if nothing has changed, and if something HAS changed, then instead of a link, the actual file (so it LOOKS like two folders that contain almost the same thing - but approx. half the size on the disk). If that makes any sense. I'm not sure if this is even a good idea (or achievable with my current ability) and I have yet to try your script which I will do later on (I presume I also need to install rdiff). Thanks for the help so far.

Sam.

---

### Post by TheFu on 2014-01-27
I would use {yyyy}-{mm}-{dd}/ folders, if that is your intent. Sorts better by the most important part. **man date** will explain how to get that output format - something like `date "+%Y-%m-%d"` I think.

Don't forget to clean up the the old backup directories.

**rsnapshot** uses "hard links" to do what you want. No need to reinvent this wheel, unless you really want to. Hardlinks are cool and have some neat tricks. They have limitations too that are important to understand with backups - like hardlinking only works on the same file system and only 1 set of file permissions is stored, so changes to those over time are lost.

rdiff-backup does NOT use hardlinks, but achieves something very close to what you seem to desire.  Just for fun, run rdiff-backup on something small a few times, making tiny changes (add a space to a file) between the runs. Then look at the target location to understand how it works. I think you will be impressed.  So try this:
```
sudo mkdir -p /Backups/$hostname
sudo rdiff-backup /etc /Backups/$hostname
```
look around in the target and when you are done, delete /Backups/$hostname. No harm done. Doing this on a small area means no real commitment, but you can still learn how things work.  Do the same for rsnapshot or any other rsync-based tool. See how the backups appear. Learn about the restore process for each.  

Oh - and I see a small issue with my script - ${HOME} will not be set as expected, probably.
I see an issue with yours too - what will the CWD be when you put the script into a crontab?  Best to always fully specify the complete path to any files used in scripts - that goes for commands too.  The following line has 2 failures:
```
dpkg --get-selections > package_list
```
See them?

---

### Post by samwillc on 2014-01-27
> **TheFu said:**
> rdiff-backup does NOT use hardlinks, but achieves something very close to what you seem to desire.  Just for fun, run rdiff-backup on something small a few times, making tiny changes (add a space to a file) between the runs. Then look at the target location to understand how it works. I think you will be impressed.  So try this:
```
sudo mkdir -p /Backups/$hostname
sudo rdiff-backup /etc /Backups/$hostname
```
look around in the target and when you are done, delete /Backups/$hostname. No harm done. Doing this on a small area means no real commitment, but you can still learn how things work.  Do the same for rsnapshot or any other rsync-based tool. See how the backups appear. Learn about the restore process for each.


Sounds good, I will try this at the weekend when I've got some time.

> **TheFu said:**
> 
I see an issue with yours too - what will the CWD be when you put the script into a crontab?  Best to always fully specify the complete path to any files used in scripts - that goes for commands too.  The following line has 2 failures:
```
dpkg --get-selections > package_list
```
See them?

I just ran this script out of home. Don't know what a crontab is although I am aware of cron making jobs automated, no real technical knowledge of it though.

2 failures? I can only throw in a few guesses...

Needs to run as sudo? Underscore in filename? No file extension on package_list? I don't even know what the '>' does, this line is from an ubuntu forums post that looked useful for restoring my packages after a reinstall. I did not write this line myself because I never knew you could even do this.

As you can probably work out, I am no expert but always willing to learn new things.

---

### Post by TheFu on 2014-01-27
You are doing really well. I'm happy to help _teach you how to fish_!

> **samwillc said:**
> Sounds good, I will try this at the weekend when I've got some time.

I just ran this script out of home. Don't know what a crontab is although I am aware of cron making jobs automated, no real technical knowledge of it though.

2 failures? I can only throw in a few guesses...

Needs to run as sudo? Underscore in filename? No file extension on package_list? I don't even know what the '>' does, this line is from an ubuntu forums post that looked useful for restoring my packages after a reinstall. I did not write this line myself because I never knew you could even do this.

As you can probably work out, I am no expert but always willing to learn new things.

Interactive shells behave differently from crontab environments.   CWD - current working directory. That will not be set when used in a crontab, so you cannot assume where any file will be written ... ore more likely where permissions will fail to allow it to be written. 
**dpkg --get-selections > package_list**
Always fully specify the complete path to any programs AND to any files used in scripts. Those are the 2 failures. Most of the time, dpkg will be found, so that will work, but how do you know exactly which dpkg is used? There can be a few on any system and we want /usr/bin/dpkg .. not something else. 

Which "package_list" file do you want to store the output into?  It needs a full path - also, it would be handy if that output file were somewhere in your backup directories, right?  /home/{insert-userid}/package_list is probably what you mean.  Don't forget this will be running as root most of the time, so that file will be in YOUR HOME, but owned by root.

In a terminal, run **dpkg --get-selections|more** just to see what the command does. It is safe.

The '>' takes the "standard output" - that is a specific term with a specific meaning - and redirects it to a file. There is something called "standard error" which also goes to the console, but not to the same "file", so errors will not be redirected to your file. Kinda cool and sometimes a big hassle.  If you want to both see the output AND store it into a file, use **tee**.

After all that, the better line is:
**/usr/bin/dpkg --get-selections > /home/samwillc/package_list**
Make sense?
Now we are fishing!

---

### Post by samwillc on 2014-01-27
> **TheFu said:**
> You are doing really well. I'm happy to help _teach you how to fish_!

Interactive shells behave differently from crontab environments.   CWD - current working directory. That will not be set when used in a crontab, so you cannot assume where any file will be written ... ore more likely where permissions will fail to allow it to be written. 
**dpkg --get-selections > package_list**
Always fully specify the complete path to any programs AND to any files used in scripts. Those are the 2 failures. Most of the time, dpkg will be found, so that will work, but how do you know exactly which dpkg is used? There can be a few on any system and we want /usr/bin/dpkg .. not something else. 

Which "package_list" file do you want to store the output into?  It needs a full path - also, it would be handy if that output file were somewhere in your backup directories, right?  /home/{insert-userid}/package_list is probably what you mean.  Don't forget this will be running as root most of the time, so that file will be in YOUR HOME, but owned by root.

In a terminal, run **dpkg --get-selections|more** just to see what the command does. It is safe.

The '>' takes the "standard output" - that is a specific term with a specific meaning - and redirects it to a file. There is something called "standard error" which also goes to the console, but not to the same "file", so errors will not be redirected to your file. Kinda cool and sometimes a big hassle.  If you want to both see the output AND store it into a file, use **tee**.

After all that, the better line is:
**/usr/bin/dpkg --get-selections > /home/samwillc/package_list**
Make sense?
Now we are fishing!

I went fishing before, only thing I caught was my finger on the hook! I admit all this is quite exciting, terminal is awesome all the stuff you can do with such ease (relatively speaking). I do appreciate how important backups are, I lost a whole drupal site a few weeks ago because I switched computers and forgot to back up the database, locally stored only. That moment when you realise there is NO return is not a feeling I wish to repeat any time soon :)

I will try out your suggestions when I get a free moment, right now I'm bogged down in learning OOP aka java hell. I more than appreciate you taking time out to help me here.

---

### Post by TheFu on 2014-01-27
[http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use](http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use) - read the 1st comment for how to backup a mysql database.
Don't trust any backup method we've discussed to handle a real DB correctly unless you shutdown the DBMS first. Using the technique in that link, the DBMS can stay up and you'll still get the backup you need.

I've been doing OOP since 1992-ish.  Never bothered to learn Java - always seemed slow. It hasn't gotten much better that I can tell and with Oracle at the helm ... well ... we don't use anything based on Java if we can avoid it. Only php is worse according to our CSO.

Haven't written anything OO except in Perl and Ruby the last decade - after years of C/C++.

BTW, don't forget to backup all the system crontabs.  Those are in /var/spool/cron/crontabs ... somewhere, methinks. As we setup more and more automatic things, the crontab becomes more and more important.  Of course, you can also put cron-jobs in /etc/cron.*/ folders - if running at an exact time isn't needed, but "sometime" today or this week is better. For servers, I want things to happen at specific times, but for a laptop _today_ is fine - even better.

---

### Post by samwillc on 2014-01-27
Thanks. You've given me a lot to think about, and to action of course. Looking forward to trying some of this stuff out.

---

### Post by samwillc on 2014-02-12
> **TheFu said:**
> So, just to get you started .... I have no idea if this is all that needs to happen. Usually I shutdown a few services before doing a backup and capture some other system, package, data before starting ... anyway, here's a script to get you started:

```
#!/bin/bash
# #######################################################
# 
#  Backup_to_xyz.sh
#  Purpose: Capture important system files, settings and 
#           back them up to local directory. This is a simple script.
#  Author: jdpfu.com
#  Date: 1/27/2014 (last update for ubuntu forums)
#  Date: 10/23/2011
#  Date: 10/22/2010 
#  Date: 3/1/2007 (original)
# #######################################################
TARGET_DIR=/Backups  # set this to your backup partition location. Must be mounted already and appear as a local file system.
RETAIN_DAYS=30D
RDB=/usr/bin/rdiff-backup
MKDIR=/bin/mkdir
RM=/bin/rm

INCLUDE="--include /etc \
--include /home \
--include /usr/local \
--include /usr/etc \
--include /usr/share/bluej \
--include /opt"

EXCLUDE="--exclude-special-files \
--exclude **/.cpan \
--exclude **/.cache \
--exclude **/.kde/share/apps/kpdf \
--exclude **/.gkrellm2 \
--exclude **/.miro/icon-cache \
--exclude **/.miro/mozilla \
--exclude **/.smplayer/screenshots \
--exclude **/.mozilla-thunderbird \
--exclude **/.vlc \
--exclude **/*.mp4 \
--exclude **/.mozilla/firefox/*/chrome/sagetoo \
--exclude **/.mozilla/firefox/*/sessionstore \
--exclude **/.mozilla/firefox/*/Cache"

# Remove all flash files and cache
$RM -rf ${HOME}/.macromedia/* ${HOME}/.adobe/*

# ensure the target directory exists - manually need to ensure this area has enough storage.
$MKDIR  -p "$TARGET_DIR/$HOSTNAME"

#### Do the backups
$RDB $EXCLUDE $INCLUDE "$TARGET_DIR/$HOSTNAME"

#### Delete backups over X days old
$RDB --remove-older-than $RETAIN_DAYS --force "$TARGET_DIR/$HOSTNAME"

```

I didn't run it - my system is different. Use sudo to run this and be certain to meet the prerequisites in the script. Anyway, this should get you started.

Just a quick thanks for introducing me to rdiff-backup. I am building a new pc and will install linux over the weekend. Of course, now's my chance to get a backup from this pc and try and restore files/apps onto the brand new one, fingers crossed.

This may seem like a silly question but I removed a bunch of packages when I first installed elementary, namely midori, geany, noise and a few others. So I create a package list which I will use for my reinstall. Now when I do a fresh install of elementary, these original packages will be present. When I reinstate my packages using the generated package list, will the ones on the list be added (i.e. on top of midori, geany etc) or will the original packages be removed so I'm left with only the ones on the package list?

---

### Post by TheFu on 2014-02-12
> **samwillc said:**
> Just a quick thanks for introducing me to rdiff-backup. I am building a new pc and will install linux over the weekend. Of course, now's my chance to get a backup from this pc and try and restore files/apps onto the brand new one, fingers crossed.

This may seem like a silly question but I removed a bunch of packages when I first installed elementary, namely midori, geany, noise and a few others. So I create a package list which I will use for my reinstall. Now when I do a fresh install of elementary, these original packages will be present. When I reinstate my packages using the generated package list, will the ones on the list be added (i.e. on top of midori, geany etc) or will the original packages be removed so I'm left with only the ones on the package list?

Yes, rdiff-backup is pretty great. There are other fantastic tools too. Each has different trade-offs.  I really like the idea of duplicity, but hate parts of the implementation.  rsnapshot and rbackup can be great too, for certain uses. There is always rsync to be used when you just want a mirror, not versioned backups too.

I honestly do not know the answer to your question.  All my systems begin as **Ubuntu Server with just ssh**; no gui.  When the list of packages gets *selected*, only those will be added back.  Then I run an **ansible-playbook** for the system or a minimal playbook if it is something completely new that I've never built previously. Those playbooks will purge and add specific packages as I've already decided. Ansible is a little overkill for just one box, but I have about 20 and like certain things to be 100% consistent across all of them.  Automation via Ansible is perfect for that, IMHO, without all the setup hassles of Puppet.

So ... when restoring from my minimal backups, I do something like this:
[LIST=1]
[*] reinstall the base OS (ssh-server only),
[*] update/dist-upgrade with **aptitude**,
[*] restore the backed up data areas (/usr/local, /home, whatever is in the backups)
[*] reinstall all listed packages,
[*] purge any packages like nano, gedit, compiz, unity-asset-pool, geoclue* (this is automatic via Ansible),
[*] put any crontabs back
[*] install all listed cpan, ruby-gems and other modules (if perlbrew or rvm aren't used)
[*] run a fresh backup!
[/LIST]

Doing that takes about an hour. The restore process needs to be script-able, so it works at 4am.  That script can be a program or simple steps to follow.

---

### Post by samwillc on 2014-02-12
> **TheFu said:**
> So ... when restoring from my minimal backups, I do something like this:
[LIST=1]
[*] reinstall the base OS (ssh-server only),
[*] update/dist-upgrade with **aptitude**,
[*] restore the backed up data areas (/usr/local, /home, whatever is in the backups)
[*] reinstall all listed packages,
[*] purge any packages like nano, gedit, compiz, unity-asset-pool, geoclue* (this is automatic via Ansible),
[*] finally install all listed cpan, ruby-gems and other modules (if perlbrew or rvm aren't used)
[/LIST]

Doing that takes about an hour. The restore process needs to be script-able, so it works at 4am.  That script can be a program or simple steps to follow.

Great! I have to admit I haven't got round to making a restore script. Not 100% on how I'm going to run my backup in reverse but a fresh install is probably a better time than most to be able to screw things up and for it not to matter too much. Other than than the time it takes to reinstall and try again. It's a learning process!

I actually sold my macbook in order to fund this new build thus only running linux right now. Been great so far, feel kind of free in a funny way and of course that there's an awful lot of great support on this forum helps.

---

### Post by samwillc on 2014-02-15
Jeez, still trying to do this! Trying to keep it very simple, so got this:

```

#!/bin/bash

TARGET_DIR=/media/BACKUP/Backups
RDB=/usr/bin/rdiff-backup
MKDIR=/bin/mkdir

INCLUDE="
--include /etc \
--include /usr/local \
--include /usr/etc \
--include /usr/share/bluej \
--include /opt \
"

# Create packages list
/usr/bin/dpkg --get-selections > /home/sam/package_list

# ensure the target directory exists
$MKDIR -p $TARGET_DIR

#### Do the backups
$RDB $INCLUDE $TARGET_DIR

```

And it wont run.

```

sam@sam-pc:~$ sudo sh .backmeup.sh
Fatal Error: Switches missing or wrong number of arguments
See the rdiff-backup manual page for more information.

```

I don't know what the problem is. sublime_text_2 folder is in opt so I need that. I built a new pc which is just sitting there raring to go but I need a backup to use for my restore, and failing miserably here! :(

Any help is very much appreciated. Not quite tearing my hair out here but getting close. My new pc is screaming at me to hurry up!

Sam.

*EDIT*

Also, what are the permissions on the actual folder where the backups are contained i.e '/media/BACKUP/Backups'. At present if it is created, the owner and group are both 'root'. This means I can't drag and drop any single files out of my backup with running 'gksudo pantheon-files' first. Is this intended behaviour?

---

### Post by TheFu on 2014-02-15
The "INCLUDE" line need a trailing \

Permissions during backup are locked down. After backup completes, they match the source.

I'm NOT a fan of running ANY GUI program with root authority.

Is the target file system Linux?

---

### Post by samwillc on 2014-02-15
@TheFu, thanks for the quick response.

> **TheFu said:**
> The "INCLUDE" line need a trailing \

Not sure where this goes. Where exactly in the script?

> **TheFu said:**
> Permissions during backup are locked down. After backup completes, they match the source.

Ok :)

> **TheFu said:**
> I'm NOT a fan of running ANY GUI program with root authority.

Is the target file system Linux?

Yeah, ext4 external HDD, just for backups. Some of the files, for instance .bash_history which is in home I just wanted to be able to open and view so I can remember the many steps I took so set everything up. But I can't access the backups folder on the external HDD because of permissions.

Sam.

---

### Post by TheFu on 2014-02-15
You have
```
INCLUDE="
--include /etc \
--include /usr/local \
--include /usr/etc \
--include /usr/share/bluej \
--include /opt \
"
```

That will not work. You need a line continuation character - the \ as the very last character for any line that continues to the next line. No other characters or spaces can come after that.
```
INCLUDE=" \
--include /etc \
--include /usr/local \
--include /usr/etc \
--include /usr/share/bluej \
--include /opt \
"
```
See the diff? It is a common mistake that everyone makes all the time - noob or 20 yrs later. ;)

---

### Post by samwillc on 2014-02-15
Oh I see, thanks. Will try again :)

---

### Post by samwillc on 2014-02-15
Still not working:

```

#!/bin/bash

TARGET_DIR=/media/320GB_EXT/Backups
RDB=/usr/bin/rdiff-backup
MKDIR=/bin/mkdir

INCLUDE=" \
--include /home \
--include /etc \
--include /usr/local \
--include /usr/etc \
--include /usr/share/bluej \
--include /opt \
"

# Create packages list
/usr/bin/dpkg --get-selections > /home/sam/package_list

# ensure the target directory exists
$MKDIR -p $TARGET_DIR

#### Do the backups
$RDB $INCLUDE $TARGET_DIR

```

Getting:

```

sam@sam-pc:~$ sudo sh .backmeup.sh
[sudo] password for sam: 
Fatal Error: Switches missing or wrong number of arguments
See the rdiff-backup manual page for more information.

```

What's wrong with it? Package list is created, the backup directory is created so it fails on the last line.

```

$RDB $INCLUDE [NEED-ANOTHER-COMMAND-HERE?] $TARGET_DIR

```

Do I need to set a source still or something? I thought that was handled by setting which folders to include.

Sam.

---

### Post by TheFu on 2014-02-15
Try printing the command out, then using that directly to troubleshoot. Did you check the manpage for recent changes to the command or a bug?

Also, why run the command as "sudo sh .backme....."?  That is spawning an extra process - wasteful.

I'd run it as 'sudo /full/path/to/.backme.... ' and provided the permissions on the script are set to allow read and execute, it should work.

As to permissions to access /media/backups ... that has NOTHING to do with rdiff-backup. That is controlled by the mountpoint permissions. Fix those to be what you want.  I prefer to avoid using mounts under /media since that is where Ubuntu mounts temporary stuff.

---

### Post by samwillc on 2014-02-15
I got it to work in the end like this:

```

#!/bin/bash

TARGET_DIR=/media/320GB_EXT/Backups
RDB=/usr/bin/rdiff-backup
MKDIR=/bin/mkdir

INCLUDE="\
--include /home \
--include /etc \
--include /usr/local \
--include /usr/share/bluej \
--include /opt \
"

EXCLUDE="\
--exclude / \
--exclude /home/sam/.gvfs \
"

# Create packages list
/usr/bin/dpkg --get-selections > /home/sam/package_list

# ensure the target directory exists
$MKDIR -p $TARGET_DIR

#### Do the backups
$RDB $INCLUDE $EXCLUDE / $TARGET_DIR

```

Given up caring if it's correct or not, just wanted a backup! The above gave me what I need for the new pc.

> **TheFu said:**
> I prefer to avoid using mounts under /media since that is where Ubuntu mounts temporary stuff.

I don't know what you mean here. When I plug my drive in, the path is always 'media/DRIVE_LABEL', in this case 'media/320GB_EXT'.

---

### Post by TheFu on 2014-02-16
> **samwillc said:**
> I got it to work in the end like this:

Given up caring if it's correct or not, just wanted a backup! The above gave me what I need for the new pc.

I don't know what you mean here. When I plug my drive in, the path is always 'media/DRIVE_LABEL', in this case 'media/320GB_EXT'.

Congrats!

That automatic mount location ... well .... I consider THAT MAJOR a bug.  Automatic mounting is a security issue on UNIX systems for many reasons.Which you'll probably learn over years. I always disable it and control the mount locations and options carefully. Of course, other people have different opinions and clearly Canonical has deemed this to not be an issue. It is your choice.  On a single-user, physically control machine, I wouldn't worry too much.

Easier and convenient is seldom "more secure."

---

### Post by samwillc on 2014-02-16
I use elementaryOS and you have to click on the external drive in the pantheon files sidebar to mount them which suits me ok, no auto mount. Up and running now on new pc, ethernet didn't work OOTB ([http://forums.linuxmint.com/viewtopic.php?f=90&t=144088](http://forums.linuxmint.com/viewtopic.php?f=90&t=144088)). The only nvidia drivers in the 'additional drivers' popup was version 304. I've got a GTX 650 so I would have thought a newer version would be available for this. My BIOS is also pretty old. However, as the old saying goes "if it aint broke, dont fix it!". Everything works and is reinstalled from my HDD. Now just gotta fire up dosbox and get some retro gaming going on!

Thanks for all the help :)

---

