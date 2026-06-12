---
title: "Aborted upgrade to 8.04: doesn't launch GUI"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by jacobly on 2008-06-19
My girlfriend tried to upgrade her Ubuntu installation from 7.04 to 8.04 using the update manager. Somewhere in between, the computer seemed to freeze up (I think it was actually installing packages) and so she restarted.

Now, on startup she gets to the login screen with no problems but login doesn't complete--instead she gets a brown screen (like a blank desktop) with no icons nor menus and no indication that anything is happening.

I started up in recovery mode and was able to get to a command prompt with no problem. I tried to "apt-get update" and "apt-get upgrade" to try to restart and complete the upgrade but I get a message recommending that I run "dpkg --configure -a".

Running "dpkg --configure -a" repeatedly seems to clear up some problems, but "dpkg --configure -a" also says it runs into too many errors and cannot complete.

I have a Ubuntu 8.04 installation CD (not the alternate installation CD), and I have an internet connection (but no idea how to configure the connection via the command line).

What should I do?

Thanks!

Jacob

---

### Post by prshah on 2008-06-19
> **jacobly said:**
> I run "dpkg --configure -a".

Running "dpkg --configure -a" repeatedly seems to clear up some problems, but "dpkg --configure -a" also says it runs into too many errors and cannot complete.

Take a look at my (solved) thread on how to recover a failed hardy upgrade: [http://ubuntuforums.org/showthread.php?t=780531&highlight=hardy+wonderful](http://ubuntuforums.org/showthread.php?t=780531&highlight=hardy+wonderful)

---

