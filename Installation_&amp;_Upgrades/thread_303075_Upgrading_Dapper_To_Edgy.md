---
title: "Upgrading Dapper To Edgy"
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by AndrewG on 2006-11-19
Hi,

I'm considering upgrading my Dapper workstation (that gets used all the time) to Edgy. I've waited a while since it was released, so would the upgrade bugs have been ironed out yet - is it safe to upgrade now? Should I wait longer? I'd really like some of the Edgy features such as hibernation that actually works, Cairo, faster shutdown/startup times etc.

I'm not sure if my sources.list might stuff things up, so I'll post it here in case anyone knows of any problems that will happen: [www.thewebdruid.com/files/sources.list]("http://www.thewebdruid.com/files/sources.list")

What's the easiest way to do it all? Replacing "dapper" with "edgy" in that file? I've got an NVIDIA graphics card installed - apparently they turn bogus when you're running Beryl. Will this be the case for my 7300GS?

Thanks heaps,

AG.

---

### Post by finferflu on 2006-11-19
Well, in [this howto]("https://help.ubuntu.com/community/EdgyUpgrades") there is a method which they say is the safest one:

> If you want to upgrade from 6.06 LTS to 6.10, run the following command (either via ALT-F2 or a terminal):

gksu "update-manager -c" 

The -c switch instructs Update Manager to look for upgrades. By default, the Ubuntu 6.06 LTS release will not offer that automatically because of its long support cycle and high stability.

If you have a working network connection, it should then inform you about a new release and offer to upgrade your system.

If you have the Edgy Alternate Install CD (not the Desktop CD), you can save bandwidth by using:

gksu "sh /cdrom/cdromupgrade" 

I actually do not know about the issues you are raising, but surely someone will come and help.

Good luck! ;)

---

### Post by AndrewG on 2006-11-19
Here goes!

Wish me luck!

---

### Post by finferflu on 2006-11-19
Let us know what happens, and good luck again! :)

---

### Post by AndrewG on 2006-11-19
I should have changed my repositories first - I'm stuck doing only 305KB/s :(

---

### Post by AndrewG on 2006-11-19
It crapped itself.

> Could not install 'python2.4-minimal'

The upgrade has aborted. Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

subprocess post-installation script returned error exit status 1

But by the looks of it, it's still going past that. I hope my system remains usable once it's finished.

---

### Post by AndrewG on 2006-11-19
> Could not install the upgrades

The upgrade will now abort. Your system could be in an unusable state. A recovery was attempted (dpkg --configure -a).

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

installArchives() failed


Awww. :(

---

### Post by AndrewG on 2006-11-19
It's now working fairly well after playing around with it a lot. At least it didn't completely die altogether during the upgrade procedure. I'm happy that Amarok is now working better than it was - it had difficulty with FLAC files before). Thanks for all your help.

---

