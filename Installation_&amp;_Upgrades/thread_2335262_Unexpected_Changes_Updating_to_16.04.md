---
title: "Unexpected Changes Updating to 16.04"
date: 2016-08-26
forum: Installation &amp; Upgrades
---

### Post by Iflana on 2016-08-26
I booted into ubuntu 14.04, which I was happy with, and it prompted me to upgrade to 16.04.  It was late and I didn't read everything properly, and in the process it updated some items like phpmyadmin, php, and mysql that I had installed for a local development web server.  Unfortunately, that's caused major issues & now nothing works.  I don't want to run newer versions as I know the web application I was using locally doesn't work on newer versions.  Is there a way to roll back to 14.04 with the previous versions of everything I had?

---

### Post by TheFu on 2016-08-27
Sure! Restore from a backup taken pre-update.  Lacking having backups, I don't know. Sorry.  Making backups is requirement for all computers, after all. Making a fresh backup prior to doing anything major (even weekly patching) is a best practice, assuming daily, automatic, versioned, backups aren't already in-place.

To get the most important things backed up, [https://askubuntu.com/questions/9135/how-to-backup-settings-and-list-of-installed-packages](https://askubuntu.com/questions/9135/how-to-backup-settings-and-list-of-installed-packages)
This does NOT backup data, but most of that would be in ~/ or in places that you should know well - after all, you put it there.  Places like /var/www ... 

Anyway - having a backup is a basic thing everyone should do. The system settings and list of packages is a minimal amount of data, so having 90 days of versioned backups for this critical information isn't a big storage requirement.  I'd be surprised if more than 300MB was needed for all those backups (using a smart backup tool).

Just sayin'.

---

### Post by Trogladyte on 2016-08-27
There's no downgrade process that I'm aware of.

If you want 14.04 back, I think your only option is to do a clean install of 14.04 from live cd or thumb drive.

---

### Post by ian-weisser on 2016-08-27
Downgrading is available in the package manager, but the feature is not supported and comes with big ALL CAPS warnings to use it at your own risk...downgrading may cause problems and conflicts that you must resolve manually. Serious problems - your system may fail to boot.

TheFu and Trogladyte are right - restore or reinstall are the two best options.

---

### Post by Iflana on 2016-09-04
> **ian-weisser said:**
> Downgrading is available in the package manager, but the feature is not supported and comes with big ALL CAPS warnings to use it at your own risk...downgrading may cause problems and conflicts that you must resolve manually. Serious problems - your system may fail to boot.

TheFu and Trogladyte are right - restore or reinstall are the two best options.

Is what you're talking about the same as restoring a backup made prior to the upgrade?

---

### Post by ian-weisser on 2016-09-06
Downgrading uses apt to uninstall a newer package, replacing it with an older package. The feature exists, but is not supported.

Restoring from a backup is an entirely different method of undoing an upgrade.

---

