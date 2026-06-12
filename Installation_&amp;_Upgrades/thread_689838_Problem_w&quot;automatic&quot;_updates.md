---
title: "Problem w/&quot;automatic&quot; updates"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by Thrasonic on 2008-02-06
Hey all,

So I've tried the four versions of Ubuntu that I would want to try:

Live install DVD 32-bit
Live install DVD 64-bit
Alternate install CD 32-bit
Alternate install CD 64-bit

Every single one has installed fine.  However, the first thing I like to do when I boot into the OS for the first time is click that little icon by the clock that has an exclamation point on it (the one that tells you there are updates).  I go through the process to download and install the updates and every time I do the installation process gets about half way through and than I get the following message:

"Could not commit changes - Adept Manager
There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages."

At least the last couple of times it got hung up on the following:

"Preparing to configure new version of libqt3-mt..."

It installs all of the updates to that point and than craps out on me and gives me that error message about not being able to commit changes.  This normally ruins my install, which is one reason I've installed each of those four versions of the OS.  I also swapped out hard drives just to make sure it wasn't the drive or the hardware.  I don't think it is.  I never had this problem with version 6.10.  What do you all think is going on?  I really wanted to give 7.10 a try but I'm beginning to wonder if it just isn't going to work for me.

I have an AMD64 x2, 1 GB RAM, 40 GB IDE HD, 18x DVD-RW, etc.

---

### Post by Rocket2DMn on 2008-02-06
So you're using Kubuntu (with KDE).  Try running the updates from the command line instead, some people have problems with Adept sometimes.
```
sudo apt-get update
sudo apt-get upgrade
```

In what way does it ruin your install?

---

### Post by Thrasonic on 2008-02-06
Hi Rocket and thanks for the quick response.  So that does the exact same thing?  It downloads and installs the updates?  I've had it completely hose my installation.  It would just stop working, and rebooting wouldn't fix it.  Things just wouldn't work, like apps and being able to do things that require administrative rights.  I'll try the method you recommend and see what happens.  If I can't get this worked out I'll just revert back to version 6.

---

### Post by Thrasonic on 2008-02-06
> **Rocket2DMn said:**
> So you're using Kubuntu (with KDE).  Try running the updates from the command line instead, some people have problems with Adept sometimes.
```
sudo apt-get update
sudo apt-get upgrade
```

In what way does it ruin your install?

It seems like that did the trick.  I did this in terminal and had no problems.  Thanks.

---

