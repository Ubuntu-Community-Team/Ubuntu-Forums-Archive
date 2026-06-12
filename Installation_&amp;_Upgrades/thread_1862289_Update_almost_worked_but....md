---
title: "Update almost worked but..."
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by egruber on 2011-10-16
It was going well.  It was almost done with the installing packages portion when it stopped with some error.  It never did the cleaning step or the reboot.  I booted the PC and I was able to boot successfully, but now there are some minor glitches.  For example, if I list all my apps, I don't see all the associated icons.  Just a little white square (like a sheet of paper).  Some are displayed properly, some are not.  I think everything else is OK.  I have all my data files.

Is there any way to have the install 'complete' without having to create a USB or CD image and redo it?  I had a similar problem after the last major upgrade and doing this was a real hassle.

Thanks!

---

### Post by 23dornot23d on 2011-10-16
You could try 

sudo apt-get update
sudo apt-get install aptitude

sudo aptitude update
sudo aptitude safe-upgrade

---

### Post by egruber on 2011-10-16
> **23dornot23d said:**
> You could try 

sudo apt-get update
sudo apt-get install aptitude

sudo aptitude update
sudo aptitude safe-upgrade

I tried these, but I did not see any noticeable difference after it was done.  But I found the fix in this thread.  Just change the theme and change back!

[http://ubuntuforums.org/showthread.php?t=1860830&highlight=missing+icons+upgrade](http://ubuntuforums.org/showthread.php?t=1860830&highlight=missing+icons+upgrade)

---

