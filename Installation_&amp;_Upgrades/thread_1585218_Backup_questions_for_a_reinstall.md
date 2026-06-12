---
title: "Backup questions for a reinstall"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by gotsanity on 2010-09-30
I am planning on upgrading my hard drive to a raid 0 array. Most of the threads i have found about backups are all full drive images/archives. Would I run into any issues by performing one of these backups instead of a full reinstall?

If so, is there any ways i can backup just my /home, apt sources and installed software, and related config files?

---

### Post by DJonsson2008 on 2010-09-30
Not sure of your objective,but to replicate drives
I've used 2 methods.

* Cloning drives directly using Gparted.
  I use the direct method on this 
  from drive to drive with this 
  not backing up and restoring images. 
  Easy GUI method, more details can be read in this discussion
  [http://ubuntuforums.org/showthread.php?t=1520450&page=2](http://ubuntuforums.org/showthread.php?t=1520450&page=2)

  This has worked 99% of the time for me, even migrating
  from IDE to SATA drives of different brands. Some people
  though report issues between brands/sizes.

* Backing up key files then restore key files to fresh install.
  This method takes quite a bit more work.

  There may be a better cheat sheet on this somewhere
  but here are my notes.
  
Old Drive
---------
* Make sure all updates are done on old drive.
* Backup \home and \etc directories
* [Optional] Backup \var\cache\apt\archives\*.deb files
* Create a list of packages 
  _sudo dpkg -l | awk '{print $2}' > installed_packages.txt


New Drive
---------
* Install same version of Ubuntu on new drive with same
  username/password as old machine.
* Make sure all updates are on new drive.
* [Optional] Restore \var\cache\apt\archives\*.deb files

As root
* Restored \var \home and \etc directories from backup  files.
* Rebooted just for good luck
* Bulk install apps via list of 
  installed_packages from old machine.
  _apt-get install `cat installed_packages.txt`
   (watch out for those single quotation marks)

Per my experience depending on the complexity of your
install (mine had a lot of customization) this gets
you about 95% there. 
 
Everything usually runs smooth including
restoration of all bookmarks desktop items...

Bulk apt-get install tho may take a little work. 
For instance use gedit to editing
installed_packages.txt to clean out 
headers at the top of what otherwise 
is just a list of package names.

apt-get install may choke on items that
are not in the standard Ubuntu repository, ie 
gimpshop, realplay, skype, webmin and so on. Perhaps 
putting these packages inside of /var/cache/apt/archives,
may resolve this. 

Otherwise; you should 
remove these items from installed_packages.txt; 
run apt-get install `cat installed_packages.txt`
(until all packages install)
and then install remaining apps separately.

---

