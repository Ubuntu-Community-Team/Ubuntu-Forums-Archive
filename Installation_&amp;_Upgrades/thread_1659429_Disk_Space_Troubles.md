---
title: "Disk Space Troubles"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by kazagha on 2011-01-04
I have got myself into a bit of a jam and was wondering if I could get a few pointers on getting out. 

df -h
[http://pastebin.com/XAYdT4HU](http://pastebin.com/XAYdT4HU)

I did the following command to find everything is in /usr or /var, then tracked it down to /usr/lib and /usr/share as the main offenders, but out of all the directories none are more than 1mb or so. 

du -sh /* | sort -gr | head -n 5

I tried to uninstall firefox, which is what got me in this mess in the first place, the log claims it will remove ~240 mb but failes on a "E: Write error - write (28 No space left on device)"

[http://pastebin.com/TPQYcJ9D](http://pastebin.com/TPQYcJ9D)

If I could juggle something onto an external hard drive so I can uninstall firefox I would be out of the wood. Failing that I believe a new install is in order. 

Kind Regards, 
Kazagha

---

### Post by kazagha on 2011-01-06
I ended up rebuilding.

---

