---
title: "Is an Almost-Clean Install Possible?"
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by thinkalone on 2008-04-01
hi there,

this is my first forum post, and hopefully the answer to this will be quick-and-easy, but i haven't been able to find anything useful by searching.

i'm wondering about updating only the "system" part of Ubuntu without backing up and doing a clean install.  i'm using Feisty now, but i started with Breezy and i've had to hack things together along the way (having to custom-edit xorg.conf every upgrade, solving ndiswrapper headaches, manually mounting usb drives, and doing all kinds of crazy stuff to get Compiz working before there was a Beryl).  i'd like to an almost-clean install of Hardy and hopefully let it autodetect the best settings for my computer so that things will 'Just Work' instead of relying on my home-brew solutions.  the answer might be to just backup and re-install my home directory, but i haven't found a clear answer on how to preserve program settings in addition to personal files.

ok, so i hope that makes sense.  thanks to ubuntuforums for helping me solve lots of other problems over the years!

---

### Post by Pumalite on 2008-04-01
If you have a separate /home partition, I see no problems.

---

### Post by thinkalone on 2008-04-01
> **Pumalite said:**
> If you have a separate /home partition, I see no problems.

sadly i don't, this was my first install of Linux and i didn't know enough to put /home in a separate partition

---

### Post by Pumalite on 2008-04-01
Then the best you can do is save /home, do clean install and then restore /home.

---

### Post by thinkalone on 2008-04-01
sounds good, thanks for the confirmation.  my only plan was to tarball most of my system to an external drive, then do a clean install and see what broke and what didn't.  i'll be sure to put /home in its own partition this time!

---

### Post by Pumalite on 2008-04-01
Good luck.

---

