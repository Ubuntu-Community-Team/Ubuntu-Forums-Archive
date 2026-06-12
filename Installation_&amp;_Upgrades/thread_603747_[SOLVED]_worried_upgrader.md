---
title: "[SOLVED] worried upgrader"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by DarinB on 2007-11-05
i know that as time marches on i will eventually have to upgrade to gutsy then heron, since it will be a long tern support.
i have made so many changes to my system i don't know where to start, so should i do a clean install.
what steps should i take?? can i save all my stuff and just put it back?
if i do an upgrade what will i lose i.e. docx support etc. 
i also have regular issues with my ge force mx440 i just remove all kernel changes that add nvidia glx and i am back and running? And Gutsy has the nvidia drivers already there will it cause problems??
i need to do some homework before i do this...any ideas from the community??
Thanks 
D

---

### Post by milton1 on 2007-11-05
1. back up anything you don't want to lose.

2. make a list of all apps you use and may need to reinstall.

3. edit your /etc/apt/sources.list changing all 'feisty' to 'gutsy'

4. ```
sudo apt-get update

sudo apt-get dist-upgrade
```

if it works, great. If it breaks, do a fresh install.

---

### Post by jkounis on 2007-11-05
I don't know how your system is configured, so it's hard to advise you precisely, but here's how I do a major upgrade. I have my /home directory on a separate partition than /, so it's easier to backup just the system files and leave user data intact. i also have several mysql databases (e.g. mediawiki, Drupal, etc.) that need to be backed up, and are not normally backed up by a tar -cv /

    *  Backup the mysql databases
          o First, backup all of them: 

mysqldump -uroot -p<pwd> --all-databases > backupfile.sql

    * Then, backup the databases one at a time: 

mysqldump -uroot -p<pwd> <database1> > backupfile.sql
mysqldump -uroot -p<pwd> <database2> > backupfile.sql
mysqldump -uroot -p<pwd> <database3> > backupfile.sql
...

    * (The reason to back them up independently, is that you may not want to restore the mysql database after the system install, especially if you've upgraded versions of programs like mediawiki that may make changes to that database.
    * Boot to the Ubuntu Live CD
    * Backup the / partition with partimage, as described in [http://psychocats.net/ubuntu/partimage](http://psychocats.net/ubuntu/partimage).
    * Backup the individual files from the / partition to another directory, too, if possible, since you may need to refer to them one file at a time (e.g. /etc/hosts or /etc/fstab) 

sudo mkdir /rootfs
sudo mount /<root partition> /rootfs
sudo mkdir /backupdir
sudo mount /<backup partition> /backupdir
sudo rsync -av /rootfs /backupdir

    * Install the system, following the Initial Server Setup Procedures
    * Restore the mysql backup, either all at once: 

mysql -uroot -p<pwd> < backupfile.sql

    *
          o or one at a a time: 

mysql -uroot -p<pwd> 
mysql> create db1;
mysql> create db2;
mysql> create db3;
mysql -uroot -p<pwd> db1 < backupfile-db1.sql
mysql -uroot -p<pwd> db2 < backupfile-db2.sql
mysql -uroot -p<pwd> db3 < backupfile-db3.sql

---

### Post by DarinB on 2007-11-05
how do i do step 3 or better what does it mean edit??

3. edit your /etc/apt/sources.list changing all 'feisty' to 'gutsy'
What is step 4 how to do step three?? OR how to upgrade via terminal an if so why not use upgrade manager?
4.
Code:

sudo apt-get update

sudo apt-get dist-upgrade
sorry i am really still a noob 
once i survive an upgrade i may no longer be a noobie 
lastly i do not have a separate home partition can i make one and transfer my home folder to it and not kill my machine? and what about my nvidia geforce mx440 issues buy a new card and if so which one?
D

---

### Post by Pumalite on 2007-11-05
You can do this:

sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list

sudo apt-get update

sudo apt-get dist-upgrade

---

