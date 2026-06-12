---
title: "Virtualbox under 11.10"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by mcpish on 2011-10-18
When I want to install "Virtualbox" under 11.10 I get a bunch of warnings that it's going to remove a ton of stuff on my Ubuntu box and that I won't be able to get future updates for these things.  It wants to remove essentail stuff like "libcurl", "libreoffice", and "ubuntu-desktop".  What's with that?  why is it bound up with all these other programs now?  It wasn't like this in 11.04

How on earth do you get Virtualbox installed in 11.10 without completely destroying the rest of your Ubuntu install?

---

### Post by dhysk on 2011-10-18
did you upgrade from earlier versions.  I'm just wondering if these are older packages and its just trying to get rid of them when the software manager starts.  Anyway, when I did my upgrade those were on the list of deleted packages.  I let it delete them and I've had no problems. 

If you are worried about it though you cold go here down load and install 

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by mcpish on 2011-10-18
even if you get the .deb file directly from the virtulbox servers, it still wants to remove all those programs in order to fix some sort of dependancy issue.  Very strange.  I've narrowed it down a bit to the fact that it seems to be "libcurl" that's causing the issue.  By default, Ubuntu 11.10 doesn't have libcurl installed, but if you "try" to install it from synaptic, synaptic wants to remove a whole bunch of stuff like the "ubuntu desktop".  Something's not setup right with the dependencies and stuff in Ubuntu 11.10

---

### Post by mcpish on 2011-10-18
ahh geez I think I see what my problem might be.

The guide that I use to setup Ubuntu everytime I reinstall it has a bad mistake.  I usually use this guide everytime I have to install a new version of Ubuntu:

[http://ubuntuguide.org/wiki/Ubuntu:Oneiric](http://ubuntuguide.org/wiki/Ubuntu:Oneiric)

But as you can see, even though the author has updated it for 11.10  He neglected to update his "repository" list"  it still refers to a bunch of NATTY repos in the "add extra repositories" section.  That's got to be my problem.  ARGHH!

---

