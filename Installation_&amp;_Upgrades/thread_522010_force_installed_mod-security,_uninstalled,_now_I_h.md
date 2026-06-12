---
title: "force installed mod-security, uninstalled, now I have problems"
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by grittyminder on 2007-08-10
Yeah, I force installed the mod-security packages for apache2, which in retrospect was not such a good idea. I removed the packages and now I can't update packages in general. It seems that the problem stems from an issue with the libc6 package (many other packages seem to depend on this package, including apache2), which probably was installed at one time, but now has a status of 'pU', which means that is has been purged and but still exists in "unpacked" form? When I try to reinstall libc6 I get an error stating that I cannot reinstall due to to dependency on tzdata. However, tzdata seems to be "unstable" so I think that I probably should not install it. I don't know my way around dpkg all too well, and I've never been in this situation before, so does anybody have any handy suggestions?

---

### Post by grittyminder on 2007-08-10
wait, I just found the old libc6 packages in /var/cache/apt/archives/ so I'm going to try to reinstall those and see how it goes...

---

### Post by grittyminder on 2007-08-10
That seemed to work. I re-installed libc6 from /var/cache/apt/archives/, which cleared up the dependency issues.  However, now when I try to update packages I get a "connect (111 Connection refused)" error for each of the package repository sites. This is unusual because, I can pretty much copy/paste the repository URL into my browser and access the Release.gpg file with no problems (i.e. which means that the repository server is up, and that the url's that I am using are correct). Maybe something is wrong with apt-get? How do I turn on logging for apt-get anyways? When I examine the aptitude log file at /etc/var/aptitude it is totally blank.

---

### Post by grittyminder on 2007-08-10
Okay, I've now discovered that wget does not work (which is probably why I was having problems downloading from the package repository)...

---

