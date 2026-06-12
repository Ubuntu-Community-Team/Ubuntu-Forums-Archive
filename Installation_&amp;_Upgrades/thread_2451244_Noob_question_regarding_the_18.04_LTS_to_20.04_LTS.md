---
title: "Noob question regarding the 18.04 LTS to 20.04 LTS upgrade."
date: 2020-09-29
forum: Installation &amp; Upgrades
---

### Post by koollaydtac on 2020-09-29
Hey mates. I got a pop up message regarding a 18.04 LTS to 20.04 LTS upgrade today when I logged in. If I take the upgrade does it wipe the pc and install the OS fresh or is it an actual upgrade and will everything I customized and installed be left alone? Also how much free space do I need to clear for this upgrade? I always assumed I had to download a newer distro separately if I wanted to upgrade the distro itself and it was a clean install. I don't want to have to redo everything all over again so I am wondering if I am better off staying at 18.04 LTS or if it is safe to upgrade it or not basically. Thanks in advance. :)

---

### Post by CatKiller on 2020-09-29
It's the same as your normal regular upgrades, but it's upgrading every single package that you've got installed all at once.

A fresh install and restoring your data from a backup is likely (quite a lot) quicker, and some people prefer to do it that way anyway. The more you've diverged from a default install (and so, really, the more you'd *want* to upgrade-in-place rather than doing it all again) the more potential points of failure there are.

You don't have to upgrade straight away. 18.04 is supported till 2023 (2021 for the flavours) so you've got plenty of time to work up to it.

---

### Post by deadflowr on 2020-09-29
A release upgrade, when it works, upgrades all the install packages on the system.
It won't wipe and install fresh, but...
There are no guarantees that all setting will still be intact,
as new versions packages for various pieces of software may require resetting or setting up new customizations.
(It may also remove packages that are now deprecated within the Ubuntu ecosystem)
> Also how much free space do I need to clear for this upgrade?
It will tell you how much space is required, if you take the upgrade ride.
>  I am wondering if I am better off staying at 18.04 LTS 

If you want to, you have plenty of time to upgrade. There are about 3 years worth of time.
(well, 2 and a half years)

18.04 is a long term release so why not keep it going.
I'm on 18.04 as my main system and have no plans to upgrade it anytime soon.

---

### Post by Impavidus on 2020-09-30
> **koollaydtac said:**
> Hey mates. I got a pop up message regarding a 18.04 LTS to 20.04 LTS upgrade today when I logged in. If I take the upgrade does it wipe the pc and install the OS fresh or is it an actual upgrade ...
It is an actual upgrade. Just like your normal upgrades, except that it will upgrade all packages at the same time and the new packages will not only contain bugfixes, but will be new releases of the software. Keep in mind though that release upgrades sometimes end in failure, and then you'll have to do a fresh install anyway. So make sure you've got a live disk at hand and backups of all your valuable data.
> ... and will everything I customized and installed be left alone?
It will be left alone, for as far as still supported on the new release. Some software has been removed from Ubuntu, some settings will no longer work.
> Also how much free space do I need to clear for this upgrade?
Just as much as is needed for temporary storage of files. About 3GB should do, but it will tell you how much exactly. For best performance it's best to keep some space unused at all times.
> I always assumed I had to download a newer distro separately if I wanted to upgrade the distro itself and it was a clean install. I don't want to have to redo everything all over again so I am wondering if I am better off staying at 18.04 LTS or if it is safe to upgrade it or not basically. Thanks in advance. :)
Upgrades are safe if you take some precautions, but fresh installs are cleaner and more reliable. I usually do 3 upgrades in a row, every 6 months, then a fresh install.

---

### Post by mrdc76 on 2020-09-30
In my past 20 years of using Linux, I don't remember a time when (1) a distribution upgrade failed or (2) a clean install fixed a problem in the upgrade for me. That said, I don't use PPAs or heavily modify my OS by running random scripts from the internet.

---

### Post by Impavidus on 2020-09-30
> **mrdc76 said:**
> In my past 20 years of using Linux, I don't remember a time when (1) a distribution upgrade failed or (2) a clean install fixed a problem in the upgrade for me. That said, I don't use PPAs or heavily modify my OS by running random scripts from the internet.

Neither have I in 14 years using Ubuntu, and yet the forum if full of such stories. It must have to do with some people installing random stuff from the internet like chocolate bars. The only thing that ever goes wrong here is that sometimes I see that some home-written software no longer works and must be ported to a later version of whatever it depends on. And a fresh install is a great way to get rid of cruft that's not properly cleaned during release upgrades. I always find fresh installs to be good for boot time.

---

### Post by rsteinmetz70112 on 2020-09-30
I normally do release upgrades on my systems (a total of 8) since they are mostly servers and have some settings, configuration and databases that would be lost in a new install. I think my oldest one started out with 6.04 and has had the hardware incrementally replaced at least 3 times. I have one that's still 32 bit so I'm going to have to reinstall that one - I have tried to change the architecture of a test computer a couple of time without success. I don't use PPAs or much third party software, but there is some. I usually have a few problems which I have to work to repair. When I upgraded to 18.04 I posted a thread on the issues and most of the fixes. I've never had one completely fail nor one I couldn't fix. I have 3 desktops I keep for my use and to try new software I plan to try to upgrade one soon. The biggest ongoing problem is that I usually install Ubuntu Desktop for administration and that has resulted in a lot of left over display managers and gnome versions which are difficult to remove, without possible breaking things.

---

