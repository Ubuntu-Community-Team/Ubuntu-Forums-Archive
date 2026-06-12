---
title: "HELP! i want to customise the mini.iso"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by songshu on 2008-05-04
dear all,

not really sure where to put this so i do it here, and first of all a little explanation of my situation.

i have some servers (debian) with 10 to 20 ubuntu clients in a pretty normal office setup. nice and all that ubuntu has this nice live-cd and customizzze it yourself with synaptic thing going on but that goes way beyond the skills, time-schedule and patience of my users. so this calls for some automagic approach that will basically do the following.

install everything i want without asking any questions.
install the packages i want, including some custom made.
authenticate users against LDAP.
mount the /home directories on the server.

the end result would be that the end-user would have to boot from cd - press enter to start the installation routine - remove the cd and press enter again to reboot.

this is not a single specific question, i know, so maybe not really suitable for a forum of this kind, but i definitely need some help on this one to achieve and document so i'm just giving it a shot here hoping it can prevent me from hitting a few walls here and there.


I will document my findings on the link below, for both my own reference and hoping it might ever help someone in the same situation since i find the information available lacking to say the least.
[http://songshu.org/doku/doku.php?id=custom-ubuntu](http://songshu.org/doku/doku.php?id=custom-ubuntu)

what i would like to ask is if people have some good reference, sugestions or even working examples for Hardy concerning
- d-i
- custom packaging and mirroring
- LDAP scheme for location name password homedir
- autofs automounter with CIFS


much obliged

songshu

---

