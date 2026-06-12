---
title: "Request repository upgrade?"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by Umang on 2008-05-03
Hi!
I noticed that many applications in the Ubuntu repository are out of date. I'd like to know how I (and if) I can request for an upgrade (in the repository, so that I can update to the new version)?

Thanks a lot!

Umang

---

### Post by Kowalski_GT-R on 2008-05-03
I guess repositories host the latest stable (or tested) versions of software, to get the latest version, sometimes you must manually install a package.(e.g. aMule)

My Hardy repositories are more up-to-date than Feisty ones though...

Maybe you can ask for help in installing what you're missing...

hope this helps,


Andre

---

### Post by Umang on 2008-05-03
I'm not desperate to get the latest, but I was just wondering why the latest (for some applications, the latest version is more than a month old and it hasn't been updated) isn't on the repositories.

My question actually was, why aren't they updated? Are the latest versions not up because they have not been tested/are not completely stable? Or is it just that the people maintaining the repositories haven't noticed the updates?

Just curious to know the process.

---

### Post by forestpixie on 2008-05-03
The way I understand it is that a version of a piece of software is tested against a particular version of ubuntu and except for security updates it stays at that version.

So for example - 

version 1.1 piece of software tested against hardy, they know it works and it stays like that for ever,except for any security improvements

version 1.2 and then 1.3 get released before the next version (bear in mind it's only a 6 month cycle)

version 1.3 is tested against the new version, and is released with it

version 1.1 will always be the version for Hardy, 1.3 always the version for Intrepid

This page is the amarok packages - [http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=gutsy&release=all&keywords=amarok&sourceid=mozilla-search](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=gutsy&release=all&keywords=amarok&sourceid=mozilla-search)

You can see the different versions against each buntu release.

That is just my interpretation of what I've read, it could be wrong and probably is in some instances.

---

### Post by Umang on 2008-05-03
That seems to make sense... 
Then here's my final quesion:
What's the advantage of using the repos? Why can't I use only .deb files (and sources if required) to install software (if I know its safe)? Is there something cool about the way I upgrade to the new software, or does the software get installed in a way that upgrading to newer versions of Ubuntu is easy?

Thanks a lot!

---

### Post by forestpixie on 2008-05-03
If you use .deb or compile it yourself then it won't update along with everything else.
You can sometimes find repositories for 3rd party software and as it becomes looked after by apt or dpkg it gets update along with the rest.

Also you can find debs for things but that doesn't always mean that it won't cause problems with other installed software.

I haven't actually used any 3rd party repos other than medibuntu - I have rarely had to compile finding what I need through the repos.

You can enable the backports repo - which gets more up to date software, but it can break your system.

I think that when you come to upgrade, if thats what you want to do, then 3rd party stuff could potentially be a problem, but not sure.

At the end of the day you can do what you like and if it falls to pieces there will likely be somebody about who could help - if you're going to play like that make sure you have backups - but sometimes it means reinstalling. I reinstalled feisty 3 times in 1 week when I first started :D

---

### Post by Umang on 2008-05-04
Thanks for sorting that out. I'll stick to old versions from the repository!

---

