---
title: "[SOLVED] firefox lost all preferences"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by cnkbrown on 2008-05-16
Earlier I was using wireshark, and hit a "help" button. Wireshark responded that firefox had an error, and I'd need to restart it. So I did. 

A bit after that I got a notice that firefox had updated, and I needed a restart, so I did. 

Now all my history, bookmarks, etc... are all gone.  Any ideas on how to get them back?

The title bar shows firefox 3 beta 5.

---

### Post by cnkbrown on 2008-05-16
As a follow up, firefox is not capturing browser history. so I can't navigate backward/forward. and I can't get to previous web pages, nor can I capture bookmarks.

If I run firefox as root, everything comes back and works as expected. I expect wireshark, launching firefox, changed ownership on a bunch of files to root.   Now I just have to go find out which ones and change them back.

---

### Post by taurusvip on 2008-09-27
Hi !   I had the same problem with wireshark, I executed sudo wireshark + firefox...   every preferences+favorites gone forever, even the adress bar is always blank :))

I tryed to reinstall with package manager snynaptics but doesn't work, some foldes/files was not removed, permission stuff... how did you fix ?

---

### Post by cnkbrown on 2008-09-30
It's been a while, so I can't recall exactly what I did, but here's the gist of it;

$ cd
$ ls -alR | grep "root[ \t]*root"

this exposed a bunch of files under, I think, .mozilla that had become owned by root.  So, then I chown'ed them to be owned by my user id instead;

$ sudo chown -R myuid:myuid .mozilla

I'm not sure that .mozilla was the only folder affected, so pick through the results of the 'ls' command and change anything that you should own back.

---

