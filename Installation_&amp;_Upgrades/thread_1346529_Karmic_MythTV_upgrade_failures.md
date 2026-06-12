---
title: "Karmic MythTV upgrade failures"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by jonny on 2009-12-05
I've been using Ubuntu and MythTV since the original Warty Warthog release in 2004, but, despite my fairly extensive experience, upgrading MythTV from Jaunty to Karmic was a major challenge.  I've dumped my experiences in this post in case it helps anyone else, not least because Google usually puts threads in these forums near to top of its search results.

**Summary of issues**
To summarise, I had the following problems on upgrade:
 - MySQL failed to upgrade properly.  MythTV depends on MySQL
 - MythTV wouldn't update my database to the latest version
 - My list of recorded programs spontaneously disappeared
 - My tuner card stopped working

Let's take these one by one.

**Failed MySQL Karmic upgrade**
Problem: On upgrade to Karmic, MySQL failed.  I couldn't log in to my MySQL server through MythTV or directly. 
Solution:
[LIST=1]
[*]For some reason, Update Manager removed the MySQL server package from my system.  The problem was easily fixed by reinstalling the mysql-server package using Synaptic package manager.
[*]My MySQL installation had a legacy entry in its configuration file that caused the latest version to fail.  The answer was to edit the file ```
sudo gedit /etc/mysql/my.cnf
``` and place a # symbol in front of the line containing skip-bdb.  After correction it looks like this: ```
#skip-bdb
```
[/LIST]
After this, I could start MySQL with this code ```
sudo service mysql start
```

**Failed MythTV server installation**
Back in the days of the Breezy Badger, I'd installed the back and front ends of MythTV separately.  Possibly because of this, Update Manager uninstalled the MythTV-backend package.  This was easily fixed by choosing the correct packages in Synaptic and reinstalling.

However, I then found that when I started MythTV, I received error messages about mismatched database versions.  Despite using the MythTV Setup program on the Administration menu, the database failed to upgrade.  I eventually discovered the reason is that the database upgrade scripts are found in the mythtv package - which I hadn't installed - and not where you'd expect them to be in the mythtv-backend package.  Installing the extra package did the trick, but I still found that I had to run the database upgrade scripts by hand (instructions can be found in MythTV's mailing lists), probably because of the order that I'd installed the packages.

**Missing recorded programmes**
My next problem was that I couldn't see my recorded TV programmes.  The problem has been reported by other users who've upgraded from very early versions of MythTV, and the solution is to run this command: ```
mysql -umythtv -p mythconverg -e "UPDATE recorded SET bookmark = 1 WHERE bookmark != 0;"
```This command will ask you for your MySQL password, which can be found in the file /etc/mysql.txt.

**TV Tuner card failure**
At first, my Hauppage Nova-T 500 DVB-T tuner card wouldn't work with Karmic.  I tracked this problem down to an incompatible firmware version, and it was easy to fix by forcing a firmware reload.  I powered down the PC and removed the power cable for 10 seconds, and on reboot everything appeared to work perfectly.

However, on close inspection, I found that some of the lesser-known channels were no longer available.  The problem was that the signal amplifier on the tuner card had been turned off, a problem that was fixed by adding a module configuration directive to the driver.  I created a configuration file with is command```
sudo gedit /etc/modprobe.d/options.conf
```and entered this text```
#Nova-T 500 Signal Amplifier
options dvb-usb-dib0700 force_lna_activation=1
```On restarting my PC, all my missing channels became available.

Hopefully my experiences will help someone.

---

### Post by drifting on 2010-01-08
Very usefull and duly bookmarked as when the insanity takes me to upgrade, I am sure I will need it.

Paul

---

