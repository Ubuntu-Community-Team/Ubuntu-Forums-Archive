---
title: "Need help backing up my server"
date: 2017-12-07
forum: Installation &amp; Upgrades
---

### Post by flutz on 2017-12-07
Hi,

i want to upgrade my old ubuntu server, which is still running 10.04, to the next (and then, afterwards the next) LTS-Version. To make sure I don't ruin everything, I want to make a full backup of all files. My normal work-computer runs on windows10 and now I need a tool to make a backup of my ubuntu-server, which is running in the basement. I found several programs to do it the other way around (backup a remote windows machine with linux) but not this way. Please help me!

Kind regards,
Fabian

---

### Post by shintaomonk on 2017-12-07
You could use Samba to mount your server on as a drive on your windows 10 pc, and from there copy the directory. You'll need to install Samba after you upgrade if you need to restore to backup

Heres the link to the samba page
[https://www.linux.com/news/using-samba-share-files-between-linux-and-windows](https://www.linux.com/news/using-samba-share-files-between-linux-and-windows)

---

### Post by cc1984 on 2017-12-07
What kind of backup are you looking to do? What kind of "files" do you have to backup? How much data do you have to backup? Where are you going to put the backups?

You could use rsync which is nice in that it will maintain the ownership and permission settings. You could also use clonezilla in addition to rsync which would take an image of your machine. Then if the upgrade process had an issue you could always do a complete restore to the way it is now. However you would not be able to access files from the image, that would be a complete system restore. If you had the storage, I think a combination of the two would be really useful. 

I use rsync to backup all the data files and databases that are most important on our server to two 6Tb external hard drives. This backup is run every week with one of those external hard drives taken off site. I also use rsync to backup all the necessary data files on my laptop. rsync is very flexible and there is a gui (grsync) if you preferred that.

---

### Post by SeijiSensei on 2017-12-07
Migrating a server is a task that require thought and planning.

Unless you have some sort of custom installation, the first place to start is /home. Every backup needs to include that. Once we get to services and configuration files it get much more complicated quickly.

What does the server do now?  Have you installed custom packages?  You can create a list of all installed packages using the command "sudo dpkg --set-selections" then read that file into dpkg on the new machine and the same packages will be installed.  From a terminal type the command "man dpkg" and read the sections about --set-selections and --get-selections.

If you've created custom configuration files for services like Apache httpd or Samba, most of them will be stored under /etc which needs to be backed up as well.  I'd discourage a mass overwrite of /etc on the new machine with the contents of /etc on the old machine.  As tedious as it may be, I'd take each installed service one-at-a-time and see if the file from the previous version like /etc/samba/smb.conf works on the new version without problems.   There may be ways to do this globally like using "do-release-upgrade", but I tend to be more conservative in these matters.

So, then, what services is this machine providing?

---

### Post by flutz on 2017-12-08
Thank you for your numerous answers. The server is used for theoretical chemistry and calculations. Best-case scenario would be to create a backup of everything on the server, so that I can restore the actual state in case I cause trouble during the upgrade. I would store the backup-data on my local machine (windows computer), it will be about 900gb
I tried using acrosync, but that only copies the files but deletes ownership.

I'm sorry that I can't give you very detailed information because I'm still quite new to linux and this whole server-business, but what I want (in laments terms) would be any way to just secure all data on my local computer (including ownerships) so that I can just restore the server to its actual state if I cause any problems during the upgrade?

---

### Post by agillator on 2017-12-08
Working over a network is going to be slower than simply transferring files around on the computer. From what you describe I would get an external drive of at least a TB if I didn't already have one, plug it into the server and use rsync to copy everything you need (or everything, period). Then remove the external drive and store it somewhere safe. It is still going to take time to transfer a TB, but it will be much faster than working over any network. It also has the advantage of not relying on another type of OS (Windows) for anything. Further, if you ever need to restore it will only be a matter of copying the necessary files.   Once your new system is set up, I would seriously consider one of the rsync based backup programs (I use rsnapshot) to maintain current backups of the server so you don't run into this again. The advantage of rsnapshot and other programs like it is that they use hard links for files that haven't changed. This normally makes backups after the first much faster and they take up far less space unless a large percentage of files change between backups. This easily gives you a series of backups so you can go back as far as necessary to recover a certain version of a file or files.

---

