---
title: "GDM hang after upgrade to heron"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by kreyszigrocks on 2008-07-06
Hi,

I upgraded via the upgrade manager to Heron and now get a busy cursor when gdm starts (before seeing a login screen).
I did have kdm installed and that was my default display manager, so I tried using kde and that was ok. 
I hate kde though, and I've now removed kde and kdm.
I have removed and purged gdm, ubuntu-desktop (using aptitude). I then tried installing kubuntu-desktop and I have the same problem, although the blank screen behind the busy cursor is pale blue rather than ubuntu orage-brown.
I've also reconfigure xserver-xorg but that didnt help either.
What's even more annoying is that once I get this blank screen with busy cursor I can't crl-alt into any other terminals to look at logs etc.
Your thoughts greatly appreciated.

edit: I should add that unlike other posts i've seen along these lines, i can't get to a desktop via startx from a commandline - I get a grey (monochrome) background.Initially I see the X pointer, then get a warning about running as root (as I've launched from a root prompt via recovery mode) and then see some popups flash up too quick to read anything.

---

### Post by kreyszigrocks on 2008-07-06
As noted in another thread, this was down to my own copy of glibc getting in the way.

---

