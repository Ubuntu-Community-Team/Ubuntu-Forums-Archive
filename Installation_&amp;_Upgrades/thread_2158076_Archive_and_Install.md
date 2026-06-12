---
title: "Archive and Install???"
date: 2013-06-27
forum: Installation &amp; Upgrades
---

### Post by artphotodude on 2013-06-27
Hello: am trying to figure out what is wrong with my Mom's install 
[http://ubuntuforums.org/showthread.php?t=2157865](http://ubuntuforums.org/showthread.php?t=2157865)

But at this point it isn't looking good.  Anyway, in the worst case scenerio, is there a way to rebuild a corrupt system without wiping out all the installed programs and user data (like the Mac 'Archive and Install', or PC System Restore function)??  I have almost a full week into getting this set up for her and it is (was) just right before the problems started.

Thanks for your thougts!!

---

### Post by janepage on 2013-06-27
Try to see here [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) 
[http://community.spiceworks.com/how_to/show/381-how-to-backup-and-restore-an-ubuntu-server-with-tar](http://community.spiceworks.com/how_to/show/381-how-to-backup-and-restore-an-ubuntu-server-with-tar)

--
Jane
Hard Drive Specialist - [www.harddrivesforsale.com/]("http://www.harddrivesforsale.com/")

---

### Post by artphotodude on 2013-06-27
> **janepage said:**
> Try to see here [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) 
[http://community.spiceworks.com/how_to/show/381-how-to-backup-and-restore-an-ubuntu-server-with-tar](http://community.spiceworks.com/how_to/show/381-how-to-backup-and-restore-an-ubuntu-server-with-tar)

--
Jane
Hard Drive Specialist - [www.harddrivesforsale.com/]("http://www.harddrivesforsale.com/")

Thanks so much for the reply.  This does really make me think twice about using Ubuntu for my own stuff (have only been setting it up for customers and friends/family), was planning to set up my own Ubuntu system in the Fall.  There is not much incentive to get really comfortable in a system and set up just they way you want if a major system curruption means you will loose the configuration.  One's data is only half of the issue.  If wrecked system files also mean wrecked programs, configurations and customizations, and there is no real, working (bootable) backup solution, then Ubuntu has to be relegated to "disposable system" status.  Too bad.  Hopefully this gets fixed.  Not to be a Mac-o-file, but there are definite advantages to keeping applications, library files and user files separate from the system.

---

### Post by grahammechanical on 2013-06-27
You could try a re-install using the Do Something Else option and selecting the same partition but not marking it to be formatted. That will overwrite system files but not user configuration files in /home. I have not tried this recently with an installation that I had modified from the default install but I did do it some years ago and the applications picked up the original configuration settings. You most probably will have to re-install any non-default applications.

If it is the user configuration files/scripts that are causing the problem then you can delete them and when the application is loaded they will be recreated. These files are hidden files. They all have a dot ( . ) in front of the file name that hides them from the File Manager. But there is a View Menu setting of Show Hidden files that gets around that.

The default file system in Ubuntu is Ext4. The BTRFS files system is available and that has a feature where we can take a snapshot of the system and then rollback to it if needed. There are a few issues stopping btrfs being used by ordinary people. The main issue is the lack of a GUI fronted managment utility for creating the snapshots and doing the rollbacks.

Grub also cannot detect Ubuntu installed on btrfs. That is not a problem if there is only one Ubuntu installed and no other Linux OS installed. But more than on Linux OS and it will not show up in the Grub boot menu.

The Ubuntu installer crashes when doing a reinstall on to btfrs if we do not tick to format. A reinstall without a format does not require the user's details. They are already there in /home. So, the installer does not ask for user details and it crashes when it tries to create a user profile. Apparently the installer (Ubiquity) like Grub cannot read btrfs partitions.

So, until these issues are fixed Ubunt will not have a rollback option. I speak from recent experience of runing tests on this kind of thing.

Regards.

---

