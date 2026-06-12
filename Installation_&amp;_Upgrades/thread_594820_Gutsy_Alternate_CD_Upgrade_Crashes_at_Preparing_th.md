---
title: "Gutsy Alternate CD Upgrade Crashes at Preparing the Upgrade Step"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by JoseArmandoJeronymo on 2007-10-28
I downloaded and burnt a Gutsy Alternate CD to upgrade from Dapper however in my main computer the Update Manager seems to crash at the very first stage 'Preparing the Upgrade" on the "Checking the upgrade system" step.

The CD seems to be all right as of now it is way down upgrading my old box from 7.04 to 7.10 which makes me suspect of some setting or application incompatibility problem.

Tks in advance for any ideas.

---

### Post by JoseArmandoJeronymo on 2007-10-29
I have got this line from auth.log:

Oct 29 11:17:06 localhost sudo: prospero : TTY=unknown ; PWD=/tmp/distupgrade.M14038 ; USER=root ; COMMAND=/tmp/distupgrade.M14038/gutsy --cdrom /media/cdrom

/tmp/distupgrade.M14038/gutsy seems to be a pyhon script. Could this be the problem?

---

### Post by Insightfill on 2007-10-30
Sadly, it seems that spaces in the disk name make it difficult to upgrade 7.04 to 7.10 with the alternate CD.  You'll probably see it start over and over again fetching the files, and if you cancel you'll see that there were a ton of "MD5 errors" as though the disk burning didn't catch.

[http://ubuntuforums.org/showthread.php?p=3575562](http://ubuntuforums.org/showthread.php?p=3575562)

You can try the workarounds recommended, do an internet-based upgrade, or upgrade from the Live CD instead.

Took me a while to get this answer, long after I had given up (but right before I decided to reburn the CD!)

---

### Post by Insightfill on 2007-10-30
A little more research, and it appears this guy got it working by mounting the drive differently.  Sigh, and I've got 13 minutes for downloading from the official servers.

[http://ubuntuforums.org/showthread.php?t=580338&highlight=alternate+cd+spaces+upgrade](http://ubuntuforums.org/showthread.php?t=580338&highlight=alternate+cd+spaces+upgrade)

Go down to post #7.

---

### Post by JoseArmandoJeronymo on 2007-12-27
Gee, I totally forgot about this thread. I ended up making an internet based upgrade which worked fine. Just to say thanks for your interest :-)

---

