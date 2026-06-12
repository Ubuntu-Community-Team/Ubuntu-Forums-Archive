---
title: "Help!  How to force apt-get to use the cd (commandline only)"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by Winterhart on 2008-11-05
Sometime between yesterday and today, something's happened to my fonts.  I can't get into X, and xorg.0.log has "Fatal server error: could not open default font 'fixed'.

I'm booted up in recovery mode, root terminal, so I have no internet yet.

**fc-cache -f -v** didn't fix the problem, so my next attempt is to reinstall xfonts-base.  However -- no internet!

**apt-cdrom add** seems to work, but afterwards **apt-get --reinstall install xfonts-base **still looks only for the remote repositories and doesn't seem to realize there's a CD it can pull from!  It just gives the error that it failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xfonts-base/xfonts-base_1.0.0-5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xfonts-base/xfonts-base_1.0.0-5_all.deb)  Could not resolve 'us.archive.ubuntu.com'.  Which, needless to say, is less than helpful.

How do I make apt-get *actually* look for the CD, since **apt-cdrom add **by itself doesn't seem to be doing the trick?

Thanks!

---

