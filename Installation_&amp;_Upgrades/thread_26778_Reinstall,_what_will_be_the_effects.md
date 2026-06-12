---
title: "Reinstall, what will be the effects?"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by armeck on 2005-04-13
I am having just a lot of random errors since upgrading.  I think it may be due to some "residual" beta stuff as I was upgrading starting a few weeks ago.

I have two partitions, with /home safe on its own.  I am thinking a fresh reinstall with final may help out.  

To that end, will my configuration files all still be safe.  I mean those for Firefox, thunderbird, etc.  All teh account info and prefs and stuff is kept in the /home directory right?  Am I think correctly here?  So if I reinstall those apps after a clean install, will they pick up right like they were?

---

### Post by Dr Gonzo on 2005-04-13
Yes, you've stumbled onto one of the most convenient things a Linux user can do -- keep /home on a separate partition!

You can even switch distributions that way.  My /home was originally on Slackware, then Gentoo for about a year, then Debian, and now Ubuntu.  Never ran into many problems. :)

---

### Post by skoal on 2005-04-13
1. Assuming you reinstall the exact same (or closely related) versions of said software, your /home/<user>.<application> config files will pick up right where you left off.

2. It's also a good thing to tar/gz up your /etc directory and move it to your /home folder somewhere.  When I have to make any changes in there, after a fresh reinstall I just copy over that etc.tar.gz into /tmp, untar/gunzip it, and diff specific files with the new /etc if I need to.

3. I also like to keep separate /opt and /usr/local partitions (in addition to /home).  If you install any 3rd party software you can't find in these repos there, it's a simple matter of reistablishing some symlinks and menu entries.

/edit Of course, be sure not to select the format option for those specific partitions you wish to keep during the install.

---

### Post by armeck on 2005-04-14
[QUOTE=skoal]1. Assuming you reinstall the exact same (or closely related) versions of said software, your /home/<user>.<application> config files will pick up right where you left off.

2. It's also a good thing to tar/gz up your /etc directory and move it to your /home folder somewhere. When I have to make any changes in there, after a fresh reinstall I just copy over that etc.tar.gz into /tmp, untar/gunzip it, and diff specific files with the new /etc if I need to.

3. I also like to keep separate /opt and /usr/local partitions (in addition to /home). If you install any 3rd party software you can't find in these repos there, it's a simple matter of reistablishing some symlinks and menu entries.

/edit Of course, be sure not to select the format option for those specific partitions you wish to keep during the install.[/QUOTE]

Thanks for the tips, I am downloading the iso right now.

---

