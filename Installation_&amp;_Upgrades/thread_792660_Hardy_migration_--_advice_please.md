---
title: "Hardy migration -- advice please"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by tamias on 2008-05-13
Hello all,

I upgraded  my Dell Inspiron 6000 laptop from Gutsy to Hardy via the Release Candidate when it was released. Since then I've hit problem after problem -- it is by far the least successful upgrade I've ever performed in three years of using Ubuntu.

I've managed to solve a number of the showstoppers (unreadable text in Firefox, Accessibility tools stealing all keypresses, display manager crashing) in the last month on my own. Unfortunately, despite being a relatively experienced and confident user, there is too much still to fix: DPMS issues on suspend/resume, gnome-panel crashing on startup, fullscreen video using 100% CPU, etc...

To make things worse, the latest round of updates has actually borked things even more. Now the HAL reports a "can't start" error on boot-up, so I've lost power management and networking via network-manager altogether, and have to revert to manually executing dhclient via a cabled connection to get online.

I'm just about ready to give up on Hardy now and revert to Gutsy. My questions are two-fold:

1). How long should I wait until Hardy is at a stage where I could try it again? Or is it considered 'finished' now and there won't be any more significant updates?

2). Is there a definitive guide to installing all the packages, 3rd party software, and configuration currently installed on my laptop, onto a fresh install of Gutsy? My laptop represents three years of extensive personalisation and customisation, and I'm loathe to just "do a Windows" and reinstall everything from scratch.

Many thanks in advance,

Mark

---

### Post by lemming465 on 2008-05-19
> How long should I wait until Hardy is at a stage where I could try it again
July, maybe.  Canonical is going to respin Hardy point releases every few months with accumulated bug fixes.  Their official guidance to 6.06 folks wanting stability was to wait for 8.04.1.  Hardy shipped not quite ready for prime time due to the desire to migrate onto newer technologies such as pulseaudio which had better long term support prospects.  Sorry to hear about your problems; in spite of the teething pains Hardy has been running better for me than Gutsy, so I won't be going back myself.

> Is there a definitive guide to installing all the packages ...
Not that I'm aware of, no.  However, *dpkg --get-selections* on the Hardy system followed by *dpkg --set-selections* might do a lot of what you want.  You'd have to edit the list of packages a little in between, I think.

---

### Post by tamias on 2008-05-20
Thanks very much for this. I'll hold tight until July for now, but if that doesn't solve my issues (or I can't fix them myself in the meantime) then I'll look into the dpkg options on a fresh install of Hardy.

Looks like another case for [https://wiki.ubuntu.com/PainlessUpgrade](https://wiki.ubuntu.com/PainlessUpgrade)  though!

---

### Post by MyR on 2008-05-25
I went back to gusty on my inspiron 6000 although I did not experience nearly as many problems.  It took longer to boot and it crashed twice within the first hour or so.  I just backed up /home reinstalled.

---

