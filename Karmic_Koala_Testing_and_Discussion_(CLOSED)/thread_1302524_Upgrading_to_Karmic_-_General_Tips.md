---
title: "Upgrading to Karmic - General Tips?"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Roger Allott on 2009-10-27
As I understand it, Karmic (9.10) will be released on Thursday.

When I upgraded from Intrepid to Jaunty, everything happened quite smoothly, although the installation took over two hours, I seem to recall. There were three occasions that the install stalled, asking me whether I should change some file to the new default one or keep my old one. I chose to go with the new ones, but I didn't keep a record of the files in question.

However, upon restart, all my compiz and Emerald settings had vanished, and some of my repositories (software sources) had been disabled.

It was a simple task to re-enable the repositories, but it was a few months later that my old compiz/emerald settings magically reappeared.

What I would have liked at the time of upgrade to Jaunty was an idiot's guide to upgrading. Is there such a thing on the site at present? If not, would anybody like to write one in time for Thursday?

---

### Post by ukripper on 2009-10-27
> **Roger Allott said:**
> As I understand it, Karmic (9.10) will be released on Thursday.

When I upgraded from Intrepid to Jaunty, everything happened quite smoothly, although the installation took over two hours, I seem to recall. There were three occasions that the install stalled, asking me whether I should change some file to the new default one or keep my old one. I chose to go with the new ones, but I didn't keep a record of the files in question.

However, upon restart, all my compiz and Emerald settings had vanished, and some of my repositories (software sources) had been disabled.

It was a simple task to re-enable the repositories, but it was a few months later that my old compiz/emerald settings magically reappeared.

What I would have liked at the time of upgrade to Jaunty was an idiot's guide to upgrading. Is there such a thing on the site at present? If not, would anybody like to write one in time for Thursday?

Backup your home --> Clean install Karmic--> put back your data on karmic install : All of this will take no longer than 40 mins depending on amount of data in your home drive.

---

### Post by WolfRage on 2009-10-27
Although I agree there should be a better way. I do have to agree with ukripper and say that a clean install with a saved home directory is the best way to go.

---

### Post by twright on 2009-10-27
There is nothing wrong with upgrading - the only reason it takes longer is that it include downloading the updates at the same time.

Just tell everything to use the new version. You will get the new default settings for some things rather than your old customized ones but that is part of the point of upgrading in any case. I have already upgraded one machine to Karmic and it ran smoothly.

On the other hand there is something to be said for doing a fresh install and getting the most out of the update, especially in Karmic with new technologies such as ext4 and grub 2 which you will not get via an upgrade.

---

### Post by Murray Walker on 2009-10-27
Currently I use 8.10 and would quite like to try out 9.10 but I'm worried that it won't work on my hardware.  My laptop might be slightly damaged and Windows crashes more than it used to.  I use Ubuntu 8.10 because all other distros (Suse, Fedora and earlier versions of Ubuntu) that I've tried haven't worked properly, or at least I couldn't get them to work.

I know I can try Karmic out off a CD/USB stick but sometimes I find problems when I install onto my harddrive that didn't show up when running off a CD.  If I use the automatic upgrade process, will it keep all my data and previous versions of Ubuntu?  When I boot my system up at the moment, I get several choices of which version of Ubuntu to use, and which linux kernel etc.   Does Karmic just add an option at the top of this list and leave my current version there somewhere for me to revert to?  Or do I lose all previous installations of Ubuntu?

Also, I gather from the above that if I use the automatic upgrade process, I won't get the full upgrade.  This seems a bit disappointing.  Why would I not get all the new stuff?

Thanks in advance for replying to my very basic questions!

---

### Post by twright on 2009-10-27
> **Murray Walker said:**
> 
Also, I gather from the above that if I use the automatic upgrade process, I won't get the full upgrade.  This seems a bit disappointing.  Why would I not get all the new stuff?

Thanks in advance for replying to my very basic questions!
Some older components will not be switched out for newer ones as for most people not loosing data or having their system rendered unbootable is more important than having improvements to the core system. Both of these things are tricky to upgrade in place as the filesystem storing all of your data would have to be rearranged and your boot manager would have to be overwritten; these are things done in a fresh install of Ubuntu anyway but rather too risky for an upgrade process which has to be smooth and bulletproof.

---

### Post by Claus7 on 2009-10-27
Hello and welcome!

> **Murray Walker said:**
> Currently I use 8.10 and would quite like to try out 9.10 

Since you are trying an upgrade from 8.10 then you should first upgrade to 9.04 and then to 9.10.

Nobody will reassure you that this process will proceed without failures. What you have to do is to have a backup of your files before doing so. Normally it should keep your configurations, yet sometimes during upgrade it asks you whether you want to keep up your current files or upgrade them.

Finally, about the hardware you are mentioning, its difficult I think for someone to tell you something since you do not give any specifications.

Regards!

---

### Post by WolfRage on 2009-10-27
[COLOR=black][FONT=Verdana]One more point about the hardware. I actually regressed my older system after trying out Karmic. I then went to Jaunty and found that it was not compatible with my hardware. So I wound up going back to Ubuntu 8.04 in the end. 8.04 and 8.10 are currently the best at supporting proprietary drivers for older hardware. The newer Ubuntu versions are steps in the right direction of moving away from proprietary drivers but they do not fully support all older hardware right now. In my case the old hardware holding me back was my ATI Radeon 9600 xt All-In-Wonder (Yes it is a POS but it is what I have for that motherboard).[/FONT][/COLOR]

---

### Post by Claus7 on 2009-10-27
Hello,

> **Roger Allott said:**
> As I understand it, Karmic (9.10) will be released on Thursday.

When I upgraded from Intrepid to Jaunty, everything happened quite smoothly, although the installation took over two hours, I seem to recall. There were three occasions that the install stalled, asking me whether I should change some file to the new default one or keep my old one. I chose to go with the new ones, but I didn't keep a record of the files in question.

However, upon restart, all my compiz and Emerald settings had vanished, and some of my repositories (software sources) had been disabled.

It was a simple task to re-enable the repositories, but it was a few months later that my old compiz/emerald settings magically reappeared.

What I would have liked at the time of upgrade to Jaunty was an idiot's guide to upgrading. Is there such a thing on the site at present? If not, would anybody like to write one in time for Thursday?

I do remember myself upgrading and having to choose between my old files and the new ones. I was not sure exactly what might be the difference, yet if I can recall correctly those were no more that 3 or 4 of them, with the majority of them having nothing to do with some configurations that I have done. I suppose that those files were simply updated... Also someone should note them down during the update process (unfortunately a print screen key is not functioning during upgrade).

Anyway, I do not think that such a guide is necessary, since things are straightforward. Some remarks I can make, are the following:

[LIST]
[*]In case something crashes someone should know how to continue the update via command line.
[*]The update process should be from version to version, except if is done from LTS to LTS.
[*]As it is pointed out the update process might take longer that a clean installation, since the packages should be downloaded first.
[*]Every time this is done, someone should take a backup of his or her own files.
[*]It is better to keep / partition (root partition) separately, so if things are messed up, someone should not have damaged his or her own home directory.
[*]And finally, it is required to have enough free disk space for the upgrade to proceed (I would advice more than 10GB).
[/LIST]

This is what I can tell, judging from my humble experience.

Regards!

---

### Post by raprap30 on 2009-10-27
As a conclusion, a clean install is always better. :)

---

### Post by philinux on 2009-10-27
On this occasion a clean install will definitely be better.

Grub2 and ext4 to name two major changes.

Home on its own partition is good. But when I reinstall karmic I'm backing this up and doing a full format of the hard drive. I'll still have a home partition though.

---

### Post by Murray Walker on 2009-10-27
Many thanks for the replies, explanations and welcomes.  I'll do a clean install as you all suggest.  Cheers!

---

### Post by cwmoser on 2009-10-27
Hint -- here is a tip for your fresh install of Ubuntu.
The following are my notes on how to get a listing of all the packages installed on current OS, and how to automtically reinstall them on the new OS.



Get list of packages installed on OLD PC

- On old PC, get a list of all the packages I had installed:
$ dpkg --get-selections | grep -v deinstall > installed-software


- Manually scan through the list of packages and remove any I think I don't need.


- On new PC, reinstall all the packages I installed on the old PC:
$ sudo dpkg --set-selections < installed-software


- Remove orphaned packages:
$ sudo apt-get autoremove
$ sudo apt-get update


Carl

---

### Post by Roger Allott on 2009-10-27
OK, so best to do a clean install then, and not bother with upgrading.

A few questions come to mind.

Backing up my home directory. To a CD-R (or DVD-R) only, or could I back up to an NTFS hard drive, such as I have for Windows?

I have various things in what I think is my root directory that I can't afford to lose. For example, the files and stuff in my /var/www directory that is my webserver location. I can add them to my back up pretty easily, but I'm concerned as to what else might be lurking in root. Is there likely to be anything else there worth preserving and porting to the new karmic installation?

I have various MySQL databases on my machine that would be a real bummer to lose. Is that data stored in my home directory or my root directory? As far as I know, I haven't changed the default situation.

---

### Post by VMC on 2009-10-27
> **Roger Allott said:**
> Backing up my home directory. To a CD-R (or DVD-R) only, or could I back up to an NTFS hard drive, such as I have for Windows?

I have various things in what I think is my root directory that I can't afford to lose. For example, the files and stuff in my /var/www directory that is my webserver location. I can add them to my back up pretty easily, but I'm concerned as to what else might be lurking in root. Is there likely to be anything else there worth preserving and porting to the new karmic installation?

I have various MySQL databases on my machine that would be a real bummer to lose. Is that data stored in my home directory or my root directory? As far as I know, I haven't changed the default situation.

I don't know about MySQL, myabe look in you home dir to see if any config files and database saves are there. Is there any option or preferances in MySQL that would direct a dir?

Regarding backups, sure can use NTFS. I do it all the time. You can also use several backup programs in case you forgot something - Clonzilla, FSArchiver, dd with gzip, etc.

---

### Post by twright on 2009-10-27
> **Roger Allott said:**
> OK, so best to do a clean install then, and not bother with upgrading.

A few questions come to mind.

Backing up my home directory. To a CD-R (or DVD-R) only, or could I back up to an NTFS hard drive, such as I have for Windows?

I have various things in what I think is my root directory that I can't afford to lose. For example, the files and stuff in my /var/www directory that is my webserver location. I can add them to my back up pretty easily, but I'm concerned as to what else might be lurking in root. Is there likely to be anything else there worth preserving and porting to the new karmic installation?

I have various MySQL databases on my machine that would be a real bummer to lose. Is that data stored in my home directory or my root directory? As far as I know, I haven't changed the default situation.
With Mysql I would manually dump the databases and do a test restore. Unless you are doing much server stuff everything should be stored in home. If you do have much in the way of complex system setup then you could always do an upgrade; as a general rule though, the more new stuff you have after upgrading (i.e. application config files, installed software), the better it should be :-)

---

### Post by Roger Allott on 2009-10-28
Why was this thread moved to the back end of beyond?

I put it in Absolute Beginner Talk originally because I'm quite sure there are many noobs who need to know stuff about Karmic before tomorrow. At the very least, it would seem sensible to advise noobs about the benefits of a complete reinstall from scratch.

Something else that's come out of this thread is that ubuntu 9.04 onwards seems to be moving away from the position of being the OS to put onto old machines. I wish I'd known that a few weeks ago, when I tried upgrading my xubuntu 8.10 to 9.04 - a process that failed so badly that I needed to remove xubuntu altogether and can no longer get any form of ubuntu 9.04 installed on it.

I'm sure this is not a flaw in 9.04 and the development plans of ubuntu generally, but the reluctance to tell people stuff that might be perceived negatively is itself a rather big negative. 

Why not just have a general comment somewhere prominent saying that old machines might be best not upgraded beyond 8.10? Someone might even be able to write a jolly useful little script that analyses a PC's hardware to report whether it's a good idea to go for 9.04 onwards, or to stick with 8.10.

---

### Post by ukripper on 2009-10-28
> **Roger Allott said:**
> 


I have various MySQL databases on my machine that would be a real bummer to lose. Is that data stored in my home directory or my root directory? As far as I know, I haven't changed the default situation.

I use mysqldump for regular full backups. This is a good script for backup to begin with, check this link - [http://openconcept.ca/mysql_permissions_for_backup](http://openconcept.ca/mysql_permissions_for_backup) and you can cron the script to run as a scheduled job.

You should always have a regular backup for database in place. Not having backup is never a good computing practice.

---

### Post by ukripper on 2009-10-28
Follow instructions on this thread for full system backup which is very simple to do. [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by Roger Allott on 2009-10-28
> **ukripper said:**
> I use mysqldump for regular full backups. This is a good script for backup to begin with, check this link - [http://openconcept.ca/mysql_permissions_for_backup](http://openconcept.ca/mysql_permissions_for_backup) and you can cron the script to run as a scheduled job.

You should always have a regular backup for database in place. Not having backup is never a good computing practice.

Cheers. Personally, I prefer to use MySQL Administrator for these sort of things, and it has a relatively nice doo-dah for backing up databases.

I've just backed up my relevant schemas to a dedicated directory in /home, so my data etc. will be included in the stuff I backup when I save my whole home directory/folder shortly before installing Karmic.

---

