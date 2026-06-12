---
title: "karmic updates"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by vttay03 on 2009-10-06
Hi all-

I am having some problem running updates in Karmic.  The first strange thing I noticed was that I hadn't gotten any updates and I first installed the beta version 3 or 4 days ago.  So tonight I went to update manager to see if any updates were available.  When I did that, I got a message I have never seen before (although this is the first time I've used a beta version so I wasn't surprised); it said "Not all updates can be installed - run a partial upgrade, to install as many updates as possible."  I thought this was peculiar since the word "upgrade" was used and I didn't understand why there'd be any need for an upgrade.  The other thing that happens is when I actually go ahead and click "Install Updates" it downloads a portion of the update but can't seem to get the remaing 26 MB or so, just comes back with "failed to download package files check internet connection."  Anyone else running into this or have insight into the situation?

---

### Post by cariboo on 2009-10-06
While we are in testing, you should never do a partial-upgrade, important packages may be removed. 

If you really need an upgrade, and are offered a partial, open a terminal and use:

```
sudo aptitude safe-upgrade
```

This will only install packages, with out uninstalling important others.

---

### Post by emarkay on 2009-10-06
FWIW, I've been asking for a "Sticky" post here to warn about this for a few days now...

---

