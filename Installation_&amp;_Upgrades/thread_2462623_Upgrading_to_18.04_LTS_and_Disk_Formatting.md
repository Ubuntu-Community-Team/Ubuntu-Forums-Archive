---
title: "Upgrading to 18.04 LTS and Disk Formatting"
date: 2021-05-24
forum: Installation &amp; Upgrades
---

### Post by erdemaltuntac on 2021-05-24
Hello,

I am a 16.04 LTS user. I need to upgrade to 18.04 LTS. My current ubuntu version has damaged packages. I have two questions related to upgrading;

1) If I upgrade 18.04 LTS without deleting 16.04 (overwriting), would I have those damaged packages fixed? And, would I lose any data locally stored on my current disk?

2) Another option to upgrade to 18.04 LTS is to format the disk, and installing the new ubuntu. Is there any software formatting the disk?

Thanks for the responses already.

Cheers,
Erdem

---

### Post by GhX6GZMB on 2021-05-24
I'd do this in a completely different way.

First, back up your /home directory completely.

Second, do a live boot with a 20.04.2 installation DVD/USB and do a complete new install. The installer will give you format options in the "Partitioning" section.

Upgrading from 16.xx to 18.xx to 20.xx is tedious to say the least.

Downside is, that you'll lose your installed programs and settings and need to reinstall them.

Upside: you'll have a clean, new install with no quirks and deadwood.

Jst my personal opinion.

---

### Post by tea for one on 2021-05-24
Good advice from [COLOR="#0000FF"]ml9104[/COLOR].

Also, it is good practice to install in UEFI mode with GPT.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by guiverc on 2021-05-24
I've got a 16.04 system I've been wanting to upgrade to 20.04 for awhile... and with luck will have time this afternoon to do it  (*I've said that before!*)

I'm not going to *release-upgrade* as the box will likely run into disk space issues if I try, and given a *release-upgrade* takes so long, I don't want that hassle.

I'd opt for a *upgrade via re-install*.

ie. I'll boot & use "*Something else*" (or "*Manual*" , "*Manual Partitioning*") option, select my existing partitions and ensure I don't format any.

This will cause the installer to 

- note my packages
- erase system directories
- install system
- restore additional packages I had installed if available for the new release
- won't touch my user files (unless I formatted)

Yes I'll expect a **warning** that some packages cannot be restored (esp. given I'll jump from 16.04 to 20.04, Qt4 & python2 were both removed in 2019 & I'm not going to check to see if I have any packages that no longer are available in 20.04; but I'm 75% expecting that warning so it won't be a surprise).   It'll ask me to reboot, so I can look at the change & use the *newer** focal* system on that laptop.

This method allows you to *skip* releases, or re-install the same release (*should you stuff something up.. a great relief when we're learning!*).   Any user config issues however will remain; as $HOME (your user directory) isn't touched so any issues that exist there will remain present.

As system directories are wiped; any package issues will be gone.. but I often do a final boot (*prior to re-install*) & clean/remove unwanted software, or software that I know may not exist in the later release (*thus reducing the chance of the package warning*) but if I don't do that; it just means a higher chance of the warning message (some packages could not be re-installed) that isn't a concern to me or a working system.


Formatting can be done in many ways; `gparted`, `gnome-disks`, KDE Partition Manager... or in the installer itself..  I like `gparted` as I'm most familiar with it, but it's optional (and can be done inside installer; though maybe worth doing first if using a `calamares` install)

---

### Post by TheFu on 2021-05-24
Support for most 18.04 desktop already ended. Only the Gnome3 version is still supported. Best to do a fresh install of 20.04.

Backup your HOME.
Before you do that, backup a list of manually installed programs first.  **apt-mark showmanual > ~/list-of-manual-programs.txt**. 
Backup any special settings you might have done.  Most will be in /etc/, but if you are into installing fonts or themes, those could be elsewhere.  Since 16.04, all the GUI stuff has changed to Gnome3, so themes aren't exactly useful anymore.

These backups have to be done even if you are **sudo do-release-upgrade**.  BTW, if there are broken packages, NO they will not be magically fixed.  For the upgrade process to work, everything needs to be in good condition BEFORE starting.  I've attempted it and ended up with a system that wouldn't boot, so be prepared for that.  Hence, why we are saying to backup the stuff you don't/cannot lose.  Backups cannot just be a copy of the files and directories.  They need to retain the owner, group, permissions, ACLs and xattrs too. In your HOME directory, a copy is probably fine, except a few directories must have specific permissions/ownership to work - like ~/.ssh/ must be 700. But for /etc/ and themes and fonts, those absolutely must have the full permissions retained.

Do a fresh install wiping everything, restore your HOME, put some the the special settings back, then take that list of manually installed programs ... ~/list-of-manual-programs.txt in your HOME on the new install and feed that into  
```
sudo apt-mark manual $(cat ~/list-of-manual-programs.txt)
sudo apt-get -u dselect-upgrade
sudo apt-get -f install
```
and you will have all the manually installed programs reinstalled, using the settings from the specific restored /etc/ files and personal settings from your HOME directory.  As far as getting back to a system nearly the same as what you had before, this is pretty painless.  

Caveats:
[LIST]
[*]The order of the restore is very important.
[*]Don't just sling everything from the old /etc/ into the new /etc/ . that will break the system. It needs to be just those specific files, perhaps 5-15 of them, that get put into the new install.
[/LIST]
Depending on where you keep the huge files, doing these things should only take 30-45 minutes.

I think all the methods outlined above will work. It is just the results which are slightly different.

---

### Post by erdemaltuntac on 2021-05-28
Thanks. I successfully upgraded to 18.04 through the system without losing anything. But, I now have a different problem with upgrading to 20.04.
I posted the question already on a different thread, [here]("https://ubuntuforums.org/showthread.php?t=2462826") .

---

