---
title: "Upgrade broke my LIRC (Solved)"
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by picbits on 2011-03-14
I run a little Revo R3600 for my frontend / media player and have a homebuilt IR receiver connected up to the soundcard input. The whole lot is controlled by an old Sky+ remote.

Yesterday I gave into the constant update manager nag to update the system and downloaded/updated the Revo. I was using remote desktop so didn't notice the LIRC had stopped working until I booted it into MythFrontend this morning.

IRW didn't work so I did a pgrep lirc - nothing
/etc/init.d/lirc start - nothing (blank - no answer)
Checked the syslog - nothing - no mention of lirc
apt-get install lirc - already installed

Then I checked in my /etc/lirc directory. Yesterday, there were a number of changes to the files going by the date stamps. Turns out whatever had updated had renamed my hardware.conf to hardware.conf.old and put a nice blank hardware.conf in its place.

It had also renamed lircd.conf to lircd.conf.dpkg-old and put a generic blank lircd.conf in its place.

Removing the two .conf files and renaming the two backup  files back to their original filenames then restarting LIRC solved the problem but there was a good 10 minutes of headscratching going on :P

Posting this in case anyone else has the same problems - fingers crossed it will save them having to work it out all over again.
Dom

---

