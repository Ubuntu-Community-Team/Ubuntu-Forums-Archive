---
title: "Re-install of Wubi failing"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by the_silent_one on 2011-02-25
Hi, I was wondering if someone could help me.

I was happily running ubuntu via wubi for a few months on an asus laptop, and then I started getting the no wubildr error, and it would refuse to boot properly into ubuntu.  As I had all my docs backed up ( including the oh so important minecraft savegame ! ) I decided rather than muck around it would be easiest to uninstall it.  

I tried to uninstall via windows, but there was a problem with a .disk file, so ran chkdsk /f on the drive, and uninstall worked fine.

I re-downloaded the wubi installer and downladed the latest 32bit iso from ubuntu.com, and tried to re-install.

Install runs fine until the reboot, once I select ubuntu I get no wubildr error flash up for a second, along with a prompt about an install and then a five second count down.  After the count down hits 0 nothing happens.

I've selected verbose install, and the last few messages are as follows :

```
[ 3.timestamp ] EISA : Probing bus - at eise.0
[ 3.timestamp ] EISA : Cannot allocate resources for mainboard
[ 3.timestamp ] Cannot allocate resource for EISA slot 1
[ 3.timestamp ] Cannot allocate resource for EISA slot 2
[ 3.timestamp ] Cannot allocate resource for EISA slot 3
[ 3.timestamp ] Cannot allocate resource for EISA slot 4
[ 3.timestamp ] Cannot allocate resource for EISA slot 5
[ 3.timestamp ] Cannot allocate resource for EISA slot 6
[ 3.timestamp ] Cannot allocate resource for EISA slot 7
[ 3.timestamp ] Cannot allocate resource for EISA slot 8
[ 3.timestamp ] EISA: Detected 0 cards.
[ 3.timestamp ] cpuidle: using governor ladder
[ 3.timestamp ] cpuidle: using governor menu
[ 3.timestamp ] TCP cubic registered
[ 3.timestamp ] NET: Registed protocol family 10
[ 3.timestamp ] lo: Disabled Privacy Extentsions
[ 3.timestamp ] NET: Registered protocol family 17
[ 3.timestamp ] Using IP No-Shortcut mode
[ 3.timestamp ] PM: Resume disk from failed.
[ 3.timestamp ] registered taskstats version 1
```I am completely stumped at this point :( I have tried everything I can think of but just can't get past this point - I'm wondering if there is an extra file somewhere that was missed in the uninstall? No idea :)  Any help would be awesome.

---

### Post by mörgæs on 2011-02-25
Hi, welcome to the fora.

Try searching in this thread:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

