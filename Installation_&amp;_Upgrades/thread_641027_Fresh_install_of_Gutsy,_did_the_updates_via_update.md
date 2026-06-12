---
title: "Fresh install of Gutsy, did the updates via update manager.  Firefox won't start."
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by Mysticle31 on 2007-12-14
So on a fresh install of Gutsy.  I decide to do the updates form the update manager.

Firefox won't start.  I can't find any information about the problem.  I tried to run firefox in the terminal and it says 

"bus error (core dumped)"

What's the deal?  How do I fix it?

I had no problems with firefox on my un-updated installations of ubuntu.  If I have to, I supose I could just reformat and not update.  I'm getting tired of making these little 'if I have to' reasons for the problems I experience in linux.

---

### Post by kool_kat_os on 2007-12-14
Did you try reinstalling firefox?

---

### Post by lbthrice on 2007-12-14
Did you try going into Synaptic, searching for mozilla-firefox and then selecting it for re-installation?  This may be a logical place to start.

Believe it or not...I think that this is one of the advantages of Linux...you will learn more about your OS by troubleshooting this type of issues.
:guitar:

---

### Post by Mysticle31 on 2007-12-14
Yep, that was one of the first things I did.

Don't get me wrong, I like troubleshooting things.  Sometimes I feel though like I've gone backwards instead of forwards.

Is there a reinstall for apt-get?  I've come to like using the command line.  I would like to embed one in my desktop.  Or essencially make my desktop one big transparent command line with a background image.  Someday.... :)  Basically I would right click on the desktop to get my programs menu, type on the desktop for the command line, and have a background picture!  Someday, someday.  I've got right click down though :P

---

### Post by mdlueck on 2007-12-28
I have just been fighting with a fresh install of 7.10 Gutsy Gibbon and Firefox doing some strange "Bus error (core dumped)" things. I went as far as reinstalling a couple of times.

Clean install of 7.10 and no updates, FF will start. Download the updates, FF no longer starts.

The solution to these problems was to go into Synaptic and marking:
firefox
firefox-gnome-support
ubufox

all for re-installation. Once that was done, FF came right up.

---

### Post by gfca on 2008-01-04
> The solution to these problems was to go into Synaptic and marking:
 firefox
 firefox-gnome-support
 ubufox


This fix my gutsy! ;)
thanks a lot

---

### Post by mdlueck on 2008-01-04
Sorry, I did not follow up in this thread.

Many people has reported such trouble, and like us most seem to be running with xfs as their file system.

Heikki Lindholm reported that switching kernels solved the troubles in his case. Therefore I suspect we are dealing with a kernel bug of some sort, which seems only to show up when using xfs. I opened a bug report specifically about xfs here:

[https://bugs.launchpad.net/ubuntu/+bug/179238](https://bugs.launchpad.net/ubuntu/+bug/179238)

---

