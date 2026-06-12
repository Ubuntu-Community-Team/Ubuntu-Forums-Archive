---
title: "live cd problem doesnt have /sbin/init"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by gunterhausfrau on 2007-01-02
Sorry if this has been answered, but I have been looking for two days!

I can't even get the live CD to work (yes, I'm lame) I'm new (used unix years ago, and now coming back). 

I'm getting no such file or directory. Seems to be everywhere (I'd include the specifics but I would have to type them in manually, ick) the first occurance appears to be 

cp: unable to open '/root/rar/log/': No such file or directory

then downhill until I get busybox and /bin/sh:can't access tty; job control turned off

argh.

Thanks.
Gunter

update: I tried the disk on another system, and it seemed to work fine. The computer I'm trying to put it on is new, core 2, 2 gig ram, 500g hard drive, intel motherboard, etc. would details help?

second update: downloaded and tried Knoppix, same sort of issue, seems that after the initial access to the CD drive it somehow looses focus? So not specific to Ubuntu, but any help would be appreciated.

---

### Post by gunterhausfrau on 2007-01-06
I never did fix this...
but I was able to install Linux, Fedora, but still it is not MS.

The problem is the Intel motherboard (as far as I can tell). The work around can be found here:

[http://www.blindedbytech.com/2006/11/10/how-to-install-fedora-core-6-on-intel-dg965ss-motherboard/](http://www.blindedbytech.com/2006/11/10/how-to-install-fedora-core-6-on-intel-dg965ss-motherboard/)

clear and it works!

just putting it here for the next guy.

---

