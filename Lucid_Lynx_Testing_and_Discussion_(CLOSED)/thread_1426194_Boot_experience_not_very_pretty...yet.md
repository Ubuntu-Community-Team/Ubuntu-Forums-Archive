---
title: "Boot experience not very pretty...yet"
date: 2010-03-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Anduu on 2010-03-10
Hopefully they will get some of these boot glitches ironed out.

[LIST]
[*]Booting with ureadahead is hit and miss for me.It seems whenever a new kernel comes down the pipe I have to chroot into my install and remove it before GDM will come up.I can then usually reinstall ureadahead and it works fine.

[*]Plymouth seems to quit a bit too early.I still see text for a couple of seconds between the time the boot logo disappears and GDM starts.

[*]Plymouth is still exiting and letting GDM fire up while disk checks are in progress which will lead to the desktop completely barfing if an attempt to login is made.

[*]Finally...the really annoying one...From the time GDM kicks in until I get to a usable desktop the screen of my secondary monitor flashes continuously.I counted last boot.It flashed forty-four times.That's 44 flashes...glad I'm not epileptic.
It isn't switching modes or going in and out of standby as is doesn't make the tell tale clicking sounds so it isn't likely to damage anything but dang it is driving me nuts.
[/LIST]

With Beta1 coming in just over a week it would be nice to see things cleaned up a bit ;)

---

### Post by yelo3 on 2010-03-10
I also find that plymouth starts very late. after almosta 10 seconds after grub.
Is it the same for you?

---

### Post by Giwex on 2010-03-10
I had plymouth working (more or less) on my Alpha2 regularly upgraded. Few days ago I made a fresh install of alpha3 and I don't have it any longer (only verbose mode up to the GDM)

---

### Post by nperry on 2010-03-10
Very nice rant, now please look on launchpad to see if there is any bugs been filed for these problems, If there is please put any supporting logs/conf files there. If there isn't please make one. 

As everyone else seems to be saying, Developers don't read the forums.

---

### Post by teh603 on 2010-03-10
> **nperry said:**
> Very nice rant, now please look on launchpad to see if there is any bugs been filed for these problems, If there is please put any supporting logs/conf files there. If there isn't please make one. 

As everyone else seems to be saying, Developers don't read the forums.

You mean this?

[https://bugs.launchpad.net/ubuntu/+bug/535671](https://bugs.launchpad.net/ubuntu/+bug/535671)

---

### Post by cyberkilla on 2010-03-10
> **yelo3 said:**
> I also find that plymouth starts very late. after almosta 10 seconds after grub.
Is it the same for you?

I get this too. It starts after 10 seconds, displays for a few seconds itself, then GDM appears (before Plymouth's progress bar reaches 100%).

I get console messages on shutdown and boot too. Not a lot - roughly 5 lines, related to a dodgy webcam driver and two fsck messages (one for each partition).

> **teh603 said:**
> You mean this?

[https://bugs.launchpad.net/ubuntu/+bug/535671](https://bugs.launchpad.net/ubuntu/+bug/535671)

Hate to burst your bubble, but we're testing Lucid Lynx:P It makes no difference to us alpha-testing complainants whether Karmic's boot process changes:D

j/k

---

### Post by Anduu on 2010-03-10
> **nperry said:**
> Very nice rant, now please look on launchpad to see if there is any bugs been filed for these problems, If there is please put any supporting logs/conf files there. If there isn't please make one. 

As everyone else seems to be saying, Developers don't read the forums.

Very nice lecture.Now please give me some credit.I have been around long enough to know how things work around here.

My problems with Plymouth and ureadahead are know bugs and as for my problem with the screen flashing I haven't been able to track down the issue yet.There are no errors being generated that I can find that seem relevant.Who is the culprit...GDM,xorg or some weird Plymouth side effect?

The whole point of the development forum is to get our ideas/issues out there.Get input/suggestions from other users and perhaps fine solutions on own.

---

