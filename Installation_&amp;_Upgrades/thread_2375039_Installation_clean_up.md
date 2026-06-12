---
title: "Installation clean up"
date: 2017-10-21
forum: Installation &amp; Upgrades
---

### Post by habana on 2017-10-21
Well, I stuffed up. Upgrading from 17.04 to 17.10 I got to the point where old packages were to be removed and was asked to close any open programs before proceeding. I had a terminal open so closed it. The installation window promptly vanished! So I restarted the computer and fortunately 17.10 boots OK. I have run the following:

```
sudo apt-get clean
```
```
sudo apt autoremove
```

Is there anything else I should do to clean up my system?

---

### Post by TheFu on 2017-10-22
Maybe.  Just depends on what is left over that you don't like. Completely a personal decision.

If it were me, I'd restore from the backup I made prior to starting the move from 17.04 --> 17.10 and start over.  It is likely you will have issues later because the move wasn't completed.  
Or
It could be that closing the terminal was just a coincidence with the migration installer finishing.  If you ran the installer from inside the terminal, then closing that window killed all child processes.  If you ran the installer in some other way, then closing the terminal was just a coincidence.

---

### Post by termibuntu on 2017-10-22
That should be it for cleaning up after a upgrade. If you feel that&#8217;s not enough, you could clean out some caches and other temporary files. But it seems to me like that&#8217;s enough. There should be nothing more to do to clean up.

---

### Post by habana on 2017-10-22
Thanks guys. It certainly wasn't a coincidence. I closed the terminal and the installer immediately vanished. I didn't install from inside a terminal. 

One day on and everything seems to be OK which one would expect as the installation part of the upgrade was completed. I was just concerned that I may have old files scattered everywhere.

I backed up my data of course but I didn't back up the 17.04 installation, if indeed that is possible. To start over, I assume I would have to install 17.10 from an iso which would mean a lot of work to get my system configured the way I like it.

---

### Post by TheFu on 2017-10-22
Moving from distro to distro will leave old files around.  That is part of the reason why many people prefer to NOT upgrade and choose to perform a fresh install instead.  It is just storage and since we aren't in the world of 2GB disks anymore, it usually isn't worth the effort to clean up much.  I doubt more than 1G of old files remains after the upgrade.  Even on my 64G SSD, I wouldn't bother worrying about it and certainly wouldn't manually search for those old files.

Beyond apt clean, apt autoclean ... I wouldn't worry.

Certainly you can backup the entire system. There are 20+ F/LOSS tools that do just that.  It is always a good idea to make a complete system backup PRIOR to doing anything as risky a distro upgrade. I would argue that having daily versioned backups are necessary for security reasons in the world today AND that retaining at least 60 days of those versioned backups is a requirement for a low-risk system.  120+ days of versioned backups for high risk system is a requirement for me.

For most home users, files will not be "scattered everywhere" - they are in the HOME directories for each userid. Period.  For most home users, backing up their HOME and the list of packages manually installed is sufficient to make an efficient, easily restored, backup.  **Aptik** is an application that handles this, but I've never used it.  I use rdiff-backup for my system backups, since most of my systems don't have any GUI installed and run services that do not store data in the HOME.  On a server, data isn't usually stored in a HOME directory - rather it is stored under /var/ somewhere or in /opt/.  I also always backup /etc/ - it is tiny and has so much highly useful information that might be good to have during a restore. Most of my systems have system-level customizations. Those are stored in /etc/ almost always.

I think you are probably fine, but if you are paranoid or see any issues, check out aptik, make a backup of the things that tool handles, then do a fresh 17.10 install, followed by restoring the aptik backed up files.  Then have a beer. ;)

---

### Post by habana on 2017-10-22
Thank you TheFu. It has been my habit to do a clean install of LTS and do upgrades in between. Aptik looks to be a really useful tool, I have now installed it. I'll mark this thread as solved and have a beer.

---

### Post by habana on 2017-10-23
Just a postscript to my last post. I discovered I had to run
```
xhost si:localuser:root
```
to run Aptik. I have to do the same thing when I run Synaptic. It's a Wayland thing, I suppose I will get used to it.

---

