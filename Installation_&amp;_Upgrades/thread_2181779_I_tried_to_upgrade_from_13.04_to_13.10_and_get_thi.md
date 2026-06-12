---
title: "I tried to upgrade from 13.04 to 13.10 and get this error:"
date: 2013-10-19
forum: Installation &amp; Upgrades
---

### Post by Zewbie on 2013-10-19
```
Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu
```

---

### Post by deadflowr on 2013-10-19
Is this from the do-release-upgrade command?

Try running the software updater.
Let the updater update the system as normal, and when it finishes the normal updates it will have an upgrade button and ask if you want to upgrade to a newer version.

If you have PPAs installed the method through the software updater should disable the PPAs, which will make the update run properly.

---

### Post by Johan De Cauwer on 2013-10-19
Did you read the sticky thread about 'tried to upgrade'? I won't repeat it here, it's too long but one general truth is that a clean install is always the best...

---

### Post by Zewbie on 2013-10-19
It's from the normal "Software Updater" program.  Says "The software on this computer is up to date.  However 13.10 is now avalible. (You have 13.04).  Then I get the 'Could not calculate' error after when in "Setting up ne software channles"

EDIT: I also have all PPA disabled.

---

### Post by Zewbie on 2013-10-19
ran this command "sudo apt-get remove xserver-xorg-video-*" and it seems to be updating now...  Will report back no matter what.

---

### Post by Zewbie on 2013-10-19
Looks like that did the trick...  still upgrading so will see how it goes after reboot.  Thanks for replays and views

---

