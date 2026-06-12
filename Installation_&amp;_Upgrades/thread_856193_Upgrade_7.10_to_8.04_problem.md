---
title: "Upgrade 7.10 to 8.04 problem"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by honestaitch on 2008-07-11
Hi,

I started to upgrade from 7.10 to 8.04 last night, and left it running as it said it would take
approx 1.5 hours. When I went back to the PC it was powered off. On restart I am presented with
the old boot manager options (i.e. boot from Ubuntu 7.10, but no 8.04) and I get the logon screen.
However, when I log on I just get a screen with the background colour and nothing else. It seems
that the upgrade has happened (or been partially successful) because the icons displayed during startup
are different to the 7.10 ones.

I can select the recovery manager on rebooting and get as far a having a command prompt from where I can 
issue commands. It's just knowing the right ones to enter :-)

Any ideas what I can do resolve this problem?

---

### Post by Partyboi2 on 2008-07-11
At the terminal try
```
sudo dpkg --configure -a
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by honestaitch on 2008-07-11
Thanks, I'll give that a go this evening (at work at the moment)

---

### Post by honestaitch on 2008-07-11
Excellent, all now working (this post is from my repaired Ubuntu 8.04 PC), although not without some problems ...

I ran dpkg which did loads of updates / installs before failing with "too many errors too continue".
I then rebooted (boot menu now says 8.04 ... promising).
Reran dpkg again and this time it completed successfully.
Rebooted and all now ok.

I haven't run the apt-get commands yet, but I now have a working system again.

Many thanks to PartBoi2.

---

