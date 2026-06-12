---
title: "Problem upgrading to gutsy (install step: replacing libpam0g stuck at Debconf window)"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by sulemankm on 2007-10-22
Hi I'm in the middle of upgrade process from fiesty to gutsy.

All the packages have been downloaded and now the install step is in progress.  The problem is that the install step is halted here while installing the replacement libpam0g.  It has displayed the Debconf with a text box and a help button and no other buttons on it.  The dialog box does not seem to respond to any mouse event etc.

What should I do now?  Any help please?  Its urgent and my install process is halted here. I have to complete is successfully.

---

### Post by sulemankm on 2007-10-22
OK I couldn't wait for someone to reply to the last message above and I pressed Ctrl+C in the terminal window of the Distribution Upgrade dialog.  It reported that it could not complete the post install step of the libpam0g package.

After this the installation of the other packages continued but I got one error for many packages.  The error message said that due to dependency problems, it is leaving certain packages unconfigured.  A partial list of such unconfigured packages is given below:

dependancy problem - leaving unconfigured

base-files
bash
adduser
login
ssl-cert
cupsys


Any help on how I can get these packages to configure correctly?

---

### Post by sulemankm on 2007-10-22
And yes, the installation of ntfs-3g package also failed after this.  Is it related to the above problem?

---

### Post by Seisen on 2007-10-22
To answer you first question all you had to do was hit the tab key and it would highlight yes or no or Ok. Now to fix your problem try

```
sudo apt-get -f install
sudo dpkg --configure -a
```

---

### Post by sulemankm on 2007-10-22
OK it has now aborted the installation when it failed to install the dbus package, with the same message that it is leaving it unconfigured.  

It also said that:

The upgrade aborts now. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a).

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
installArchives() failed


By the way there were no Yes, No or OK buttons on the dialog box and it was stuck and not responding to mouse events.

---

### Post by dhanes420 on 2007-10-24
I'm having the same issue.  Looks like the Wacom tablet device is back in my xorg.conf file.  removing that crap and trying again.

---

### Post by dhanes420 on 2007-10-24
Yup, the Wacom tablet BS had been put back into xorg.conf apparently during the upgrade process.  Why wouldn't the vesa driver install leave that alone from the already existing xorg.conf or at least copy it over?

Removed all Wacom entries, along with the bottom 3 (forget what they were, in the screen section i think - stylus). 

Couldn't get the upgrade manager to quit, powered off and on the PC.  Of course, now upgrade manager won't run.

Tried the sudo apt-get -f install sudo dpkg --configure -a, and was told that the database was puked, needed to run sudo dpkg --configure -a first.  Did that and rebooted.

Tried to run the update mananger, said the dbase was hosed and needed to run sudo apt-get -f install.

Did that, now update manager runs. Says I have the option of a partial upgrade, as a previous upgrade didn't complete (no duh).  Running that now, will update after it gets done.

---

### Post by dhanes420 on 2007-10-24
Well, looks like the partial upgrade worked.  I don't think I got the pam stuff loaded since it failed in the middle of that and the terminal window didn't show them being upgraded in the beginning or throughout the upgrade.

But, it's up and working, doesn't seem to be any problems.  

Much easier to fix a borked package dbase in ubuntu than fedora i have to say :)

---

