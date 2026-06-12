---
title: "Gnash 0.8.5 or Swfdec 0.8.4 for Jaunty"
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ubu-for on 2009-03-13
Will Gnash 0.8.5 or Swfdec 0.8.4 get into the Jaunty repository, because I can't trust Flash anymore.

[http://www.getgnash.org/](http://www.getgnash.org/)

[http://swfdec.freedesktop.org/wiki/](http://swfdec.freedesktop.org/wiki/)

[http://tips.webdesign10.com/flash-cookies-privacy](http://tips.webdesign10.com/flash-cookies-privacy)

---

### Post by nyarnon on 2009-03-13
So drop it, If you just knew how many customers I have that buy a flashy site and then come to me to revert to decent (x)(ht)ml you wouldn't be thinking of gnash either ;-) Yes I know it's fun to use in aMSN :-)

---

### Post by asimon on 2009-03-13
It's very late in the development cycle and for new upstream versions a [freeze exception](https://wiki.ubuntu.com/FreezeExceptionProcess) needs to be granted.

For gnash there is at least a request at
[https://bugs.launchpad.net/ubuntu/+source/gnash/+bug/338074](https://bugs.launchpad.net/ubuntu/+source/gnash/+bug/338074)

It's possible that the release team will grant an exception but absolutely uncertain.

---

### Post by ubu-for on 2009-03-13
Now I've tried the current Jaunty version of Swfdec. Verison 0.8.2 works great with YouTube but needs much hardware resources.

> **asimon said:**
> It's possible that the release team will grant an exception but absolutely uncertain.

It looks like the Gnash team will release a version for the Jaunty.

[http://www.getgnash.org/packages/snapshots/ubuntu/jaunty/](http://www.getgnash.org/packages/snapshots/ubuntu/jaunty/)

---

### Post by pferraro on 2009-03-13
The latest stable release is already in the official repos.

For those interested in testing swfdec, check out the swfdec team PPA:

deb [http://ppa.launchpad.net/swfdec-team/ppa/ubuntu](http://ppa.launchpad.net/swfdec-team/ppa/ubuntu) jaunty main
(Contains the latest unstable release 0.9.2)

---

### Post by ubu-for on 2009-03-13
> **pferraro said:**
> The latest stable release is already in the official repos.
But the Swfdec website says 0.8.4 is the current stable version and Jaunty uses 0.8.2.

> **pferraro said:**
> For those interested in testing swfdec, check out the swfdec team PPA:

deb [http://ppa.launchpad.net/swfdec-team/ppa/ubuntu](http://ppa.launchpad.net/swfdec-team/ppa/ubuntu) jaunty main
(Contains the latest unstable release 0.9.2)
Thanks!

Do you also have a security ID for Synaptic?

---

### Post by ubu-for on 2009-03-13
> **pferraro said:**
> deb [http://ppa.launchpad.net/swfdec-team/ppa/ubuntu](http://ppa.launchpad.net/swfdec-team/ppa/ubuntu) jaunty main
(Contains the latest unstable release 0.9.2)

Some YouTube videos are mute with Swfdec 0.9.2.

[http://www.youtube.com/watch?v=M_W2Eb0w2ng](http://www.youtube.com/watch?v=M_W2Eb0w2ng)

---

### Post by pferraro on 2009-03-13
> **ubu-for said:**
> But the Swfdec website says 0.8.4 is the current stable version and Jaunty uses 0.8.2.

[http://packages.ubuntu.com/jaunty/libswfdec-0.8-0](http://packages.ubuntu.com/jaunty/libswfdec-0.8-0)

> **ubu-for said:**
> Do you also have a security ID for Synaptic?

gpg --keyserver keyserver.ubuntu.com --recv 34F13038
gpg --export --armor 34F13038 | sudo apt-key add -

---

