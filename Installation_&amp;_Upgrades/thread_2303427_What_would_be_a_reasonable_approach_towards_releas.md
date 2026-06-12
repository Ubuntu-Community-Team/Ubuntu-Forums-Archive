---
title: "What would be a reasonable approach towards release updates?"
date: 2015-11-18
forum: Installation &amp; Upgrades
---

### Post by igor39 on 2015-11-18
Hi, tried to look for a comprehensive answer but without success...

**Background:** about a year ago I started to use Linux again after almost 7 years of break. Used to use Debian Sid + XFCE so Xubuntu was a natural choice. I am very happy with the overall experience and totally enjoy my "back to old times" experience...

BUT

Recently I did my second release upgrade and it was a second time in a row when it blew my system up the way I had to spend couple of hours brining it back to some usable state. Actually after last upgrade I still strongly consider reinstalling the whole thing completely. Smells like Windows ;-)

**Question:** what could I do to prevent/minimize such events? Wait 2 months before upgrading? I already did wait 2-3 weeks and was not rushing to upgrade straight after release but still run into trouble. Some different approach? I'd probably like much more some kind of a gradual upgrade process. With the all-at-once approach it's much harder to find suspects after a crash. Is such "gradual" procedure available? I know this might sound like a stupid question, but still decided to ask it. :-)

Thank you in advance for all helpful answers!

---

### Post by QIII on 2015-11-18
One of the top culprits in failed upgrades to new releases is the failure to first remove proprietary drivers.  Have you been doing that.

---

### Post by tgalati4 on 2015-11-18
Stick with 14.04 LTS and don't release-upgrade until April 2019

---

### Post by grahammechanical on 2015-11-18
+1 to both of the above but adding

Keep the user interface in a default state or revert it back to the default sate if heavily modified & remove any applications that were downloaded from the web and not part of what Ubuntu Software Centre offers.

---

### Post by ajgreeny on 2015-11-18
Did you upgrade to 15.10, and is your machine using an AMD graphics system and the fglrx driver?

That has been a major problem for upgraders, even though it was a known bug and mentioned in the release notes for 15.10.  You can either look at the work-arounds for this, which I can't find at this moment, or temporarily remove fglrx with ```
sudo apt-get remove fglrx*
``` until the problem is fixed.

I'll keep looking for the details of the workaround for you, and will come back with the info.

---

### Post by ajgreeny on 2015-11-18
Found it.

The work-around for some has been to enable the proposed repositories and install fglrx only from them, then disable proposed again.

See [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888) for the bug and details.

---

### Post by igor39 on 2015-11-20
Thanks for your suggestions. 

So it is quite as I was afraid - I have not missed any silver bullet solution and the only somewhat-reasonable option is sticking to the LTS versions (thanks tgalati4 
).

The "no proprietary drivers" rule was known to me and it was not a problem. I had quite a few others e.g. (Just to give examples! I'm good, the intention of this thread was finding some general solution, not detailed troubleshooting):

- upstart to systemd switch for some, still unknown to me reasons results in a spectacular failure during boot
- random system hangs (after Werewolf)
- my desktop PC won't turn off after entering halt command, need to use power switch again

So if nobody else has my silver bullet - you can close the thread. I'll strongly consider using LTS :/

---

