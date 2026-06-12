---
title: "Coexisting packages and compiled-from-source?"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by itzfritz on 2010-05-20
I have recently installed a dev branch of Postfix on my box (jaunty), in order to access some new features.

This requires that I do not use any of the postfix-related packages in the repos, I have to set this all up manually.

What is the best method for me to manage this system moving forward?  Do I need to prevent the repo's postfix package (or anything depending on it, like postfix-mysql, postfix-dovecot etc.) from ever being installed accidentally?  Is there anything else I need to worry about?

How do you folks generally manage having compiled, customized versions of software that exists in the repos on your systems?

Thanks!

---

### Post by lemming465 on 2010-05-21
First, except for the fact that packages providing major capabilities such as e-mail will keep trying to install on you, the world doesn't come to an end if you have a mixture of managed and unmanaged code.  It helps a lot if you keep you unmanaged code strongly separated from the managed stuff, e.g. don't install the /sbin /bin /lib type directories, stick to /opt, /usr/local, etc.

The best way to deal with replacing packages is to use ... packages.  You can actually make your own.  From scratch, if you have to.  If you do use a custom package, you can use the priority and pin features to prevent the regular system packages from overriding your homebrew stuff.  The easiest ways to get packages tend to be 1) using backports  2) using PPA's  3) using upstream debian packages  4) adapting an existing package to your newer source tree.  Typically you'll want to use the source packages and build your own binary packages in these scenarios.

---

