---
title: "Error from Update Manager"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by Specks on 2007-11-21
The update manager is prompting me that there are available updates to install. When I click the icon in the notification area to open update manager I get the following error:
> 
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Read error - read (5 Input/output error), E:The package lists or status file could not be parsed or opened.'


I believe I just updated some stuff yesterday or the day before, so it was working very recently.

---

### Post by Specks on 2007-11-21
when I try to 'sudo apt-get update' I get the same error
> 
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.


---

### Post by ruibernardo on 2007-11-21
Hi Specks,

the status file is a text file with a list of all the packages that are installed on your system. It says the version of the packages, their dependencies, info, etc. It is a **very important file** for you package manager. **Always make a backup copy of that file before manipulating it for any reason**.

If the package manager says it can't find it, verify if you have the file /var/lib/dpkg/status. 

if you don't, there should be a backup file named /var/lib/dpkg/status-old present. Move it (rename it) to /var/lib/dpkg/status. 

If both those files are missing, there should be another (older) backup copy in /var/backup/dpkg.status.0 

Why three backup of the same file? Because if you loose/remove this file (/var/lib/dpkg/status), every package manager in your system -  dpkg, apt-get, aptitude, Synaptic, etc - will not work and it is impossible***** to bring it up again. Don't mess with the status file and if you do, **always make a backup copy of it - even if you are going to restore a backup of the status file!!!** You've been warned.

* I've seen webpages and scripts to (re)create a new status in Debian by scanning the doc directories, but I didn't get any usable status file in Ubuntu.

I hope that one of the backup files will get you out of trouble.

---

### Post by Specks on 2007-11-21
epimeteo - thank you very much for your help.

The file /var/lib/dpkg/status does exist.

I backed it up to status.bad.bkup then copied /var/lib/dpkg/status-old to /var/lib/dpkg/status. Still get the same error as before.

I then tried copying /var/backups/dpkg.status.0, but still get the same error.

Does this mean my system is stuck where it is, no updates or new packages?

Looks like I've found a new directory to add to my external backup.

---

### Post by ruibernardo on 2007-11-22
Sorry for the late reply, Specks.

Apparently it is not the status file. Restore your status file from the backup you did.

The lists are in the /var/lib/apt/lists/ directory. I've found a thread about a problem similar to yours, maybe it's your case: [http://ubuntuforums.org/showthread.php?t=440883](http://ubuntuforums.org/showthread.php?t=440883)

Good luck.

---

### Post by CFBauer on 2008-06-18
> **epimeteo said:**
> Hi Specks,

the status file is a text file with a list of all the packages that are installed on your system. It says the version of the packages, their dependencies, info, etc. It is a **very important file** for you package manager. **Always make a backup copy of that file before manipulating it for any reason**.

If the package manager says it can't find it, verify if you have the file /var/lib/dpkg/status. 

if you don't, there should be a backup file named /var/lib/dpkg/status-old present. Move it (rename it) to /var/lib/dpkg/status. 

If both those files are missing, there should be another (older) backup copy in /var/backup/dpkg.status.0 

Why three backup of the same file? Because if you loose/remove this file (/var/lib/dpkg/status), every package manager in your system -  dpkg, apt-get, aptitude, Synaptic, etc - will not work and it is impossible***** to bring it up again. Don't mess with the status file and if you do, **always make a backup copy of it - even if you are going to restore a backup of the status file!!!** You've been warned.

* I've seen webpages and scripts to (re)create a new status in Debian by scanning the doc directories, but I didn't get any usable status file in Ubuntu.

I hope that one of the backup files will get you out of trouble.

Your advice is a gift that keeps on giving.  Thanks epimeteo!

---

