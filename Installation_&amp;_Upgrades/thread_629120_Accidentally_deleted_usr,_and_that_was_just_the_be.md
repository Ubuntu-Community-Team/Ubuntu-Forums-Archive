---
title: "Accidentally deleted /usr, and that was just the beginning."
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by Teeg on 2007-12-02
I accidentally unrar'd an otherwise totally safe archive into /usr/share/games/usr/share/games instead of just into /usr/share/games.

In this case, I decided the appropriate response was to pop open a terminal, navigate into /usr/share/games, and then run *sudo rm -r usr*. But I really screwed it up, and threw in a slash by mistake, deleting my entire /usr directory.

So I booted a livecd and copied the livecd's /usr directory onto my hard drive, which should at least get the system runnable--which it did. The base system itself is working just fine now.

The problem? Nothing else is. I know that the appropriate response in this case is to reinstall all of the packages I need through Synaptic, but I'm hitting trouble here insofar as I also need to reinstall all of their dependencies, and researching then reinstalling several dozen of them isn't a task I really relish. Phrased differently, I know I'll need to reinstall vlc player, but I'm not sure off the top of my head which of the thousands of potential packages will also need to be reinstalled as dependencies, and there are about two dozen applications--with full dependencies--that will need that treatment.

Is there a way to have Synaptic check to make sure the packages it thinks are installed and working properly are, in fact, installed and working properly?

If not, would copying the entire filesystem off the livecd be a better strategy? I don't want to reinstall Ubuntu if I can help it, because I've got several large documents that it would be a huge pain to back up or throw in a lifeboat so they don't get squished by a reformatting or deletion.

We're talking 7.10 here, if it factors into it.

---

### Post by monktbd on 2007-12-02
sorting all the packages in synaptic so that all that are/were installed are next to each other, then marking all those and select "mark for reinstallation" from the menu.

in any case i would backup the data. actually i would do that always and often and can easily be made automatic too.
[www.rsnapshot.org](www.rsnapshot.org) e.g.
also if you partitioned your harddisk in a way that /home or whereever your data lies is on a seperate partition a reinstall is pretty painless because you can just point to the old /home or data partition and reuse it without reformatting. again, i would backup before doing that.

---

