---
title: "Props to all who can help !"
date: 2006-07-26
forum: Installation &amp; Upgrades
---

### Post by redicqlus on 2006-07-26
Hi there:

Got my dual boot working, and am slowly moving over to ubuntu, but... I am having some trouble with ClamAV and was hopeful someone can help.

1) I seem to have installed 0.88.2 version, and need to update to 0.88.3 but I have no idea how to do so. I got the compressed file of the new version, expanded it into /usr/bin and then compiled it.  I went to do "make install" but it didn't work.  Totally stumped.  No idea what to do.  I'm a linux noob so I'd love a tip or 2.

2) speaking of ClamAV, I am not clear if my daemon is running or not.  I go to the System -> Administration -> services menu, and clamav-daemon is checked.  When I go to System -> Administration -> Boot-Up Manager it shows a  '?' instead of a lightbulb for clamav-daemon.

The drink of the day is lillet.

-red-

---

### Post by cilynx on 2006-07-26
Hey,

ClamAV 0.88.2 comes shipped w/ Ubuntu as a package.  What told you that you need 0.88.3?  If you really need to install 0.88.3, you can get a package for it in the Debian Backports here:

[http://www.backports.org/debian/pool/main/c/clamav/]("http://www.backports.org/debian/pool/main/c/clamav/")

You probably want:

[http://www.backports.org/debian/pool/main/c/clamav/clamav-daemon_0.88.3-0bpo1_i386.deb]("http://www.backports.org/debian/pool/main/c/clamav/clamav-daemon_0.88.3-0bpo1_i386.deb")

Nowthen, to clean up the current situation:

You pulled down the "compressed version" (commonly known as a tarball or source-ball).  I'm assuming that you pulled down clamav-0.88.3.tar.gz or some such from the clamav website?  Generally when you're running a distribution (like Ubuntu), you don't want to do that until you really know what you're doing.  The package management system really does exist for a reason.

You expanded to /usr/bin.  I hate to tell you, but that's no good either.  /usr/bin is where the ready-to-go program binaries go, not the source.  If you pulled down a source-ball, you should expand it in your home dir for safety or in /usr/src if you insist on putting it in the filetree proper.

When you expanded the archive, did it put everything into a nice new folder like /usr/bin/clamav-0.88.3/ or did it crap files all over /usr/bin?  If it put it into a new folder, you can safely delete it, then install the package pointed to above.

Let's see where that gets us, then we'll look at if it's running or not...

Good Luck --

---

### Post by redicqlus on 2006-07-26
OK, thanks for the tidbit.   In the time between your reply and my original post, I've managed to mess up more things, so I'm doing a fresh install of all my OS's and have repartitioned.  I am glad to have recieved your tips though. much appreciated.

---

