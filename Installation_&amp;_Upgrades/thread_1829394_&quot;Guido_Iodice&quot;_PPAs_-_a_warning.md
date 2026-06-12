---
title: "&quot;Guido Iodice&quot; PPAs - a warning"
date: 2011-08-20
forum: Installation &amp; Upgrades
---

### Post by recluce on 2011-08-20
You may find several threads where somebody recommends to use one of the Guido Iodice "quasi rolling" PPAs to get your older distribution (Lucid, Maverick - and recently, Natty) modernized with newer packages - without going through the agony of updating or reinstalling.

And actually, the Lucid ppa worked well (mostly), with only minor breakages. However, noticing that there were no updates from that ppa for some time, I now noticed that both the ppas for Lucid and Maverick are now "unmaintained". Obviously, somebody found a more interesting toy and decided to abandon this effort without notice.

[RANT] I do realize that all these projects are run by volunteers that get nothing for their effort. But if you don't want to follow through with a project as big as the quasi-rolling PPAs are, why start in the first place? And if it really gets to be too much (which I can understand!), why start a new one? There is now a "quasi-rolling" PPA for Natty, which is maintained for the time being. [/RANT]

So what happens if you are using one of the abandoned Iodice PPAs? Nothing right away, but you will not get required security updates for the modified packages you have installed. Considering that the end of life for Maverick is still 8 months away - and a whopping 20 months for Lucid, this is quite a problem.

Possible solutions:

1.) Accept the risk, but be aware

2.) Upgrade to a newer release (but be aware of Unity before you do so)

3.) Roll back the changes and live with older software version. If you decide to do so, MAKE A BACKUP first. After that, install "purge-ppa" and purge the Iodice PPA

**In any case, if you don't have a "quasi-rolling" Guido Iodice PPA at this moment, do _not_ install it. You will be left out in the cold!**

---

### Post by recluce on 2011-08-21
Small update: I rolled back my system by using "purge-ppa". While this caused a few warning messages (258 packages to downgrade, a couple to remove, a few to install), the system remained stable after restart with only minor problems (like overwritten settings in policykit) that were easily fixed.

I found the usage of purge-ppa slightly cryptic, you have to present the name of the PPA in exactly the right way - or it will balk. Example to remove the Lucid "quasi rolling" PPA:

```

sudo ppa-purge ppa:guido-iodice/guiodiclucid

```


After the purge, reboot (just in case) and then use: 

```

sudo aptitude update
sudo aptitude safe-upgrade

```

Chances are that more recent versions of packages exist than the ones purge-ppa just rolled back to - these could come from backports or other PPAs. In my case, 112 packages were updated - and the system still remained stable after the next restart. :D

In any case, I repeat: backup your system before you purge the PPA. And yes, you would want to use aptitude instead of apt-get because aptitude is better at resolving conflicts and repairing broken packages during such massive changes.

---

