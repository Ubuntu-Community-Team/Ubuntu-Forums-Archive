---
title: "new install, freezes before startup. frustrated"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by hughesw on 2007-02-13
new to linux, using ubuntu edgy. after the initial install i upgraded all the bios, drivers, etc. had everything working beautifully, but then after the 2nd reboot it froze about 95% of the way through without ever starting, being the noob that i am, i got so frustrated that i reinstalled edgy and the drivers to only come across the same problem. now after the 3rd install i am about to give up. i would hate to have to revert back to windows. anyone know what to do?

---

### Post by IgnorantGuru on 2007-02-13
I would try some boot options to see if they have any effect, such as acpi=off.

You can read some of the details here
[http://ubuntuforums.org/showthread.php?t=352442](http://ubuntuforums.org/showthread.php?t=352442)

When you say drivers, if you mean proprietary video drivers,  I would save that for later.  Just get it running with the basic setup first, then experiment with adding drivers.

When you say 95%, try to be more specific about where it is freezing - this can give a clue as to what is causing it.

Don't give up.  It's worth the effort.  My move from windows took some effort but I'm very glad I did it.

---

### Post by IgnorantGuru on 2007-02-13
I might add that third-party drivers are a common woe in linux - vendors don't cooperate as well with the linux community as they do with Micro$oft.

My solution is to get the basic system running with the open-source drivers (they are installed automatically).  Then I backup the partition.  Then I experiment with third-party drivers, trying to find an install method that works.  If it fails, I restore the partition from backup.  Much less headache than installing over and over.

Howto backup a partition is here...  worth the effort to master...
[http://www.ubuntuforums.org/showthread.php?p=2148017#post2148017](http://www.ubuntuforums.org/showthread.php?p=2148017#post2148017)

Also, video drivers are often the cause of lockups in my experience.  Be sure you're using the latest.  the file /var/log/Xorg.0.log might give you some clues as to how things are working, or post it here for interpretation.

Another also - the open-source video drivers are fine for most uses.  Where they fall short is in 3D rendering (mostly games and googleearth), TV-out, things like that.  Don't feel you need to get the proprietary drivers working to get to know linux - some people don't use them at all.  If they are what's giving you trouble, I would suggest getting to know other aspects of the system better, then tackle them later when you have a little more experience.  They often require a little more practice.

---

