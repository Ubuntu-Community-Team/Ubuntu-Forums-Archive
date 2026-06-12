---
title: "Hard freeze after nfs-common upgrade"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by BathroomNinja on 2007-04-25
I've been using Ubuntu for over a year now, just dist upgraded from Edgy to Fiesty, everything working great.  Yesterday, I had a few upgrades available:

libnfsidmap2
nfs-common 1.0.12-4
nfs-kernel-server 1.0.12-4
tzdata2007e  something, I didn't write down the rest of it.

After upgrading, my system pulled a hard freeze.  Everything locked up, mouse, keyboard lights, etc..  CTRL-ALT-F1 - F8 did nothing obviously, since even the KB was locked.  I let it sit for about 20 minutes with no changes before I did a hard reset.  

Of course, Ubuntu then checks my drives, a long but necessary process.  I thought it might just be a fluke, so I began using my system again and after about 30 minutes, another hard freeze.  Rebooted again, and after another long hard drive check, using my system once again.  This time, after about 8 minutes of use, the hard lock up.  So I reboot into recovery mode, and check my apt logs to write down the last things I had installed.  I found the 4 packages listed above, so I removed them.  Rebooted the system, let it run for about 2 hours this time, everything working great.  Well, great except that I need to run NFS.  So I re-install nfs-common and server and it brings those 4 packages along with it.  Within another 20 minutes or so, another hard freeze. 

So, I pop in my old trusty Edgy live CD and let my system run all night with no issues.  I'm currently using the CD right now.  I'd file a bug report, but I'm not sure exactly whats causing this problem or which logs I need to grab.

Anyone have any recommendations for me?  If not, I'm going to overwrite my current Fiesty install with a new on from a live CD.

---

### Post by bwdease on 2008-05-29
Try samba instead of nfs.  Or, if samba is already installed, they may be interfering with each other.  I'm not sure at all on the interference, but it was just a thought.  So, if nfs is your thing, maybe try uninstalling samba.

---

