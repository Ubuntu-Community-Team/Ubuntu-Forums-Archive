---
title: "Suggestions needed: upgrade to Dapper from Hoary?Is it possible?"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by gabriello on 2006-11-06
Hi everyone,

I'm a very happy user of Ubuntu 5.04 Hoary Hedgehog on my HP Pavillion dv1000 laptop. Everything works fine and I have all the programs I need configured correctly, but I recently discovered that my distribution is not supported anymore, so I decided to move to a newer version of Ubuntu (I also believe that all the efforts of the Ubuntu guys are really worth to try)
On page
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)
I found that I can't upgrade directly to Edgy:
> 
Before you start

You can only upgrade to Edgy from Ubuntu 6.06 ("Dapper Drake").

...so I think I'll have to upgrade to Dapper.

So, here comes my question: how should I upgrade from Hoary? Is it safe or will I find myself with an unusable pc? Is it just as easy as modifying apt.sources or would it be better to install the distribution from scratch deleting the old one?
Has anybody succesfully tried this kind of upgrade before?

Thanks everyone for your help.

G.

---

### Post by mozetti on 2006-11-06
Your best bet is to install a fresh copy of Edgy from CD. If you're dead-set against doing that, then you need to step through the releases one at a time: Hoary*->Breezy->Dapper->Edgy. Your best bet for doing that is probably using the Synaptic GUI -- check out the Edgy upgrade threads, because there's a CLI command that will get it to dist-upgrade for you.

* - I came in at Breezy, and can't remember if it was Hoary-Warty, or vice-versa. Either way, you should dist-upgrade one version at a time.

---

### Post by Sef on 2006-11-06
If you want to upgrade to Dapper, you have two choices:

1) Upgrade to Breezy and then to Dapper

2) Clean install of Dapper. (This one is less likely to have problems, but your settings will disappear.)

Note: If you skip an upgrade then you will likely break your system.  Whatever you decide to do, **back up** your files first.

---

### Post by gabriello on 2006-11-06
Thanks a lot guys,
I'll follow your suggestions, so I'll backup everything on my laptop!

Still don't know wheter I'll chose a clean install or the chain of upgrades, but thanks for having pointed out that a direct upgrade from Hoary to Dapper is NOT possible.

Cheers,
G.

---

