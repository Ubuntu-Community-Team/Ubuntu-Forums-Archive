---
title: "Strange install issue...possible bug?"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by iamageek on 2008-06-01
I have a Dell Precision 670 with and Adaptec chip built on board.

The first time I tried installing Ubuntu 8.04, I booted off the drive, selected Install and was taken right to Busybox.

Strange I thought. So I broke the hardware raid and tried again.
Same problem.

So for about 2 days I researched the problem and after no progress, I attempted to install CentOS.

YAH! It worked. ok So I know my hardware isn't broken.

Back to Ubuntu.
I booted off the cd, let it boot up to the menu screen, where is asks for a language.

**Now here is the strange part......**

I didn't hit any keys...nothing...I let the timer countdown and walked away.

Sure enough, Ubuntu loaded to the LiveCD. (I was never able to get the live cd to run by actually selecting live cd)

I ran the installer, it saw the adaptec card and the drives, which were all JBOD and it installed.

WOW!

I did go back and try a hardware raid, but the installer didn't recognize the raid. Even though the drives were in a hardware raid0, the installer saw them all as JBOD drives.

So is this a common problem?

Why would Ubuntu not work when I select the Installer from the menu or the Live CD, but work when I let the language selection timer count down and run on it's own.


Thanks!

---

### Post by cmnorton on 2008-06-04
Minimally, I would ask this as a question on Ubuntu Launchpad [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

However, you have documented things well enough here, if this were my problem, I would at least first search for existing bugs in launchpad (the default behavior). You could contribute your experience to an existing bug, or enter a new bug.

Edit:
--------------------------------
There is a "point" release coming out in July, 8.04.1, and I am waiting to try that.

---

