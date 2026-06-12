---
title: "how to Kubuntu upgrade to 7.10 &quot;gutsy&quot; using CD???"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by jetpeach on 2007-10-18
wow, **nevermind this whole thread **and my bug. stupidly not typing the command correctly for upgrading...
kdesu "sh /cdrom/cdromupgrade"


Question: howto upgrade Kubuntu from 7.04 to 7.10 using a CD, such that no internet connection is necessary.

1) download the alternate Kubuntu CD (not the regular).

2) insert into drive

3) ??????

Kubuntu, which doesn't quite get the respect it deserves by Ubuntu, can't be upgraded using the CD as easily as GNOME ubuntu. First, the commands here:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
are worthless, since inserting the CD in kubuntu does exactly nothing.
Looking on the mounted CD, there is a script file called, "cdromupgrade". oh that sounds promosing, but on running it, ""./cdromupgrade: Permission denied". that's strange, because it says it's executable. probably a problem because of the executability of CD rom permissions, anyone know how to fix?

Doing research, last time (upgrading to 7.04) this was also a major problem
[http://ubuntuforums.org/showthread.php?t=417475](http://ubuntuforums.org/showthread.php?t=417475)

From that thread, a solution was never found, even after the poster tried,
"OK, I copied it (via thumbdrive) to the desktop and clicked on it - but there is no "install package" to click on. It lists "Control.tar.gz", "data.tar.gz" and "debian-binary". The valid Actions seem to be "add file" or "extract". What should I do? extract?
Ok, I 'extracted'. Now, how do I apply the package to Kubuntu? Click on 'control.tar.gz'"

That wasn't me, but last time I tried as well to upgrade from CD rom (I have 4 ubuntu machines! downloading takes DAYS, and what a waste of bandwidth!), but couldn't get it to work. 

Anyway, I filed a bug on this, it is here:
[https://bugs.launchpad.net/ubuntu/+bug/154025](https://bugs.launchpad.net/ubuntu/+bug/154025)

---

