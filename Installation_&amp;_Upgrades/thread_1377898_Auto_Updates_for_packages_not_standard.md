---
title: "Auto Updates for packages not standard"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by VideoRoy on 2010-01-10
I am moving from Fedora on this particular computer and I was wondering if I install something like VLC media player, will the Auto Software update look for new releases it they come out?

In Fedora yum and the software updater will look for updates on packages that are installed from other repositories and just wondering if Ubuntu has the same function.

Thanks.

---

### Post by snowpine on 2010-01-11
Hi VideoRoy, VLC is in the Ubuntu repositories, and if installed, it will automagically be upgraded through the regular Update Manager process.

---

### Post by VideoRoy on 2010-01-11
> **snowpine said:**
> Hi VideoRoy, VLC is in the Ubuntu repositories, and if installed, it will automagically be upgraded through the regular Update Manager process.
 
Thanks for the reply. I guess this is probably true for anything I install from the Software Manager. The only reason I asked is there are some warnings on some of the packages I wanted to install and it lead me to believe they may not be.
 
I appreciate the help.

---

### Post by slakkie on 2010-01-11
> **VideoRoy said:**
> Thanks for the reply.  I guess this is probably true for anything I install from I can find in the Software Manager.  The only reason I asked is there are some warnings on some of the packages I wanted to install and it lead me to believe they may not be.
 
I appreciate the help.

Yes, everything installed by apt (via the various front-ends) will be managed by apt and will be upgraded if apt "sees" there is a newer version available. 

What kind of errors/warnings did you get?

---

### Post by VideoRoy on 2010-01-11
I did this yesterday so I might be a little fuzzy on this one but there was a warning, not really and error.  I was setting up a new system so I was installing lots of stuff but it was something to the effect that "this is a 3rd party application ....".
 
The other thing I noticed was on the Ubuntu main site there was a comment about releases for OS occur every 6 months and packages typically do not get updated unless there were serious bugs / security.
 
Sorry I am not more clear and not in front of the system until tonight.  I think you folks have answered this.
 
Thanks!

---

### Post by snowpine on 2010-01-11
> **VideoRoy said:**
> 
The other thing I noticed was on the Ubuntu main site there was a comment about releases for OS occur every 6 months and packages typically do not get updated unless there were serious bugs / security.

This is correct; Ubuntu has "stable" releases, not "rolling release."

Drop by [http://packages.ubuntu.com](http://packages.ubuntu.com) if you want to see which version of application x is in the repositories for Ubuntu release y. :)

---

### Post by slakkie on 2010-01-11
> **VideoRoy said:**
> I did this yesterday so I might be a little fuzzy on this one but there was a warning, not really and error.  I was setting up a new system so I was installing lots of stuff but it was something to the effect that "this is a 3rd party application ....".
 
The other thing I noticed was on the Ubuntu main site there was a comment about releases for OS occur every 6 months and packages typically do not get updated unless there were serious bugs / security.



Ahh, that message. It will be treated the same by apt. You get that message because the package is not maintained by Ubuntu, so it will not receive updates from the security teams etc.

And yes, Ubuntu (and Debian btw) release a version of their OS and when it is released there will be no updates, other then bugfixes and/or security fixes. This means, if you install Apache 2.2.14 it will never be updated to 2.2.26 within the same release of Ubuntu (or Debian).

See also: [http://ubuntuforums.org/showthread.php?t=1374944](http://ubuntuforums.org/showthread.php?t=1374944)

---

### Post by VideoRoy on 2010-01-11
Great info thanks!  Just getting used to Ubuntu / Debian from other distros.  The small things get me every time ;)

---

### Post by ajgreeny on 2010-01-11
Once you are used to the ubuntu system a bit more, and possibly having searched and listened carefully, there are also a lot of ppa repositories which allow you to install newer versions of some application packages than are available in the distros native repos.

As an example, there are several repos with the newer version of vlc 1.0.2 for jaunty, whereas the jaunty repos still only have vlc 0.9.9a.  Use these ppa repos with care and they can be very useful, but just be warned, they are not supportd by ubuntu, and you are on your own if it all goes wrong.  If things don't work, however, you can easily disable the ppa repo, and install the normal version, so it is not the end of the world.

---

