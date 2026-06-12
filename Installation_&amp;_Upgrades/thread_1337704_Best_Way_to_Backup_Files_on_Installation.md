---
title: "Best Way to Backup Files on Installation"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by HippieDave on 2009-11-25
I'm having a lot of trouble with my 9.10 upgrade and want to do a clean install.  I don't want to lose my settings and files -- especially my Evolution data.  I have a second hard drive that holds my Windows program and most of my other data files.

What's the best way to back up onto that drive so I can then do a clean partition/format (whatever its called) and then do a clean install of Ubuntu 9.10?

---

### Post by audiomick on 2009-11-25
Evolution has a function to archive itself which works well. It is in the File menu ( or the first one if it isn't called file. Datei in German... )
It has worked well for me a number of times, but I read a post from a bloke today for whom it apparently completely messed up...

Theoretically you can archive the whole home folder out onto your other drive, and put it back later. I've done that too, but the last time I tried, I got hung up on ownership issues. I put it down to a couple of files belonging to root in the home directory ( e.g. .dbus something or other ), but didn't have the opportunity to look into it in depth.

When you do your re-install, make a separate partition for  /home (choose the manual option for the partitioning tool ), then you can just re-mount the old home partition if the question ever arises in the future.

sorry I can't help more than that.
Michael

---

### Post by HippieDave on 2009-11-25
what does keeping /home separate do? I can't tell what data is stored there.

---

### Post by audiomick on 2009-11-25
> **HippieDave said:**
> what does keeping /home separate do? I can't tell what data is stored there.

The system puts all the user related config stuff in /home, and the default store path for everything is to there.

If your /home is in one big partition with the rest of the system, it will get written over if you have to do a fresh install ( not an update with the system updater ). If you have a seperate partition with /home in it, you can keep it and re-mount it in the event of a fresh install. All your configurations are still in place, and all your files are where you left them.

---

### Post by presence1960 on 2009-11-25
want to save your installed packages also? There is a way to save them and as long as they are in the repositories in 9.10 will be reinstalled. here is the how to:

To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

```
dpkg --get-selections > ~/my-packages
```


This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```


It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository. make sure you enable the sources in the previous version (i.e. medibuntu, multiverse, universe, etc) but for karmic prior to running the command to restore packages.

P.S. Back-up your home directory if it is not a separate /home partition. Then restore that back-up to your home directory on the new install. All your software settings will remain as they were in previous install.

---

### Post by HippieDave on 2009-11-25
[I]"Back-up your home directory"

[/I]Just copy onto a disk, or does it have to be backed up with a program that has the restore feature too?

---

### Post by presence1960 on 2009-11-25
> **HippieDave said:**
> [I]"Back-up your home directory"

[/I]Just copy onto a disk, or does it have to be backed up with a program that has the restore feature too?

either way will work!

---

