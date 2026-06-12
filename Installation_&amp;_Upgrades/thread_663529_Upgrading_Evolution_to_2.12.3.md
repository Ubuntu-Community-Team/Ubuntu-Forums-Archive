---
title: "Upgrading Evolution to 2.12.3"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by helino on 2008-01-10
I'm running Ubuntu 7.10 and I would like to upgrade Evolution to the latest stable release 2.12.3, how do I do it?

I have enabled the pre-released updates but the only version available is 2.12.1.
Is there any .deb file of 2.12.3 or how do I do it?

---

### Post by spamking2000 on 2008-01-10
Hey Helino - 

Not seeing any .deb's out there which would be the easy way to do it. You can go to their website, download the "tar ball" and compile it, which is easier than it sounds.

[http://www.gnome.org/projects/evolution/download.shtml](http://www.gnome.org/projects/evolution/download.shtml)

There's a link from this page which downloads the tar ball and pretty much you just open it in the archive manager and extract to your machine. Then just drop to a terminal, switch to the directory that you extracted it into and there most likely will be a README file with instructions.

Usually its either a matter of running some ./install-me type app or just doing a make | make install on whats there.

Hope that Helps!

---

### Post by helino on 2008-01-10
Ok, I'll do that if I'm not able to find any .deb:s

Thanks for your help!

---

### Post by Sef on 2008-01-10
Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by alpianon on 2008-02-05
I tried to compile evo 2.13.3 on Gutsy but it's much more complicated than it seems.
First, there are a lot of "-dev" packages you have to install in order to "./configure" it.
Then, after "make", I did "make check" just to be sure before installing, and almost half of the tests failed, so I didn't dare to type "make install"...
Moreover, I tried to create a .deb package with dh_make etc... but with no success (probably I have to modify debian/rules in a way that I can't figure out).

I guess that evolution is too tied to gnome to successfully backport only the app core packages...

---

