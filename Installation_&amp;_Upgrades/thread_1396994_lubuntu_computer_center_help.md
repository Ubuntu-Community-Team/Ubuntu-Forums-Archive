---
title: "lubuntu: computer center help"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by oddchild on 2010-02-02
Hi All,


I am trying to get lubuntu to download. I think it will take another week or so to finish downloading... 

I manage a series of computers at a kids center in Beirut. The computers are constantly broken. I have Ubuntu installed on them, but I am wanting to find a way to do a custom distro since I am constantly having to install and resinstall then redownload all the needed packages.

How can I make a custom iso that also has...

lubuntu 
childsplay
tuxtype
tuxmath
restricted extras

It takes  a LONG time to do the package installs...

Thanks all...

---

### Post by amsterdamharu on 2010-02-02
Here are 2 ways to do this:

1. Use tar to backup a working system
To backup use (assuming / is on sda5 mounted on /sda5):
Boot from tynicore or TRK distro, mount the / drive
tar -cvpzf /sda5/backup/backup.tar.gz -–exclude=/sda5/backup --exclude=/sda5/lost+found --exclude=/sda5/sys --exclude=/sda5/mnt --exclude=/sda5/media --exclude=/sda5/home /sda5 
To restore use:
Go to the home directories and delete any . file 
rm -R .??*
This will delete anny settings and saved stuff of applications
tar -xvpzf /sda5/backup/backup.tar.gz -C /sda5/

2. Download the packages you need and create a local repository:
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

I wonder why the installs get broken all the time, do the user have root password? Can't you not just delete all the .??* files and directories from their home folder to reset settings of your apps?

---

