---
title: "Trouble installing Google Earth"
date: 2013-04-11
forum: Installation &amp; Upgrades
---

### Post by sideburns on 2013-04-11
My sister and I have been trying to install Google Earth on her Ubuntu computer using this set of instructions: [http://linuxforums.org.uk/index.php?topic=10397.0](http://linuxforums.org.uk/index.php?topic=10397.0)  We're using them instead of just downloading and installing the .deb file because this way, she gets updates as well.  Alas, when she tries to do the update, she gets this:

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>

Of course, we didn't try the actual install after that.  Does anybody know what's going on, or how we can get that repo properly installed?

---

### Post by oldos2er on 2013-04-11
See [http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

If I'm not mistaken, when you install Google Earth by downloading and double-clicking the *.deb file, it will set up its repository automatically so you will receive updates.

---

