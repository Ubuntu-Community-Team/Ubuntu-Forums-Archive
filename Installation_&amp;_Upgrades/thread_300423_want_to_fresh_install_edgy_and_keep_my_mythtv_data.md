---
title: "want to fresh install edgy and keep my mythtv data"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by lokimon on 2006-11-15
so i have been running a dapper mythtv box for a few months now, and am thinking about making the upgrade to edgy, due to the new mythtv being out for edgy and the simpler install.

i want a fresh install of edgy rather than an upgrade, because i think it will be more stable, and i have seen horror stories about the upgrade route.

i want to keep my recorded programs, and am not quite sure about how to do this.

i have a separate partition for / /home and swap, so i think that i can just format the / partition, and leave the /home one alone.

HOWEVER, i have heard that mythv isn't happy if the user "mythtv" already exists during setup.

so, should i make another folder "foo" in the /home partition and put the old mythtv home dir in there, and then copy everything into the new one after the install?

is there a method to doing all this that i don't know about?  i tried to search for a howto but found nothing.

---

### Post by lokimon on 2006-11-16
no one has any idea if what i'm suggesting will work?

my main concern is that without the SQL database, it won't know what video file is from what show.

---

### Post by Tim Prosser on 2006-11-16
I've done this a few times (including moving from Mandrake), and its not too difficult.

All you have to do is keep all the recorded files in the same path after the upgrade (copy them elsewhere while you rebuild if you need to), and crucially, backup the database so you can restore it later.

This is easier than it sounds - its just the directory /var/lib/mysql/mythconverg.

If you install all of mythtv on Edgy it should create an initial database - stop the mysql and mythtv services, delete it, and copy your backup in place, and the mythbackend should upgrade it to the current myth version automatically, retaining your recording data (and your settings).


The commands for the database will look something like this...
```

sudo /etc/init.d/mythtv-backend stop
sudo /etc/init.d/mysql stop
sudo cp -R /var/lib/mysql/mythconverg /your/backup/drive/

(rebuild with MythTV 0.20)

sudo /etc/init.d/mythtv-backend stop
sudo /etc/init.d/mysql stop
sudo rm -f /var/lib/mysql/mythconverg/*
sudo rmdir /var/lib/mysql/mythconverg
sudo cp -R  /your/backup/drive/mythconverg /var/lib/mysql
chown -R mysql:mysql /var/lib/mysql/mythconverg
sudo /etc/init.d/mysql start
sudo /etc/init.d/mythtv-backend start

```


I usually have the mythconverg directory in my backups anyway, as it would be a real pain to have it screw up.  Do check everything gets copied before you rebuild!

Good luck!

---

