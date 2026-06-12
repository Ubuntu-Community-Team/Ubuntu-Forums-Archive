---
title: "apt-get keeps failing a configure"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by mohnkern on 2008-05-08
The other day I used aptitude to install Bugzilla, and it failed.  After reading some other posts regarding modifications, it finally was able to configure and run.  However now whenever I run sudo apt-get upgrade I get:

Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up bugzilla (2.22.1-2.2ubuntu1) ...
dbconfig-common: writing config to /etc/dbconfig-common/bugzilla.conf
Not replacing deleted config file /etc/bugzilla/dbconfig-params
.: 77: Can't open /etc/bugzilla/dbconfig-params
dpkg: error processing bugzilla (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 bugzilla
E: Sub-process /usr/bin/dpkg returned an error code (1)


Problem is, I don't want to remove Bugzilla, now that I've got it working.  I just want it to act as those its configured, or alternatively, get the configure not to mess things up.

I ran dpkg --configure bugzilla and it generated the same error.

---

### Post by Pumalite on 2008-05-08
Your apt-get is of no use in this state. You have to remove bugzilla and then reinstall it.

---

### Post by mohnkern on 2008-05-08
Disappointing, but okay.  I ran apt-get remove bugzilla.

Then I ran apt-get install bugzilla, and got:

dpkg: serious warning: files list file for package `compiz-bcop' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `compiz-plugins' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `compiz-core' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `compiz-fusion-plugins-unofficial' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `compiz-dev' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `compiz-fusion-plugins-main' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `compizconfig-settings-manager' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `compizconfig-backend-gconf' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `compiz-gnome' missing, assuming package has no files currently installed.
327713 files and directories currently installed.)
Unpacking bugzilla (from .../bugzilla_2.22.1-2.2ubuntu1_all.deb) ...
Setting up bugzilla (2.22.1-2.2ubuntu1) ...
dbconfig-common: writing config to /etc/dbconfig-common/bugzilla.conf
Not replacing deleted config file /etc/bugzilla/dbconfig-params
.: 77: Can't open /etc/bugzilla/dbconfig-params
dpkg: error processing bugzilla (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 bugzilla
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Pumalite on 2008-05-08
Do you have an 'upgrade' to Hardy or a clean install?

---

### Post by mohnkern on 2008-05-08
Upgrade

---

### Post by SukiSuki on 2009-09-29
> **mohnkern said:**
> 
dpkg: serious warning: files list file for package `compiz-core' missing, assuming package has no files currently installed.


Reinstalling the offending packages fixes this problem for me.

sudo apt-get install <list of offending packages> --reinstall

ref:[http://www.linuxquestions.org/questions/debian-26/apt-get-dpkg-error-files-list-file-...-missing-final-newline-271118/#post3701175]("http://www.linuxquestions.org/questions/debian-26/apt-get-dpkg-error-files-list-file-...-missing-final-newline-271118/#post3701175")

---

