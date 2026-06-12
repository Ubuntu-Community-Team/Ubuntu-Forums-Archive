---
title: "Disabled upgrades in Synaptic"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by Angry on 2006-11-10
I have two items listed in synaptic for update (mplayer and libggi2), however both checkboxes are disabled.  One, is this a problem? (probably not)  And two, how can I enable these update options so I can update the appropriate programs.  (or three - do I even need to bother to update?)

Thanks.

---

### Post by bruenig on 2006-11-10
Not familiar with synaptic, love me some command line, but open a terminal and do
```
sudo apt-get update && sudo apt-get upgrade
```
If there truly is something that needs to be upgraded, that will do it for sure.

---

### Post by Angry on 2006-11-10
Hmm, odd.

Ran the command as instructed and this was returned:

The following packages have been kept back:
  libggi2 mplayer
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

Not that this is really a problem for me, its just strange.  If anything, I am just curious *why* they are kept back.

---

