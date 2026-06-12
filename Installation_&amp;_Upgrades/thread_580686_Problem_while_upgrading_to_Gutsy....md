---
title: "Problem while upgrading to Gutsy..."
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by deeps on 2007-10-19
I am currently using Feisty.. I wanted to upgrade it to Gutsy.. I am using UPDATE MANAGER in this perspective... Upgrade is getting halted in the initial phase ("Preparing the Upgrade") itself and I am getting the following error (please find it in the screen-shot)

[IMG]http://www.geocities.com/pradeep_8een/Screenshot.png[/IMG]

I error exactly is "Could not resolve wine.lowvoice.nl"

I do not exactly know what the problem is... I never upgraded in this fashion.. I know that to ensure of a clean install, we gotto install in a clean HD, but, I cant afford to have one since my HD already is almost full (5GB free space)...

Please suggest me something in order to avoid these errors creeping-in and ensure near-cleanest install...

---

### Post by elehayyme on 2007-10-19
I'm guessing this is the same sort of error you got?

> Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg)  Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2)  Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz)  Could not resolve 'wine.lowvoice.nl'


I'm still trying to figure this one out too.  >.<

---

### Post by Arrdee on 2007-10-19
> **elehayyme said:**
> I'm guessing this is the same sort of error you got?



I'm still trying to figure this one out too.  >.<

Comment those sites out in your sources.list file. I had to comment out two or three of my sites before it let the upgrade manager go through.

---

### Post by elehayyme on 2007-10-19
Thanks for the tip! I saw that tip as well in another thread. Lo and behold, it's now updating on my main system.


Again, thank you! :KS

---

