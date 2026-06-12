---
title: "Failed to fetch http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz 404 Not Found"
date: 2006-06-26
forum: Installation &amp; Upgrades
---

### Post by mskogly on 2006-06-26
I'm trying to update to 6.06 lts through the update manager, but I get this error message. Have tried many times but no luck. For some reason there is no Setting-editing possibilities in Update Manager, so I can't add other repositories (if I had them).

Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found

---

### Post by jfl on 2006-06-26
I had the same problem, as well as many other users.
Just edit your [FONT="Georgia"]source.list [/FONT]and remove (or comment ) the 2 or 3 lines that give you a "404"; you'll need to do:
*$ sudo gedit / (your path)/sources.list*

or better yet, download a correct [FONT="Georgia"]sources.list [/FONT] from one of the "sticky posts" on the top of this forum and replace yours with that.

Good luck

---

### Post by jfl on 2006-06-26
Forgot to mention:

I was a lot happier with install from the CD than with the "dist-upgrade".
The upgrade was extremely long to download and the results needed a lot of tweaking.
Then I dowloaded the CD (not the live CD); it reformatted my Linux partitions,
and in an hour or so, it was beautiful.
Just make sure you backup your /home/ directory and any other data you want to keep !!!

---

