---
title: "GUTSY UPGRADE PROBLEMS... Pls HELP !!!"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by deepjaju on 2007-12-05
I just recently got the Ubuntu 7.10 cd.. But when I try to upgrade it from my previous Ubuntu 7.04 it doesn't detect. I did all the necessary updates for 7.04 via the internet and I got the option in my Update manager also saying "New Distribution Release of 7.10 available" But when I use the cd nothing happens. I also tried the command: gksu "sh cdrom/cdromupgrade
even that doesn't work. Then i created another copy of it on another cd and still it doesn't work. I even added the cd from Synaptic packet manager option. and still it doesn't work. Pls help...

---

### Post by rsambuca on 2007-12-05
You need the alternate CD to upgrade from.  If you have the liveCD it is not possible to upgrade from Feisty with this method.

---

### Post by deepjaju on 2007-12-05
I when to shipit.ubuntu.com and ordered the 7.10 cd.. wont that work ??? If not then how do I get the alternate cd ????????

---

### Post by Pumalite on 2007-12-05
Here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark the box below sign 'Start Download'

---

### Post by rsambuca on 2007-12-05
You can use the liveCD to do a fresh installation, or you can download and burn an iso of the Alternate CD.

---

### Post by namko on 2007-12-05
Hello,

Trying to upgrade from feisty Kubuntu using alternate CD (after a failed upgrade using Update Manager). When booting from CD I get no option to reinstall. I get the following options:

Install in text mode
OEM install
Install a command-line system
Check CD for defects
Rescue broken system
Memory test
Boot from first disk

After pressing F6 and typing (specific for Kubuntu) ```
kdesu "sh /cdrom/cdromupgarde"
``` I get an error and the last line reads the following:

Kernel panic -not syncing: VFS: Unable to mount root fs on unknown-block(104,1)

Where do I go from here? Thanks.

---

### Post by namko on 2007-12-06
I was able to resolve my upgrade issues by running ```
sudo dpkg --configure -a
```still would like to know on how to upgrade from CD. Thanks again.

---

### Post by rsambuca on 2007-12-06
> **namko said:**
> Hello,

Trying to upgrade from feisty Kubuntu using alternate CD (after a failed upgrade using Update Manager). When booting from CD I get no option to reinstall. I get the following options:

Install in text mode
OEM install
Install a command-line system
Check CD for defects
Rescue broken system
Memory test
Boot from first disk

After pressing F6 and typing (specific for Kubuntu) ```
kdesu "sh /cdrom/cdromupgarde"
``` I get an error and the last line reads the following:

Kernel panic -not syncing: VFS: Unable to mount root fs on unknown-block(104,1)

Where do I go from here? Thanks.

You want to boot into your existing installation, and then put in the Gutsy CD.  It will then see the disc and ask you if you want to upgrade from the CD.

---

### Post by stevecro on 2007-12-12
Hi,
New to the forum, pardon my inexperience. Haven't found how to do a new post yet (or even where the help instruction is to do a new post) so replying to this one because I have the same problem. 1) Downloaded the alternate CD and checksummed it, 2) burned it to a CD with K3B (from a SuSE/KDE machine but should be OK, right?), 3) brought CD to other machine with a Ubuntu installation, 4) inserted it while up in Ubuntu (7.04) and the "update dialog" came up, and here is where it gets interesting. Update dialog said that a CD with packages had been detected and asked me if I wanted to a) use update manager or b) run an upgrade (or cancel). Regardless of which one I choose, I get a similar outcome. Error message comes up saying things like: a) "Cannot add CD", b) cannot locate packages, c) that I should check whether or not I have a real Debian or Ubuntu CD, and d) update is aborting and original state will be restored. I have tried running the CD in both of my CD drives but that doesn't help. (Tried this because error message started with a strange "E:".) Why would the system detect that I have something usable for upgrade when the CD first spins up but then doesn't recognize it any more and can't find what it needs on it when it goes to do the upgrade? Have tinkered with various Linux installs and upgrades now and then for several years now (just got done upgrading a SuSE 10.0 to 10.3 from disks with no problems at all), but this one I cannot figure out. Any help is appreciated (with how to do new posts in this forum or this upgrade problem with the downloaded alternate CD). Thanks!

---

