---
title: "Ubuntu Feisty: Eclipse just stopped working and now has weird errors"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by Skeletor on 2007-09-30
Background:
I've been using Eclipse 3.22 on Ubunt Feisty for several months for Ruby on Rails development and it was working perfectly.  I tried to upgrade my Eclipse plugins to include the PERL EPIC plugin and I also installed the Eclipse 3.22 patches from the Eclipse update site.  I did all of the Eclipse updates though the Eclipse update menu.

Problem:
Eclipse had an error while updating because it could not fully install the 3.22 Eclipse patches.  Now Eclipse is "messed up".  I cannot start Web servers or edit .rhtml files when in Rails mode.  Also, whenever Eclipse starts up it is running some backgorund task "Search index Job", this background task takes forever and runs every time I start Eclipse.

My Attempts to fix the problem:
I tried uninstalling Eclipse and reinstalling it through Synaptic, but after I did all of this all of the Eclipse plugins are still there and everything is still not working.  I had been using generic Java, but after I started having all of the problems I download Sun's Java 6 and made it my system default and the Eclipse default. Now Eclipse is running even worse, it crashes with out of memory errors.

Help:
1) Anyone have the same problem (or know what is wrong) and how I can fix it?

2) Failing an answer to "1", how do I completely wipe out my Eclipse installation (including all of the plugins)?  I'm hoping that if I start from scratch I can freshly install Eclipse and all of its plugins and have everything working as I did originally.

---

### Post by fvbakel on 2007-10-01
Hi,

I had a different problem with starting Eclipse in Ubuntu 7.04. My problem was different but it also reoccurred after the fresh install. After a while I was able to fix the problem with the following steps:

1. removed eclipse
sudu apt-get remove eclipse

2. remove the unused libs

sudo apt-get autoremove

3. after the remove I had to remove some files and directories manually that were not removed by the apt-get command. These were:

/usr/lib/eclipse
$HOME/.eclipse

4. I reinstalled eclipse:
apt-get install eclipse

And then it was working for me!

I hope that this scenario will help you too.

---

### Post by Skeletor on 2007-10-01
Thanks for the advice, that did the trick with completely removing it from my system.  Instead of using the Ubuntu repository version I downloaded Easy Eclipse from:
[http://easyeclipse.org/site/distributions/lamp.html](http://easyeclipse.org/site/distributions/lamp.html)
I just unzipped it into my home/bin directory and it works really well.  No problems with it so far and it already has the RoR~s plugins I need.  Thanks for the feedback!

---

