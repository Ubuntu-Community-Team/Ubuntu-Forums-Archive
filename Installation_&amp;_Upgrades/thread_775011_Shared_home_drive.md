---
title: "Shared /home drive"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by lewisskinner on 2008-04-29
Hi guys.

Possibly an odd question this, but is it possible to install several Linux distros and have them share the same /home partition on disk, or could the settings from one distro interfere with another?

Basically, I have a dual-boot Virista and Ubuntu Hardy, with Hardy having it's own 10GB partition as well as a 170GB ext3 /home partition (shared with Windoze).  However, I've also purposely kept a couple of 10GB partitions empty so I can test other distros.  Would setting these the same /home partition as Hardy ruin some of my Hardy settings?

I do not believe I have to format a /home partition, so that would be a blessing!

---

### Post by Rallg on 2008-04-29
Sure. You can have a /home partition shared by different distros (even if some are amd64 and others are i386). But I advise you to give different user names. That is, don't use "lewis" as username for different distros, or they can over-write in home. You can use lewis, lewis1, lewis2... if you like.

An advantage is that you can more easily preserve what you have in home, if you upgade a distro. But it's not for everyone.

Just be sure that you don't re-format /home when you do a new install, or you will lose what the other distros put there.

If you merely wish to duplicate user setting when you install a new distro, Ubuntu (and some others) allow you to import settings.

---

### Post by lewisskinner on 2008-04-29
OK, great.

So when I install, say, Linux Mint, and it finds my username 'Lewis' for Hardy, I click on it, and enter (say) real name: Lewis Skiiner, username: lewis1

---

### Post by zvacet on 2008-04-30
I´ll not do that,specialy if you want to try no-debian based distro.Puting two different settings in one home can cose trouble.

---

