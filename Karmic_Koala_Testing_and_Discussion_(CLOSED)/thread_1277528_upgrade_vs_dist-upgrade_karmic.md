---
title: "upgrade vs dist-upgrade karmic"
date: 2009-09-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by slakkie on 2009-09-28
It is a question I have, been bugging me, so I would like you all to explain.

Why do people keep using dist-upgrade (or full-upgrade when using aptitude) to upgrade karmic packages on a hourly/daily/weekly basis?

I myself limit this to doing only "normal" upgrade (or safe-upgrade) commands. Which tends to breaks less stuff then doing the dist-upgrade because it does not remove package just so it can install another. 

I understand why someone want to do a dist-upgrade when going from release to release (jaunty to karmic for example), but not within the same release.

---

### Post by philinux on 2009-09-28
Check out the man pages.

**dist-upgrade**, 
in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages

dist-upgrade doesn't break things, buggy packages can, but partial updates really can bork your system.

---

### Post by slakkie on 2009-09-28
I've read both manpages (apt-get/aptitude), but that doesn't explain to me why I continuously see comments from people doing dist-upgrades. Or am I so conservative that I don't use it?

---

### Post by philinux on 2009-09-28
Personal choice I guess.

---

### Post by ranch hand on 2009-09-28
I generally do not do a dist-upgrade.

I have done it several times recently because of broken systems.  I have several 9.10 variations and if they break so badly that I can't boot into them, but can get to atext login, I will run a dist-upgrade to make sure that all files are updated.  Sometimes things have broken because files are removed but not replaced right or the files are just not there at all.

I have had to chroot into two of the buggers and dist-upgrade fixed both of those and they were really a mess.  One I had to run dpkg  --configure -a twice to get the upgrades to install.

To sum up - sometimes yu just need the BIG hammer.

---

### Post by FuturePilot on 2009-09-28
See [http://ubuntuforums.org/showthread.php?t=1267282]("http://ubuntuforums.org/showthread.php?t=1267282")

---

### Post by philinux on 2009-09-28
> **ranch hand said:**
> I generally do not do a dist-upgrade.

I have done it several times recently because of broken systems.  I have several 9.10 variations and if they break so badly that I can't boot into them, but can get to atext login, I will run a dist-upgrade to make sure that all files are updated.  Sometimes things have broken because files are removed but not replaced right or the files are just not there at all.

I have had to chroot into two of the buggers and dist-upgrade fixed both of those and they were really a mess.  One I had to run dpkg  --configure -a twice to get the upgrades to install.

To sum up - sometimes yu just need the BIG hammer.

LOl. Also when I said I use dist-upgrade I dont always hit the Y key. Have to use a bit of grey matter now and then.

---

