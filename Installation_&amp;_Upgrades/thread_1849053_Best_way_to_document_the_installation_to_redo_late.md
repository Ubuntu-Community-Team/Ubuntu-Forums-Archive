---
title: "Best way to document the installation to redo later?"
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by jimmyland on 2011-09-23
Hi All,

Is there a way to document a server's configuration so it can be reproduced exactly later? I have a couple of boxes running mail server, DB, and network shares. I use backuppc to do daily backups. My plan for disaster recovery is to just reinstall the downed system and restore the data back.

I'm trying to find a way to document everything I need to know about a system so that I can install everything back to get it back to a state ready for the restore files, this includes all the installed packages, disk partition information, network settings, etc. I'm hoping I can somehow dump all of it on a periodic bases as the configs changes... especially the packages installed.

---

### Post by zvacet on 2011-09-24
I´m not an expert,but I hope you have your backups on separate disc (or other device),so you want to reinstall your system as it was ( if something goes wrong).You can use [remastersys.]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html")Other way is save as text file all installled packages.You can do that with 


```
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages 
```

You will find my-packages file in your home directory.E-mail it to yourself and after reinstall put that file in home directory again and run

```
sudo xargs aptitude --schedule-only install < my-packages
sudo aptitude install[
```


Network settings should be in /etc/network/interfaces so you can copy them just in case.

---

### Post by oldfred on 2011-09-24
I only have a desktop, but include a run of boot script to show partitions and drives configuration and I use dpkg but the aptitude posted above should work also.

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
backup the following:

1. /home (Users' personal files and settings)
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup
5. list of installed applications 

I include these also:
cp /etc/apt/sources.list ~/sources.list.backup
apt-key exportall > ~/repositories.key
Various hardware listings/configurations
dpkg --get-selections > ubuntu-files
bash ~/Documents/LinuxDocs/CurrentSys/boot_info_script.sh
lshw -html > ~/hardware_info.html
udevadm info --export-db > file.txt
dmidecode > bios.txt

Other applications if data not separate
apache, any sqldb, tomcat 
Document system backup or for multiple install:
[http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm](http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm)

More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
#[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)

dpkg --get-selections | grep -v deinstall > ubuntu-files
or
dpkg --get-selections > ubuntu-files

---

