---
title: "Compaq 6910p ... upgrade issues (16.04)"
date: 2016-09-18
forum: Installation &amp; Upgrades
---

### Post by asearle on 2016-09-18
Hallo Everyone,

Some time ago I installed Ubuntu 14.04 on a friend's Compaq 6910p. Recently I recommended that he upgrade to 16.04 but somehow the upgrade has gone wrong.

It sounds like the download was unsuccessful because he tells me that the computer regularly asks if the download/install should be continued. But, strangely, when booting (which takes an eternity) the version is displayed as "16.04".

He also tells me that everything is very slow and that Wireless no longer works.

Does anyone have any advice on fixing a messed-up upgrade?  Either how to go back to 14.04 or how to get 16.04 installed?  Or is a Compaq 6910p too old for 16.04?  (and we should have stayed with 14.04)

Any tips would be a big help.

Regards and thanks,
Alan Searle

---

### Post by mörgæs on 2016-09-19
Let's see the hardware specifications. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by asearle on 2016-09-19
Hallo Mörgaes,

Many thanks for the tip: I'll get the listing as soon as I can.

As it is, I did some "remote support" with the friend and it's not as bad as it sounded: Apparently the main problem is a significantly longer boot-time (I was able to sort out most other issues).

Any ideas on the longer boot-time?

Many thanks,
Alan

---

### Post by mörgæs on 2016-09-20
I myself would never troubleshoot a Buntu which has been upgraded. Maybe other users would and they are of course welcome to post, but I would always suggest a fresh install.

What to install depends on the lshw output.

---

