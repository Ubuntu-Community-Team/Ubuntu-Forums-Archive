---
title: "Firefox auto-&quot;upgrade&quot; offered this morning older than installed"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by questant on 2007-10-23
The auto-upgrade icon this morning offered me:
Firefox
New version: 1.5.dfsg+1.5.0.14~prepatch071011b-0ubuntu1
firefox-gnome-support etc.
This version is older than the one currently installed on the system.
I am using 6.06LTS on several systems (because LTS is in our best interest for administrative purposes).  In order to install extentions for Session Manager (and two others) it was necessary to install 2X.  I did so through ubuntuzilla (as instructed through the Ubuntu Forums).  ubuntuzilla is offering and installing upgrades built on my current version which is  now 2.0.0.7 on our systems (The post at [http://ubuntuforums.org/showthread.php?t=573317&highlight=firefox+upgrade](http://ubuntuforums.org/showthread.php?t=573317&highlight=firefox+upgrade)
is apparently incorrect when it states 7 is windows specific and not for ubuntu.).
The Synaptic upgrade wants to improve my 1.5.0.x version.  This is apparently retrograde.

Thus, there are several questions:

1.  Does ubuntuzilla not upgrade the local software database of installed software on the system to reflect the current version?  If it does not, why is it listed as a solution to the upgrade path?

2.  Would not selecting the 1.5 for install downgrade and break the currently installed version of Firefox (2.0.0.7)?
I have NOT done the so-called upgrade as yet.  I HAVE gone into Synaptic and chose "Fix broken packages" and Synaptic reported they had been fixed.  I then reloaded the repositories and selected Mark Upgrades.  Firefox 1.5 is still listed as an upgrade.

3.  Will doing the current upgrade without including the firefox retroversions drop the retro firefox entries in the future or will they always be there until selected?

4.  If the ubuntuzilla upgrade path is used, what procedures should be followed to add the appropriate version information to the installed software database manually, keeping it in sync with the "official" upgrade path?

5.  Should the apparent lack of sync between the official repository channel and the ubuntuzilla channel be seen and reported as a bug to be repaired?

6.  Last, and a general observation question:  As LTS stands for Long Term Support, why does the upgrade system fall so far behind on versions of some software when that is apparently not the case for later releases?
If this continues to be normative administrative practice, it implies LTS is somewhat a misnomer.

Please advise, especially on #4.

Respectfully submitted.

---

### Post by nanotube on 2007-10-23
you can install the updates coming from the official repositories without worrying about interference with ubuntuzilla.
ubuntuzilla installs in parallel with the repos versions. 

so in summary - you can upgrade from the repos without any worries. 

for some more details, see the ubuntuzilla site, specifically this faq item may be relevant:
[http://ubuntuzilla.wiki.sourceforge.net/#tochome18](http://ubuntuzilla.wiki.sourceforge.net/#tochome18)

---

### Post by questant on 2007-10-23
Thank you Nanotube for your reply.  I proceeded with the upgrade and, as per your information (including the link), the ubuntu Syntactic upgrade did not retro my 2.0.0.7 installation.  Thank you for drawing my attention to the section in the FAQ on the parallel stream installation.  However, the very fact of a need for a parallel upgrade path seems odd.  I'm sure there is a reasoning behind the continued "patch?" type upgrade offered for Firefox but I can only speculate what it might be.  Is there an ubuntu policy statement anywhere which clarifies why the 6.06 LTS version remains so far behind the curve in this instance (and possibly others as well).  Once again, thank you for your reply.

---

### Post by nanotube on 2007-10-24
glad it worked out. :)
there have been a number of discussions on this topic in the forums... basically, a bunch of things in the system depend on the installed ff, and ff depends on a bunch of system libraries. upgrading ff from 1.5 to 2.x would necessitate upgrades to quite a few (a couple of hundred?) other packages, which is quite a job. that's why the repos for dapper are unlikely to ever see ff2. that's the whole reason ubuntuzilla exists (see the background section on the ubuntuzilla site for more info).

---

### Post by questant on 2007-10-24
Thanks once again for your reply.  I apologize for riding this horse to death, but one last question/observation:  Is there any reason whatsoever to continue updating Firefox 1.5x when 2x is present through ubuntuzilla?  It would seem to me that 1.5x could be, and probably should be uninstalled through Synaptic.  The menu icons seem all to point to 2x making the 1.5x more or less like putting a box of stuff in the garage because we don't use it any more.  We could just as well throw it away ... but ... well ... you never know.  That's why we need bigger garages.  It is conceivable that such an uninstall might possibly break other things but I'm impressed with the manner in which Synaptic handles both dependencies on installs and breakage through Edit > Fix broken packages.  Other than an issue some time back with gstreamer and an Opera update, I've not seen that choice fail to resolve my (relatively benign) issues.  With this question/observation, and whatever reply, if any, is received, I consider this thread closed and done.  Thanks again.  I am impressed by the positive, polite and sensitive calibre of this exchange.  How refreshing. :) :) :)

---

### Post by nanotube on 2007-10-24
Hi,
a sensible question, unfortunately removing the default firefox is not recommended, as the repos' firefox rendering engine is used by a bunch of gnome thungs. the following page clarifies:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
> Warning: If you use this guide, do not remove the Ubuntu version of Firefox. Doing so will break the following packages: Yelp (help viewer), Epiphany, Gnome-app-install (Add Applications), Liferea, Blam and any application requiring the Gecko rendering engine.


so... while you could /try/ removing it and see what happens, if you want to stay out of trouble, then just leave it alone. after all, what's a few megs of disk space these days? :)

thanks for asking these questions - i should add all this to the faq on ubuntuzilla site. ;)

---

