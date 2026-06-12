---
title: "Freeze at partition stage of install"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by clive littlewood on 2010-04-23
Hi All

I've been running lucid through the Alphas and Beta and decided to do a clean install of the RC.

I get to the partition stage of the install and the system just freezes.

I have tried this on 2 computers with the same results.

As a last resort I have just downloaded and used the alternate install, but this freezes at the partition stage as well !!!!!! :(

Any thoughts would be appreciated.

Clive

---

### Post by ronparent on 2010-04-23
The fault may be on the live CD. Do you get the same behabior trying to use the partitioner in an running linux OS on your computer? Running gparted from the live CD? Or is it only the Ubiquity (install program) partitioner?

---

### Post by ranch hand on 2010-04-23
I would use gparted on the live CD to create the partitions and install with no formatting from the installer.

However, if you have not filed a bug, run that again, the same way until it freezes and file the bug from there with;
```

ubuntu-bug ubiquity

```
Then see if the no partitioning thing will work.  It did when we had this problem in 9.10-testing.

The bug is important as the Final Release ISO will probably be up for testing on Monday so this is a little urgent to get sent in.

---

### Post by clive littlewood on 2010-04-23
Hi

I've just started gparted from my current install and it shows ok.

If i use an live cd (9.10) gparted says that "the kernal cannot read the partitions" then shows the table.

Very strange

Clive

---

### Post by kansasnoob on 2010-04-23
I don't know exactly what all changes were made here but I'm testing a fix for a ubiquity bug that I found back at Beta2 and there was a ubiquity update today:

> 

This bug was fixed in the package ubiquity - 2.2.21

---------------
ubiquity (2.2.21) lucid; urgency=low

  [ Evan Dandrea ]
  * Honor user-setup/force-encrypt-home (LP: #566552).
  * Check for LTS in the release name (LP: #558488).
  * Hide the keyboard query dialog when we encounter an error parsing
    the keymap decision tree (LP: #553087).
  * Fix broken comparisons against boolean debconf values (LP: #567749).
  * Return with the correct state value when a keyboard map is found
    (LP: #553087).
  * Update translations from Launchpad.
  * Automatic update of included source packages: debian-installer-utils
    1.72ubuntu5, partman-auto 89ubuntu7, partman-base 139ubuntu6,
    partman-target 64ubuntu9, tzsetup 1:0.26ubuntu9, user-setup
    1.28ubuntu7.

  [ Colin Watson ]
  * Handle new partman/confirm_nooverwrite question properly (LP: #556373).

  [ Mario Limonciello ]
  * In OEM user config, don't change the last page's button to "Install"
    to avoid confusion.
 -- Evan Dandrea <evand@ubuntu.com> Fri, 23 Apr 2010 09:32:43 +0100


I see it does include some parted updates.

Since there are no new daily builds I'm just testing by clicking on "update this installer".

Edit: I just noticed that they did away with the "update this installer" option so to get the newest ubiquity, casper, and parted updates you have to boot to live desktop and install updates.

I'm tempted to try a persistent live usb.

---

### Post by VMC on 2010-04-23
> **clive littlewood said:**
> I've been running lucid through the Alphas and Beta and decided to do a clean install of the RC.

I get to the partition stage of the install and the system just freezes.

I have tried this on 2 computers with the same results.

As a last resort I have just downloaded and used the alternate install, but this freezes at the partition stage as well Since you used both live-daily and alternate iso's, I doubt the installer is the problem.
 I wonder if you have altered you partitions since you installed from one of the alphas? Or how did you get to Lucid. Upgrade from an earlier release?

---

### Post by clive littlewood on 2010-04-23
hi


```
Since you used both live-daily and alternate iso's, I doubt the installer is the problem.
I wonder if you have altered you partitions since you installed from one of the alphas? Or how did you get to Lucid. Upgrade from an earlier release?
```


I installed Lucid as a clean install from live USB.

Kansasnoob

Thanks for that info, it looks as though there is a parted problem.

Maybe patience and a wait for the final release will be my best option ?

Which is a shame after all the testing !!

Clive

---

### Post by ranch hand on 2010-04-23
I hope that you either filed a bug or joined the one up there.  This is how things get fixed.  Do it.

---

### Post by clive littlewood on 2010-04-23
Hi

Have now tried to install from lucid RC using a USB stick and then updating to todays updates.

Still the same problem !!!!!!

Will wait for the final release.

Ranch Hand:  Will file a bug

Clive

---

