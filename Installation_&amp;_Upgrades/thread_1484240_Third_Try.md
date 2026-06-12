---
title: "Third Try"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by pbhill on 2010-05-15
I'm on my third upgrade attempt of 10.04. 
Each time has been unsatisfactory so I've waited a couple of weeks to see if the problems straighten out. 
 * I have no sound through Firefox. 
 * Ubuntu hangs frequently.
 * I can't install applications
 * I get this message when trying to update:
 
> 1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/79.5kB of archives.
After this operation, 24.6kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 210198 files and directories currently installed.)
Preparing to replace icedtea6-plugin 6b16-1.6.1-3ubuntu3 (using .../icedtea6-plugin_6b18-1.8-0ubuntu1_i386.deb) ...
update-alternatives: error: /var/lib/dpkg/alternatives/mozilla-javaplugin.so corrupt: invalid status
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
update-alternatives: error: /var/lib/dpkg/alternatives/mozilla-javaplugin.so corrupt: invalid status
dpkg: error processing /var/cache/apt/archives/icedtea6-plugin_6b18-1.8-0ubuntu1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
update-alternatives: error: /var/lib/dpkg/alternatives/mozilla-javaplugin.so corrupt: invalid status
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/icedtea6-plugin_6b18-1.8-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I have tried to uninstall / reinstall icedtea but I get a message to upgrade before uninstalling. (?) Can't do it.

I'm a bit fed up, and can stay with 9.10, but wonder what's going on?
Any ideas?

---

### Post by kansasnoob on 2010-05-15
This is only a wild guess, but might provoke some thought.

The following relates to a different package but I wonder if the dpkg "force" commands might help with that package:

> Upgrade 8.04 -> 10.04 can break apt-get.
The package flashplugin-nonfree has been problematic when upgrading 8.04 -> 10.04 and breaks apt-get;

Bug Report

For those not wanting to read the bug report in detail, the fix is :

Code:

sudo rm /var/lib/dpkg/info/flashplugin-nonfree.prerm

sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
sudo dpkg --purge --force-remove-reinstreq flashplugin-nonfree



[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

Or, from the same thread:

> Java.
Sun java has been deprecated. Openjdk is now the default, i.e installing ubuntu-restricted-extras with recommends will install openjdk and the icedtea plugin. Openjdk has been certified by Java SE Test Compatibility Kit (TCK) and is compatible with the Java(TM) SE 6 platform on the amd64 (x86_64) and i386 (ix86) architectures. However sun-java is in the partner repo.
There's a bug regarding the icedtea plugin and certain applets.
[https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/551328](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/551328)
Not fixed yet. Workaround may be to create a new Firefox profile.

---

### Post by Soul-Sing on 2010-05-15
indeed a conflict between openjdk en sun java (plugin) stuff
i should take a look at /var/lib/dpkg/info via ```
gkudo nautilus
``` and remove the conflicting elements, and I would focus on java.
After that ```
sudo apt-get update
```

---

### Post by pbhill on 2010-05-15
Thanks for the suggestion. Tried removing sun java plugins. No difference. Get this message when updating:

> E: icedtea6-plugin: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.

---

### Post by Soul-Sing on 2010-05-15
> **pbhill said:**
> Thanks for the suggestion. Tried removing sun java plugins. No difference. Get this message when updating:

this could be removed also via synpatic package manager? apt-remove/ purge
or: ```
sudo dpkg --remove --force-remove-reinstreq icedtea6-plugin
```

---

### Post by pbhill on 2010-05-15
That didn't work either:

> dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: warning: files list file for package `sun-java6-plugin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sun-java6-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sun-java6-jre' missing, assuming package has no files currently installed.
(Reading database ... 209501 files and directories currently installed.)
Removing icedtea6-plugin ...
update-alternatives: error: /var/lib/dpkg/alternatives/mozilla-javaplugin.so corrupt: invalid status
dpkg: error processing icedtea6-plugin (--remove):
 subprocess installed pre-removal script returned error exit status 2
update-alternatives: error: /var/lib/dpkg/alternatives/mozilla-javaplugin.so corrupt: invalid status
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 icedtea6-plugin


---

### Post by Soul-Sing on 2010-05-16
gksudo nautilus

remove via nautilus these package in /var/lib/dpkg/info

- icedtea6-plugin
- mozilla-javaplugin.so

after removing them, close nautilus.

```
sudo apt-get update
```

repeat this in /var/lib/dpkg/status

---

### Post by pbhill on 2010-05-17
I am so frustrated with Ubuntu. I've reinstalled 9.10 AGAIN. I'm going to wear that disc out. No more upgrades for me. I'll wait for a disc. Maybe I'll try a different distro.

   But wait! Now I have a brand new problem!
I now can't boot into XP on my dual boot system. This is something I've never had a problem with. I need XP only to run my CAD program, and now I have a project half done that I can't access. The partition is there, just can't boot into it. Only get a blinking cursor.  I'm going to bed and sleep until next Friday.

---

### Post by pbhill on 2010-05-17
OK, so I didn't go directly to bed. I did a bit of research and found out what was wrong. My fault, well, maybe... maybe not. 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")
Not too hard to fix, even for me!

---

