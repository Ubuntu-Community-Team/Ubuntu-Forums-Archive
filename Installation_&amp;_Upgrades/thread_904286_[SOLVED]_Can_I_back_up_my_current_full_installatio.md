---
title: "[SOLVED] Can I back up my current full installation"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by draclear on 2008-08-29
including all of the updates and all of the extra bits and pieces I've loaded via Synaptic to a DVD or CD, so that if I have to reinstall from scratch I can do it from this new disk rather than having to use the original and go through the whole install/update/download process again?

I'm using 64 bit Hardy Heron, fully up to date, with KDE4 installed as well, though I mainly stick with gnome

Thanks.

PS,  please keep it simple as I'm not THAT techy and would be very please if there was a piece of GUI software that would do this for me.

---

### Post by Herman on 2008-08-29
One of the easiest and best ways to make a complete backup of and entire installation including all added software and settings is to use Partimage. Aysiu has the best instructions about how to use Partimage in Ubuntu, [Use PartImage]("http://www.psychocats.net/ubuntu/partimage")
You will need another partition or a USB external hard drive for Partimiage to copy the backup files to.

I always have my files backed up separately, so that the compresses operating system backup doesn't take up very much hard disk space. Partimage makes a series of 2 GB compressed files by default, so you can fit two of those per DVD if you want to store them that way.

The ordinary way to make a backup is to just make a regular backup of all your files, and include your hidden files and folders in your /home/username directory. The .evolution directory will contain all your email, calendar and contacts and so on. Bookmarks will be in your .mozilla directory somewhere. 
Added software packages will be found in /var/cache/apt/archives/ and you can incude those in your backup if you want. When you re-install, just restore those packages to /var/cache/apt/archives. You'll still need to re-install your software, but it'll be a lot faster because it won't need to be downloaded from the internet. :)

It would probably be wise to keep both kinds of backups, a partimage backup plus an ordinary backup as well, just in case anything goes wrong.

---

### Post by robert shearer on 2008-08-29
> **draclear said:**
> including all of the updates and all of the extra bits and pieces I've loaded via Synaptic to a DVD or CD, so that if I have to reinstall from scratch I can do it from this new disk rather than having to use the original and go through the whole install/update/download process again?

I'm using 64 bit Hardy Heron, fully up to date, with KDE4 installed as well, though I mainly stick with gnome

Thanks.

PS,  please keep it simple as I'm not THAT techy and would be very please if there was a piece of GUI software that would do this for me.


Yes, there is a GUI app that makes a live cd/dvd that you can use as a re-install disc like the original Ubuntu install disc. 
You can use it to reinstall to your usual computer, another computer or take it with you to use as a live cd/dvd on someone/somewhere elses computer.
(This certainly works for std 32bit though I haven't tried it on a 64bit,you might need to check the Remastersys link to their help forum.) 
Here is the link..

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by Herman on 2008-08-29
There is also a program we can install from our 'Applications'-->'Add/Remove Applications', or synaptic or apt-get called sbackup. 
Sbackup's sourceforge page: [sbackup]("http://sourceforge.net/projects/sbackup/"). I have tried sbackup and found that it works very well. 
EDIT: Here's a link: [*Backup* and Restore Your Ubuntu System using Sbackup -- Ubuntu Geek]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=8&url=http%3A%2F%2Fwww.ubuntugeek.com%2Fbackup-and-restore-your-ubuntu-system-using-sbackup.html&ei=8tK3SJ78M5qUsQPc-Pn-Ag&usg=AFQjCNHP1FRF0haTvTSqp28niV9Zc8goOg&sig2=OCG_wPVTI9QaeCpa5sQ4_w")

 
If you just type 'backup' into the search bar in 'Add/Remove', you'll find a few more handy applications there too that you might feel like trying out, such as maybe 'Home User Backup', and 'Backup Preferences' as well.

EDIT: Hey, cool, thanks robert shearer, I didn't know about remastersys, that looks like something not to be missed! :) Thank you!

---

### Post by robert shearer on 2008-08-29
> **Herman said:**
> There is also a program we can install from our 'Applications'-->'Add/Remove Applications', or synaptic or apt-get called sbackup. 
Sbackup's sourceforge page: [sbackup]("http://sourceforge.net/projects/sbackup/"). I have tried sbackup and found that it works very well. 

If you just type 'backup' into the search bar in 'Add/Remove', you'll find a few more handy applications there too that you might feel like trying out, such as maybe 'Home User Backup', and 'Backup Preferences' as well.

EDIT: Hey, cool, thanks robert shearer, I didn't know about remastersys, that looks like something not to be missed! :) Thank you!

You're welcome,
Here are a couple of other links.

[http://loscompanion.com/forums/index.php?board=58.0](http://loscompanion.com/forums/index.php?board=58.0)

[http://loscompanion.com/forums/index.php?PHPSESSID=d578395b27bc9a7d0d1ac689a9167da3&topic=4249.0](http://loscompanion.com/forums/index.php?PHPSESSID=d578395b27bc9a7d0d1ac689a9167da3&topic=4249.0)

I am not at my usual computer but I seem to remember that the repository quoted in the Remastersys site is..
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/

but needs to be this.

deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/remastersys
Just changed computers and looked at my apt sources list and my mind must be going because this is the entry I have..
[http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys

I recall that the Ubuntu-geek site had a how-to on Remastersys. I will go look and repost.

Yep, here..
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

### Post by draclear on 2008-08-29
Thanks, guys, looks like that's my question sorted.  I shall try out each of your suggestions when I get home.:)

---

### Post by Gallardo Spyder on 2008-08-29
Those will all work...  However this is by far the quickest, easiest way to do a full system backup - meaning exact.

I do this several times per month - whenever I do changes that could dork the system...

Take a look at this thread - and down about 5 to my post...  It takes about 10 minutes and works without issue...

[http://ubuntuforums.org/showthread.php?t=408337](http://ubuntuforums.org/showthread.php?t=408337)

Thanks,
GSpyder

---

