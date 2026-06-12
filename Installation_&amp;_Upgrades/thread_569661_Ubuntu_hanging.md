---
title: "Ubuntu hanging"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by Ro_han on 2007-10-07
Hi,

I am having problems with my PC slowing down and then hanging completely.

Usually:
1. Programs slow slightly and GUIs refresh slowly but the mouse still works and basic windowing functionality works, eg. you can alt-tab between windows and drag windows with the mouse.
2. Then eventually it slows down to the point that windows won't refresh and the mouse will no longer move, (or only move horizontally/vertically).
3. Then a few seconds later it hangs.

I was running an old version of Ubuntu 5.10 and had no problems like this. Then I upgraded through repositories found here:
[http://ubuntuforums.org/showthread.php?p=3296274](http://ubuntuforums.org/showthread.php?p=3296274)

Some of these include:
deb [http://bea.cabarel.com/ubuntu/](http://bea.cabarel.com/ubuntu/) breezy main restricted universe multiverse
 deb [http://bea.cabarel.com/ubuntu/](http://bea.cabarel.com/ubuntu/) breezy-updates main restricted universe multiverse
 deb [http://bea.cabarel.com/ubuntu/](http://bea.cabarel.com/ubuntu/) breezy-security main restricted universe multiverse
 deb [http://bea.cabarel.com/ubuntu/](http://bea.cabarel.com/ubuntu/) breezy-backports main restricted universe multiverse
 deb [http://bea.cabarel.com/ubuntu/](http://bea.cabarel.com/ubuntu/) breezy-proposed main restricted universe multiverse
 deb [http://bea.cabarel.com/](http://bea.cabarel.com/) dargo main

After this, the hanging problems begun. Sometimes it will hang after 5 minutes and sometimes after 5 hours. It even hung once when I was only running vim in a terminal.

I attempted to upgrade further to Dapper but unfortunately it hung halfway through the upgrade, leaving my computer in an intermediate state so that X is not configured properly and will not run. (I'm stuck in console at start up).

So I tried Kubuntu 7.04 booting off the live CD. It still crashes inevitably (hopefully after I finish this post though!). I tried to install twice off the CD. On both occassions, my PC crashed at: "15% detecting file systems".

I had it properly partitioned with:
7 gigs for /
1 gig for swap
2 gigs for /tmp
and the rest (20 gig) for left for my original home partition (untouched)
(all logical partitions)

After the failed installations, I can no longer mount my old root, tmp and var from /dev. By that I mean /dev used to have files sda8, sda9, sda7 ... which I could mount but are missing now. It now contains lots of files like ptyr4 and tty51.

Anyway I'm a little worried because I need to finish my thesis so all of this was bad timing, and I'm also worried that I've lost my home partition.

Specs are:
Memory: 247M
Chipset: Intel i845E/G/PE/GE
(no video card)

By the way, is there a good command line application for checking your specs? I don't really know where to look. I grabbed the above from the bios.

Anyway, I've really liked Ubuntu over the years and I won't let this put me off. I hope Ubuntu conquers the world!

-Rohan

---

### Post by Pumalite on 2007-10-07
With that RAM, you need a light desktop: Xubuntu Alternate CD:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by Ro_han on 2007-10-07
Thanks for the advice.

Are you saying that my computer was slowing down due to a lack of ram? It was hanging before I tried the live CD though.
How much ram does Breezy require?

---

### Post by Pumalite on 2007-10-07
Did Breezy run well in your computer before?

---

### Post by Hallvor on 2007-10-08
You should *not* run Breezy. It is no longer supported, so that means no more security patches.

I strongly recommend upgrading to something newer. If you don`t want to buy more ram, try Xubuntu. Regular Ubuntu will be too heavy. It will probably work, but it will be sluggish.

---

### Post by Ro_han on 2007-10-08
> **Pumalite said:**
> Did Breezy run well in your computer before?

Before installing the updates found at the repositories I listed in my first post, Ubuntu was running without a problem.

---

### Post by Ro_han on 2007-10-08
> **Hallvor said:**
> I strongly recommend upgrading to something newer.

The problems occurred when I began upgrading from Breezy. Unfortunately during the upgrade process from Breezy to Dapper my computer hung and the upgrade wasn't completed so my original root partition is out of action and I am booting off a live CD now. (So I can't upgrade)

---

### Post by Pumalite on 2007-10-08
Save data and install Xubuntu.

[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)

---

### Post by Hallvor on 2007-10-09
> **Ro_han said:**
> The problems occurred when I began upgrading from Breezy. Unfortunately during the upgrade process from Breezy to Dapper my computer hung and the upgrade wasn't completed so my original root partition is out of action and I am booting off a live CD now. (So I can't upgrade)

I suggest a clean reinstall and Xubuntu instead of regular Ubuntu, unless you add another 256 MB of RAM.

---

