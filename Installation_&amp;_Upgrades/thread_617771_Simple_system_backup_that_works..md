---
title: "Simple system backup that works."
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by stepheny on 2007-11-19
Having recently been let down by [mondorestore in Gutsy]("http://ubuntuforums.org/showthread.php?t=615751&highlight=mondo") I have been researching a new backup strategy. I didn't want to leave myself again trusting in a tool which lets you down when you really need it, so the stategy had to use readily available and trustworthy software. The solution I have decided upon and tested by doing several complete restores is as follows:

**Backing up**.
Firstly you need to copy your home directory using sudo grsync (preserve time, owner, permissions and group) or 
```
sudo rsync -r -t -p -o -g -v --progress -l /home/ /media/disk/home/ 
```

Keep a copy of this somewhere so that you can find it when your system dies, ie on an external drive. Sync it regularly, rsync will only update changes to the original so after the first copy has been made, updates usually only require a few seconds.

Then make a list of all of the packages in your installation using the command 

```
sudo dpkg --get-selections | grep '[[:space:]]install$' | \awk '{print $1}' > package_list
```

Copy this file together with /etc/apt/sources.list to the same medium you have used for your /home/ directory backup.

You could initiate a cron job to keep this list up-to-date using by putting the following script in /etc/cron/dailypackage_list and making it executable.

```
#!/bin/sh
sudo dpkg --get-selections | grep '[[:space:]]install$' | \awk '{print $1}' > package_list
```

**Restoring.**
First boot the live cd and install Ubuntu.

After Ubuntu has rebooted to the HD version set up the restricted drivers for your graphics card if applicable, there is no need to reboot yet. Then replace the existing sources list with the one from your lost system. assuming that it is on an external disk (together with the /home/ directory backup) you would use

```
sudo mv /media/disk/sources.list /etc/apt/sources.list
sudo apt-get update
```

Then update the packages using:

```
cat /media/disc/package.list | xargs sudo apt-get install
```

If you are using some unauthorized packages you will get the following warning 

"WARNING: The following packages cannot be authenticated!
  libxxx libxx libx xxxplayer
  skype-common skype xxxcodecs
Install these packages without verification [y/N]? E: Some packages could not be authenticated"

for some reason you cannot answer yes or no to this, it's a bug. So simply install all of these packages using

```
sudo apt-get install libxxx libxx libx xxxplayer skype-common skype xxxcodecs
```

When that has completed run 

```
cat /media/disc/package.list | xargs sudo apt-get install
```

again and this time it should complete without problems.

Now copy your /home directory to the new system using sudo grsync (preserve time, owner, permissions and group) or 

```
sudo rsync -r -t -p -o -g -v --progress -l /media/disk/home/ /home/ 
```

That's it! You need to reboot and your system should be exactly as it was. I have tested this three times without problems.

---

### Post by scorp123 on 2007-11-19
[http://ubuntuforums.org/showthread.php?p=3795689#post3795689](http://ubuntuforums.org/showthread.php?p=3795689#post3795689)

[http://linuxmint.com/forum/viewtopic.php?t=3969](http://linuxmint.com/forum/viewtopic.php?t=3969)

---

### Post by SilverWave on 2008-01-25
I have tried all the obvious backup solutions and have not been happy with any of them - for various reasons.

So via a problem I was researching with mondo I saw this post...

I have came to the same conclusion as your self that simplicity is the key.
I think there are just to many variables with mondo its too complex.

Also the idea of not having to backup all the packages is a brilliant insight!

Thanks for this system very much appreciated :)

---

### Post by dasbooter on 2008-03-16
I know this thread is kind of old but I wonder if the original author has any comment on sbackup. It seems very similar to what is suggested here but uses a gui. This sort of method seems like a good idea (many now have a good internet connection to restore packages) .It appears development of sbackup is dead, too bad [[COLOR="Red"]sbackupHomePage[/COLOR]]("http://sbackup.sourceforge.net/HomePage"). When making a backup with sbackup it appears the method also makes a text file recording all your packages.It schedules fulls and incrementals and compresses it all up for you. I still long for a system that I could use to make a bootable dvd that you can throw in the computer and it restores automatically everything and reboots the system.

The thing with sbackup is I wonder if I could use it to backup only my home directory and not the whole root directory ( / ) which I am doing now . I wonder if you could do something like backup home and the repository sources file with sbackup and if I ever had to restore just throw in the ubuntu install cd then install sbackup and restore home and sources and then use the text file to restore all the packages. The only thing I am wondering about are the files that hold settings for various parts of the system that are not in your home folder. I suppose things like samba and all that would have to be reconfigured which is time consumptive... I think it is all about the time used. Just some thoughts. I can post a few screen shots of what you get when you use sbackup if someone would like

---

### Post by stepheny on 2008-03-31
Hi, I'm still here however I don't have any experience of Sbackup. I used Mondo/Mindi for years until last year  when I tried to restore my system only to find that it didn't work despite Mondo compare telling me the dvd was good. I then decided I would use the strategy I describe above and this works for me. I feel safe with this solution so I am not looking for anything else.

---

### Post by szandor on 2008-04-20
the thing i like about mondo is that it backs up my whole installation to a bootable reinstallation dvd. all i need to do is throw in the dvd, reboot, select nuke, and my system is restored. mondo works great in fedora 8 but it's unfortunate it does not work in gutsy. i have a couple of questions/comments about a complete hard disk backup. i had an idea but not sure if anyone has tried it. i've already hosed my ubuntu system once not knowing about the mondo issue so i thought i'd throw this idea out here first. i'm thinking i could nfs mount my ubuntu gutsy drive to my fedora system and run mondoarchive on the nfs mount. for example:

ubuntu system:
add / to /etc/exports
add fedora system in /etc/hosts.allow
exportfs -r

fedora system:
mount ubuntu / to /mnt/ubuntu_drive
run mondoarchive
backup /mnt/ubuntu_drive only

now if there's a problem with grub or other discrepancies, i was thinking you could run magiciso or something and manually add/edit files in the ISO file. after getting it working the first time, you could write a script to do this automatically. 

you know, it may just be easier to wait until mondo works in ubuntu 7.10 and up. i just can't see myself using another method. it takes about 15-20 minutes to back up my fedora drive to a bootable dvd and completely reinstall my system from the dvd. i could jack up my system playing around, etc, and just pop in a dvd and be back in business. szandor is saddened that mondo fails in gutsy.

---

### Post by mdpalow on 2008-04-20
You could always try QuickStart. It does back-ups and Sync for Ubuntu. See signature below for link..

---

### Post by stepheny on 2008-04-21
As I have said I used Mondo/Mindi successfully for over nine years and feel especially let down because under Gutsy my DVD's compared ok but when I needed them they were useless. After this experience I have absolutely no intention of ever using Mondo again. 

Waiting until Mondo  works in Gutsy (it's been about a year now hasn't it?) and then delaying your upgrade to 8.04 until Mondo works with that seems to be the wrong strategy to me. Who's to say it will ever work in Gutsy?

I am also wary of again using any  software which relies on libs that are used by other applications.

I am happy with my simple method which has saved my bacon several times and which I can trust completely. In the case of a disaster (which doesn't happen very often with Ubuntu :-) ) I can surely spare the hour or so extra time it takes to restore my system. Peace of mind is important.

---

### Post by szandor on 2008-04-22
> **stepheny said:**
> As I have said I used Mondo/Mindi successfully for over nine years and feel especially let down because under Gutsy my DVD's compared ok but when I needed them they were useless. After this experience I have absolutely no intention of ever using Mondo again. 

Waiting until Mondo  works in Gutsy (it's been about a year now hasn't it?) and then delaying your upgrade to 8.04 until Mondo works with that seems to be the wrong strategy to me. Who's to say it will ever work in Gutsy?

I am also wary of again using any  software which relies on libs that are used by other applications.

I am happy with my simple method which has saved my bacon several times and which I can trust completely. In the case of a disaster (which doesn't happen very often with Ubuntu :-) ) I can surely spare the hour or so extra time it takes to restore my system. Peace of mind is important.

the thing is, with your method, it looks like you're dependent on 2 systems. the one you are backing up and one to restore from. also i have nothing in /home (with the exception of .wine) and mostly need to back up config files/applications installed. samba, kernel, nvidia, nfs, ushare, compiz, wine, etc. i would prefer to just clone the drive to a bootable dvd all within a live, mounted file system. from your example though i can see where i can probably just get away with  backing up the current package list of installed applications and relevant conf files and do the rest manually. i like the bootable dvd option though. with mondo, i could create a 1.5gb bootable dvd prior to doing a full kernel/video/package update on my laptop (or if i don't like the upgrade to hardy). if something went wrong, i could just pop in a dvd and reboot. this whole process would take about 15 minutes from backing up, burning to dvd, and restoring. pretty quick and dvd's cost me about 10 cents each. also, i could actually do a clean install, update my packages, edit my config files in less than an hour which would be shorter and less cumbersome than using rsync. i for one am hoping mondo works in hardy. in reality, i've only had the mondo/gutsy issue for a about a week so i think i can wait a few more days for the hardy heron release. i don't see myself forsaking mondo on my fc8 laptop just because it doesn't work in gutsy. i'll either see if it works again or i'll find another method. now if this was a production server, i would use a completely different disaster recovery plan and wouldn't use mondo. however, on my toy, i guess my piece of mind comes cheaply. about 10 cents i would say.

---

### Post by stepheny on 2008-04-23
I can only give advice according to my own experience. 

Some parts of your reply are hard for me to understand, for instance you say that you have nothing in /home. All of your configuration files are there as hidden files! 

With the method I have described you reinstall all of your applications and the configuration information for them.

Regarding the 2 systems comment you made. Again it is hard to understand what you mean. The backups are written to a DVD and the basic system is installed from a Ubuntu live CD. Therefore you can restore from "bare metal", or at least from a machine with only BIOS.

You may have only had the Gutsy/Mondo problem for a week or so but the problem has been there and known about since Gutsy was released. If it cannot be resolved for Gusy what makes you think that it will be resolved in 8.04? 

And what do you need Wine for? ;-)

---

### Post by stepheny on 2008-04-23
Regarding the 2 systems comment you made. Again it is hard to understand what you mean. The backups are written to a DVD and the basic system is installed from a Ubuntu live CD. Therefore you can restore from "bare metal", or at least from a machine with only BIOS.

---

### Post by szandor on 2008-04-23
> **stepheny said:**
> I can only give advice according to my own experience. 

Some parts of your reply are hard for me to understand, for instance you say that you have nothing in /home. All of your configuration files are there as hidden files! 

yes but nothing that can't easily be recreated. .compiz, .gtk, .themes, etc aren't that important to me whereas .wine holds my games and video/sound tweaks.

> **stepheny said:**
> Regarding the 2 systems comment you made. Again it is hard to understand what you mean.

i just assumed on your comment: 'Keep a copy of this somewhere so that you can find it when your system dies, ie on an external drive.'

> **stepheny said:**
> If it cannot be resolved for Gusy what makes you think that it will be resolved in 8.04? 

there was a bug report indicating an updated package is being/has been pushed/built out for hardy, not gutsy. i won't know if it works until i upgrade to hardy though.

> **stepheny said:**
> And what do you need Wine for? ;-)

well, unless you know a better way to play world of warcraft or call of duty 4 in linux let me know. :D

---

### Post by stepheny on 2008-04-24
This is getting silly!

OK so my method is not suitable for you, I can live with that.

You have informed me that it is not useful for you so maybe now you can stop posting about it.

Good luck with Mondo.

---

### Post by szandor on 2008-04-25
> **stepheny said:**
> This is getting silly!

OK so my method is not suitable for you, I can live with that.

You have informed me that it is not useful for you so maybe now you can stop posting about it.

Good luck with Mondo.

lol. well, you did ask questions...

---

### Post by szandor on 2008-05-25
it appears the there was a problem with the ubuntu package and not the mondo package. if you apt mondo in ubuntu, you'll get a broken 2.24 package that actually looks like it should be 2.2.4. the current working mondo version is 2.2.5.

---

### Post by stepheny on 2008-06-12
[http://ubuntuforums.org/showthread.php?t=615751]("http://ubuntuforums.org/showthread.php?t=615751")

---

### Post by szandor on 2008-06-29
> **stepheny said:**
> [http://ubuntuforums.org/showthread.php?t=615751]("http://ubuntuforums.org/showthread.php?t=615751")

lol. actually found what the issue with mondo/gutsy was and fixed it a long time ago. i'm working on imaging raid via scripts/mondo but if it makes you feel better, i do on occassion use --get-selections for shits and giggles.

---

### Post by calibre97 on 2008-07-04
I'm trying your simple solution because, well, it's simple and should do the trick. I just ran rsync as you described and I get a bunch of errors. Actually I think it's the same error on every file:

rsync: chgrp "media/disk/home/me/fileadinfinitum" failed: Operation not permitted (1)


Any idea why this is happening?  I followed the instructions and used "sudo rsync -r -t -p -o -g -v --progress -l /home/ /media/disk/home" and that disk is mounted and writeable.

---

### Post by tagra123 on 2008-07-04
[http://ubuntuforums.org/showthread.php?t=240326](http://ubuntuforums.org/showthread.php?t=240326)

These are the scripts I use for backups. They are reliable and have been using them for a while now. 

You can modify the scripts to use whatever partition you wish to backup to. I backup hourly to a partition on my local drive and daily and weekly to my server.

Restore from these backups is simply a matter of opening up a tar file and copying the files back where the deleted or destroyed files are. I only backup my programming and text spreadsheets, etc... hourly. 

It's great knowing worst case you have only lost an hours worth of work. 

I also ocassionally do a partimage backup to make restoring a very simple process in the event of a complete harddrive failure.

I also use the dpkg to create an install list (described above by stepheny) especially when upgrading to a new version worked very well going from Dapper to Hardy.

My scripts run silently in the background -- you never know that they are there until you need a backup and presto =happy day.

---

### Post by calibre97 on 2008-07-04
BTW, I found out with further searching that my problem was the -o and -g combo backing up to a FAT32 SD card. I removed those options but still had some errors. I'm going to stop messing around with the SD card until I'm sure I can dedicate it to be ext3. Then the plans enumerated in this thread should work fine.

---

