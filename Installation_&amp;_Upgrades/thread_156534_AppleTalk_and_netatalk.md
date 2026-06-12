---
title: "AppleTalk and netatalk"
date: 2006-04-07
forum: Installation &amp; Upgrades
---

### Post by tamray on 2006-04-07
I need to set up a server that supports AppleTalk and can run netatalk. Does the current kernel support this. Are there docs to help with this?

Raymond

---

### Post by linear on 2006-04-08
Maybe [this]("https://wiki.ubuntu.com/AppleTalk"), in the wiki.

---

### Post by tamray on 2006-04-10
That would have been great, but I get:

 root@backup1:/home/admin# apt-get install netatalk
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package netatalk


Does it go by a different name?

---

### Post by linear on 2006-04-10
Check that you have the Universe repository enabled: [AddingRepositoriesCliHowto]("https://wiki.ubuntu.com/AddingRepositoriesCliHowto")

---

### Post by tamray on 2006-04-10
Getting closer. Here is what I am getting now:

root@backup1:/etc/apt# sudo apt-get install netatalk
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  netatalk: Depends: libgssapi1-heimdal (>= 0.6.3) but it is not going to be installed
E: Broken packages

---

### Post by linear on 2006-04-10
OK, I'm guessing now. You may still be missing a repository (breezy-security?).

If all else fails, you could download the libgssapi1-heimdal package here: [http://packages.ubuntu.com/breezy/libs/libgssapi1-heimdal](http://packages.ubuntu.com/breezy/libs/libgssapi1-heimdal)

---

