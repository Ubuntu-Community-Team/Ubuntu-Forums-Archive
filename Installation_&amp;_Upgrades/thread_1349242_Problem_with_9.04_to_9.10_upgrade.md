---
title: "Problem with 9.04 to 9.10 upgrade"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by abhatt on 2009-12-08
I had Ubuntu 9.04 (w/ Gnome) installed on my laptop.  This evening, I decided to upgrade the distribution to 9.10 using the "Update Manager".  I did not have all the latest packages (and in particular, not the latest kernel) when I started the upgrade.  Everything was going fine with the upgrade, until the very end, when it said that there was an error with the installation of the linux-restricted-module-* package.   I didn't quite know what to do.  I hit "OK", finished the update, and then the system restarted.

After the restart, there was the shiny new startup screen, but my mouse wasn't working.  Also, no sound.  After I logged in, and went to the Synaptic package manager, I saw there was an error.  It wanted to remove the linux-restricted-modules-2.6.28-15-generic package but could not.  One of the error messages was: "FATAL: Could not open '/boot/System.map-2.6.28-15-generic': No such file or directory".  Using the advice from [http://ubuntuforums.org/showthread.php?t=831658](http://ubuntuforums.org/showthread.php?t=831658) , I managed to address this problem, and the "sudo dpkg --purge linux-restricted-modules-2.6.28-15-generic" command finished successfully.


After this, I restarted my system and, as expected, the mouse and sound were still not working.  Running 'uname -r' gives "2.6.28-16-generic".  So, I now went ahead with the command "sudo apt-get install linux-restricted-modules-$(uname -r)".  Now, I get the following error:

> 
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package linux-restricted-modules-2.6.28-16-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-restricted-modules-2.6.28-16-generic has no installation candidate


I'd really appreciate some help.  Thanks in advance!  If it makes any difference, I'm on a 64-bit machine.

---

### Post by zkriesse on 2009-12-08
Hmmm it *SOUNDS *like your Packages or Repositories are screwed up...have to fix that won't we? :)

---

### Post by abhatt on 2009-12-08
> **ZachK_ said:**
> Hmmm it *SOUNDS *like your Packages or Repositories are screwed up...have to fix that won't we? :)

Yes, we would :)  But how do I go about reinstalling the restricted modules package?

---

### Post by zkriesse on 2009-12-09
Not sure...research this I shall.

---

### Post by abhatt on 2009-12-09
> **ZachK_ said:**
> Not sure...research this I shall.

Thanks!  Any help will be really appreciated.

---

