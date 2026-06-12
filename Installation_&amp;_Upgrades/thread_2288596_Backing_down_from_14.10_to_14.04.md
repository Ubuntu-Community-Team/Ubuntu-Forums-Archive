---
title: "Backing down from 14.10 to 14.04"
date: 2015-07-28
forum: Installation &amp; Upgrades
---

### Post by pwabrahams on 2015-07-28
I made the mistake of installing 14.10 rather than 14.04, figuring that it was more current.  But now support for 14.10 has ended, so I want to move back to 14.04 since it's supported until 2019. I don't want to go to 15 because for me the inability to have different wallpapers on different desktops is a killer.  (Maybe they'll fix that by 1919.)

At the same time I don't want to lose my 14.10 customizations, since it takes me some time to install them.  I assume that I can achieve that by copying various dotfiles from the old (14.10) installation to the new (14.04) installation.  But which ones?  I suppose I could copy them all, but I would expect to encounter a lot of problems if I did that.

---

### Post by dino99 on 2015-07-28
The 14.x.x are more buggy than the recent versions; so go ahead & forget about the LTS marketing flood (downgrade here means fresh reinstall)

---

### Post by Bucky Ball on 2015-07-28
> **dino99 said:**
> The 14.x.x are more buggy than the recent versions; so go ahead & forget about the LTS marketing flood (downgrade here means fresh reinstall)

No idea what this means, looks like FUD to me, but yes, you will need a clean install of 14.04 LTS. There is no going back via a in-box downgrade. 

Be aware, dino99, that not everyone wants to upgrade every six months and the OP has specifically asked how to go back to an LTS release and retain their current settings. :)

There are ways of saving and restoring your settings from one install to the other, but never done that so not sure. Also not sure if all 14.10 user settings/customisations would work in 14.04.

PS: [THIS]("http://askubuntu.com/questions/25633/how-to-migrate-user-settings-and-data-to-new-machine") might get you started. Good luck. :)

---

### Post by monkeybrain20122 on 2015-07-28
> **Bucky Ball said:**
> No idea what this means, looks like FUD to me, but yes, you will need a clean install of 14.04 LTS. There is no going back via a in-box downgrade. 

Be aware, dino99, that not everyone wants to upgrade every six months and the OP has specifically asked how to go back to an LTS release and retain their current settings. :)

There are ways of saving and restoring your settings from one install to the other, but never done that so not sure. Also not sure if all 14.10 user settings/customisations would work in 14.04.

PS: [THIS]("http://askubuntu.com/questions/25633/how-to-migrate-user-settings-and-data-to-new-machine") might get you started. Good luck. :)

Just want to note that the latest kernel upgrade apparently busted 14.04 at least for some people 
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1478844](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1478844)

While it is true that theoretically 14.04 is supported til 2019 but it seems that LTS support kind of deteriorates after a while and regular system updates become more problematic as time goes on (even if you don't mind outdated user software), you can read those threads where people borked their systems with regular updates for old LTSs like 12.04 and 10.04 after a few years. Not sure if it is because of the point releases with hardware enablement (since 12.04) or simply because Canonical's manpower has gone to newer releases, U + 1 and mobile instead of maintaining the LTSes. 

P.S. Non LTS's is supported for 9 months, not 6. One is not obliged to upgrade (that means fresh install for me) whenever Canonical has a new Ubuntu release, typically I wait for a month for post release bug fixes.


Edited: I don't use kubuntu but apparently kde5 is kind of buggy and one regular kubuntu user on UF said "it is definitely not for prime time" so may be in this instance it is better to fall back to 14.04. If encounter kernel problem just upgrade to the latest (4.1.x) from mainline [https://www.google.com/search?client=ubuntu&channel=fs&q=mainline&ie=utf-8&oe=utf-8#channel=fs&q=mainlinekernel](https://www.google.com/search?client=ubuntu&channel=fs&q=mainline&ie=utf-8&oe=utf-8#channel=fs&q=mainlinekernel)

---

### Post by Bucky Ball on 2015-07-28
I am well aware interim releases are nine months. If you wait nine you will be running an EOL install. Thanks. :)

I only run LTS releases (and test others) and have been 'bonked' by neither 10.04 or 12.04 or 14.04 (or 8.04 for that matter). Must have had the right hardware or just been lucky ...

Carry on ...

---

### Post by QIII on 2015-07-28
I have a 12.04 home server, a 14.04 web server and my primary machine is 14.04.  I have had exactly zero problems with any of them.

I also have a 15.04 machine that works flawlessly.

Remember that Canonical makes its money on service contracts, not sales.  Most who pay the big bucks on service are likely to be LTS users.  They don't want to reinstall all the time.  Canonical has a great deal of vested interest in supporting the LTS versions.  The interim versions are a form of R&D -- less stable.

So let's not find a bit of information here and there and leap to the conclusion that things are falling apart.

---

### Post by howefield on 2015-07-29
> **pwabrahams said:**
> At the same time I don't want to lose my 14.10 customizations, since it takes me some time to install them.  I assume that I can achieve that by copying various dotfiles from the old (14.10) installation to the new (14.04) installation.  But which ones?  I suppose I could copy them all, but I would expect to encounter a lot of problems if I did that.

You could copy your /home folder to a flash disk or whatever and then selectively copy back what you want, perhaps listing the applications that you want to preserve would give us an idea on what to advise.

Fwiw, I use a separate partition as a "data store" for the settings I want to preserve between installs or even sharing between the various installs on the one machine, eg firefox, thunderbird, chromium, kaffeine and others. Eg, ~/.kde is symlinked to /Data/.kde meaning I just have to install kaffeine, create the symlink and no other configuration is needed.       

> **Bucky Ball said:**
> No idea what this means, looks like FUD to me, but yes, you will need a clean install of 14.04 LTS. There is no going back via a in-box downgrade. 

Different strokes for different folks, I guess :) 

All I'll say is 14.04.x is the first LTS I have dropped from my machines within the first year of release. Every LTS before that was superb but for me. 14.04 is a dog.

---

