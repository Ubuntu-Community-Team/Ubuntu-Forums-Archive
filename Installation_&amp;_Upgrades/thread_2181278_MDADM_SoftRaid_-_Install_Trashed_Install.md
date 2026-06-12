---
title: "MDADM SoftRaid - Install Trashed Install"
date: 2013-10-17
forum: Installation &amp; Upgrades
---

### Post by stevenjrees on 2013-10-17
Nice upgrade system for non-linux gurus. 

[LIST]
[*] "The Alternate CD version previously available allowed the use  of the same fast text-based installer used in the Server version  (requiring less RAM), and there were more installation options than on  the Desktop CD ("Regular Download"). Sadly, this version has been  discontinued. "
[/LIST]

I have a Raid 1 array where i moved the home directory to. 

When i did an online upgrade from 13.04 it died half way through related to the raid drive and config file. 
Now when i try to use the live CD, i have only the choice to install in parallel to 13.04 or to erase 13.10 and if i try manual it doesn't recognize the raid partition. 

As a non-linux person, i am honestly on the verge of going back to windows, for all its flaws. at least you don't have to be a propeller head to work with it.

---

### Post by stevenjrees on 2013-10-17
i can't boot into recovery mode from the kernel 3.8.0.31 but i can from 3.8.0.30. However, i can't install mdadm in recovery mode as i get the error dpkg_error: corrupt info database format file '/var/lib/dpkg/info/format'

---

### Post by TheFu on 2013-10-17
I'm happy that you tried Ubuntu and were able to get a very geeky setup - RAID - working on non-LTS supported version.
Most users should stay on 12.04 - an LTS release - with 5 yrs of support.  Newer isn't always better ... just like Win8 and Vista and Win98 and WinME sucked at the time.  When Canonical has $1B to spend on development for every release, I'm certain that things will be better. ;)

If you choose to leave, you will be missed and just trading 1 set of issues for others. Only you can make that choice and decide which set of problems is best for your needs.

Even if Ubuntu isn't the best answer for you, there are other distros that tend to handle RAID setups better. Of course, those distros have downsides too.

I've migrated mdadm softRAID arrays between 3 different systems, but I've **never** tried to install with the array connected and I only run LTS releases.  You could disconnect the RAID for the installation, let a tiny /home be setup, then connect the RAID, and mount it onto the /home directory manually.  I'd probably do that as a relatively easy work-around.
Sorry, I cannot help more - working on installers is a little outside my skills.

Regardless of your choice, I wish you well and happy computing.

---

### Post by stevenjrees on 2013-10-17
Hi TheFu, don't think you read my post fully. I upgraded from 13.04 to 13.10. 

I did have LTS before i had Raid and the system decided to do a distribution upgrade to 13.04 beta for some unknown reason. I was then unable to go backwards. I have moved my /home to the RAID as i need my data to be secure. It is just bizarre that a so called effortless install doesn't recognize and maintain a raid device. as if no one uses secure data. 

At the moment, i am struggling to get into my system due to the lack of mdadm installed and would appreciate any help.

---

### Post by TheFu on 2013-10-17
To me, the actual release that you tried, moved to or didn't move to doesn't really matter if it isn't LTS.  I've been running LTS releases on many, many machines for years, never seen any of them spontaneously migrate to another release, but I never use the GUI to manage packages. Too easy to be "click happy", I guess.

Try these steps:
[LIST=1]
[*]Boot off a liveCD.
[*]Remove the raid from the /etc/fstab of the main OS install .. might need to mount that partition somewhere.
[*]Create a /home/{userid} directory with correct ownership and permissions on the main OS install partition.
[*]boot off the normal OS and do whatever update you like.
[/LIST]

There are probably "trivial steps" missing. Sorry, can't do any better now and you'll have to learn dome geek/nerd skills to solve this.

After you are at the point you like, reconnect the RAID partition where you had it before - probably /home, but it could be anywhere.

I've never heard "secure data" and RAID used as above.  RAID1 is just for data availability. The only way I know to secure data is through backups and RAID most definitely is NOT a backup. Corrupt data and viruses get written to all RAID disks faster if that is being used.  RAID won't help recover from those and many other scenarios, but good, versioned backups will.

I hope the steps are enough to get you moving forward.

---

### Post by stevenjrees on 2013-10-17
TheFu, the RAID for me is to enable me to minimize downtime and prevent complete data loss due to HDD failure, as happened to me some years ago. To this extent, i can have some data loss/corruption. Otherwise, i would agree with you. 

Nevertheless, i find the Ubuntu upgrade process to be completely unsatisfactory. if it can't even recognize what drivers a person is using and ensure they stay valid during any upgrade process, what use is it. especially to the lay man (which i fall into this category)

The end result for me was, the only way i could get forward was to do a re-install without my /home and add the mdadm settings and change the /home mount point after. 
This means, i have lost all my user accounts (although data remains in tact) and all application info, repositories, systems settings, etc. 
It is going to take me days to rebuild my system with corrections for AMD CPU, PulseAudio, customizations, etc, etc. all backups were gone.

---

### Post by TheFu on 2013-10-18
Nothing replaces good backups BEFORE attempting an upgrade.  

With a good backup, all the system settings from /etc and personal settings from /home would be stored.  That should cover any customizations too, provided those where not placed in odd directories.
With a good backup, a list of all the programs so that reinstallation of those in 1-3 commands is possible.

I get that you are frustrated. At this point, learning where the mistake occurred is paramount. Blaming a computer won't help in my experience.  Changing code and making a pull-request will OR modifying behavior to work around the issue.
**Backup Best Practices:**
[LIST=1]
[*]    Stable / Works Every Time
[*]    Automatic
[*]    Different Storage Media
[*]    Fast
[*]    Efficient
[*]    Secure
[*]    Versioned
[*]    Offsite / Remote
[*]    Restore Tested
[/LIST]

I will attempt to migrate a 10.04 box to 12.04 in the next few weeks. It will be a fresh install, not an update over the old one - the old install started with 6.06 --> 8.04 --> 10.04 so it is quite crufty now. Time for a fresh install.  2 x 2TB HDDs are being added for backups before I begin. During the install, those extra HDDs will be disconnected and probably located in a different room. I'm paranoid that way. ;)

---

### Post by stevenjrees on 2013-10-25
a week has passed and i am still struggling to recover from this crap upgrade process. by that i mean, it only works if you have vanilla install and no customisations.

- i couldn't install mdadm in recovery mode
- the alternate cd i found was actually Lubuntu and didn't bring me anything but more work to try back to default ubuntu look
- i was left to re-install ubuntu over the current version, but fortunately my app settings were not lost because the /home could not be mounted. 
- after re-installing and loading mdadm and redirect to the correct /home location, i installed all the packages i have on the laptop

I now have two weird problems, 
- the file associations don't get recognised. The defaults.list and mimeapps.list both have all correct file associations and i have run the command to update the database but still all file types open the archive manager
- the gnome/unity menu doesn't sort although all .desktop files exist. i.e. Planner (project management) purge/install removes/installs in the office menu. LibreOffice, Evolution do not appear and purge/install doesn't help

i have compared the directories on my working laptop (with 13.10) for .local, /usr/share, etc and they all seem fine. Packages installed are the same on both machines. 

any ideas?

---

