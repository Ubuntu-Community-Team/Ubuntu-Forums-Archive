---
title: "Apply previous configuration to upgraded distro"
date: 2013-02-20
forum: Installation &amp; Upgrades
---

### Post by samsom63 on 2013-02-20
Hey Folks,

As you know the latest LTS Ubuntu distribution will soon be released, and it is likely I will upgrade from my current 12.10.

I wonder what is the most efficient way to so. I mean, I've got lots of installed apps, each configured to suit my needs and I've also tweaked Unity quite extensively. If there was a way to avoid doing it all over again, I'd really appreciate it!

Now, I regularly back up both my packages list and my configurations files (basically the whole /etc dir), but I am not sure how to use these once I'll install the new distribution.

Any tips as to efficient ways to manage the transition?

---

### Post by dino99 on 2013-02-20
personal data & settings are stored inside your /home partition (if you have made the installation that way of course, otherwise you get a home folder).

So upgrading is not an issue (even with home folder), but a fresh install from scratch, need first you save/backup that home folder (if you dont have a /home partition)

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

---

### Post by samsom63 on 2013-02-20
> **dino99 said:**
> personal data & settings are stored inside your /home partition (if you have made the installation that way of course, otherwise you get a home folder).

So upgrading is not an issue (even with home folder), but a fresh install from scratch, need first you save/backup that home folder (if you dont have a /home partition)

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

Oh, I see, so upgrading the distribution keeps intact the home folder and all the configurations files, that's great.

Just a question though: could it be an issue if some of the previous configs are not supported anymore in the new distro?

---

### Post by zombifier25 on 2013-02-20
Most of the time it will not be a problem, but sometimes some config (such as Compiz configs) will screw up. Fixing them is pretty easy though, and 12.04 and 12.10 is pretty identical to each other so I would be surprised if any problem shows up.

---

### Post by samsom63 on 2013-02-20
That looks excellent, thanks for your answers. Cannot wait to go through my first upgrade now :)

---

### Post by ajgreeny on 2013-02-20
By the way, it sounds as if you think that 13.04 is the next LTS version; it isn't.
The next version to be LTS will be 14.04 in another 14 months.

Sorry if you did know that, but it didn't sound as if you did.

---

### Post by samsom63 on 2013-02-20
> **ajgreeny said:**
> By the way, it sounds as if you think that 13.04 is the next LTS version; it isn't.
The next version to be LTS will be 14.04 in another 14 months.

Sorry if you did know that, but it didn't sound as if you did.

Indeed, I assumed that the next one would be 13.04 and not 14.04. Thanks for the info.

---

