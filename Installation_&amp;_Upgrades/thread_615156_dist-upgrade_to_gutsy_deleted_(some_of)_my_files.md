---
title: "dist-upgrade to gutsy deleted (some of) my files"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by rsc on 2007-11-16
I just upgraded my Xubuntu box from Feisty to Gutsy.  I did this by replacing /etc/apt/sources.list and then running apt-get dist-upgrade.

After rebooting, my login script failed because it couldn't find a file I keep in /home/rsc/lib/.  I investigated to find that every file in that directory was gone.  The subdirectories were okay and still populated.  During the reboot, fsck ran, so I was willing to chalk it up to fsck screwing something up -- not unheard of.

Luckily I have live backups via unison, so I ran unison to see if anything else was gone.  Unison noticed that almost every one of my CVS directories got deleted too!  Not CVS roots or checkouts, but every single CVS/ metadata directory (the ones that contain Root, Entries, etc.).  Five CVS directories were spared, out of 2772.  Those five all had spaces in the paths (e.g., /home/rsc/pub/python/dist/src/Mac/IDE scripts/CVS/).

Also gone is the one file I had in the /home/rsc/man tree, named /home/rsc/man/man1/brandps.1.  The man1 directory was not removed, though.

In summary, apt-get dist-upgrade to Gutsy:

  - installed all the new packages fine
  - removed /home/rsc/lib/* but not the subdirectories
  - removed /home/rsc/man/*/*
  - removed every directory named CVS except those with spaces in the path

It sure sounds like some package was trying to clean up after itself and failed miserably.  Has anyone else run across this?  It seems like something that should be tracked down.

I posted the output of "dpkg -l" on my system at [http://swtch.com/~rsc/dpkg.list](http://swtch.com/~rsc/dpkg.list) .

I grepped for CVS in /var/lib/dpkg/info and in the results of dpkg -e on every deb in /var/cache/apt/archives/ and didn't find any promising leads.

---

