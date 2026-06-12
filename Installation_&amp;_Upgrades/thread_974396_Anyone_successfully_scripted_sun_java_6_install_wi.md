---
title: "Anyone successfully scripted sun java 6 install with apt-get?"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by ccharman on 2008-11-07
Hey all --

I'm trying to script installation of the Sun JDK using Capistrano. Since I'm trying to do this non-interactively, I can't accept the license agreement and the install fails.

Is there any way to script acceptance of the license agreement? Yes, I know, {tab}-{enter}, but I'm not doing this in a tty so I can't really do that.

Ideas? Suggestions?

Thanks in advance!

-Chris

---

### Post by jlgoolsbee on 2009-04-24
I am trying to do this as well, except I'm just using a bash script with some simple logging.  Here's what I've got:

> 
echo -n "Installing Sun Java 6... " >> $INSTALLDIR/install.log
sudo apt-get --yes install sun-java6-jdk sun-java6-source && echo "SUCCESS" >> $INSTALLDIR/install.log || echo "FAIL" >> $INSTALLDIR/install.log

The issue is that I need it to accept the license agreement non-interactively, and it doesn't seem that there's a good way to do that.

Any ideas, anybody?

---

### Post by timjdavey on 2009-12-16
Hate to do this but... same thing! Anyone work out how. Would love to know.

---

