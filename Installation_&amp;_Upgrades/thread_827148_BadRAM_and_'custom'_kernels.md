---
title: "BadRAM and 'custom' kernels"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by GeoffreyTransom on 2008-06-12
Greetings, all.

We recently bought a second PC (so that The Lovely doesn't need to hog my machine), and discovered during an install of 8.04 that there are some bad bits in the RAM. (It began with a failure to start the install disc, with a BAD EIP Value and a kernel panic... **memtest86** revealed the RAM problem).

I've let the seller know the problem, and a new RAM stick is on its way.

Not being a very patient chap, I was keen to get the new machine ticking over so that The Lovely could do her own thing (and we could avoid this thing of stealing the computer chair when the other goes to the loo).

So I investigated RAM problems, and found two things - first, the ability to install Ubuntu with the **mem=*nnn*MB** (where *nnn* is an integer), and second, **BadRAM**, which enables Linux to be compiled so as to 'ignore' known dud memory addresses.

This second thing was very interesting on its face, and I do intend to have a crack at it if the new RAM is not here by tomorrow (we live in the French countryside, so things relating to stuff more technical than a pointed stick have to happen by post... unless you want to pay ***un prix pharamineux***). 

One thing that prevents me from simply crashing ahead is that the forums seem to be almost entirely silent on the subject. Yes, RAM is cheap nowadays, but as one whose upgrade-baptism was in 1991, increasing an NEC PowerMate IV from 640k of RAM to (GOSH) 1Mb, I am always loath to chuck out things that are still 99.95% functional - particularly if there is a mechanism to retain the part with no attendant loss of functionality.


So - to make a long story even longer - has anybody seen a recent discussion regarding kernel customisation in general, and kernel customisation with BadRAM in particular?  A nice step by step how-to would be just ginchy (I've seen [this thread at help.ubuntu.com/community/BadRAM]("https://help.ubuntu.com/community/BadRAM") and others like it, but something a little newer would be teh awesome to the power of eleventy.


Cheerio



GT
Deepest Darkest Auvergne (but I'm Australian, in case you're wondering why my English is so bad)

---

