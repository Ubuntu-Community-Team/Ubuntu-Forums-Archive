---
title: "Woody to Hoary, or Woody to Warty to Hoary?"
date: 2005-04-05
forum: Installation &amp; Upgrades
---

### Post by sterwill on 2005-04-05
With Hoary nearing release, I installed it on my PowerBook last weekend, replacing Debian testing in the process.  I've been happy with it so far; the installation was pretty easy (although I should have chosen expert to weed out some of the large packages I won't use), but it got almost everything "just right."  I simply wiped the disk to install Ubuntu.

I also run a bunch of Debian Woody servers at work, and have Woody running on one of my own personal servers.  This morning, I entertained the idea of letting "apt-get dist-upgrade" do the work of upgrading my server, instead of wiping the disk.

The big question: should I go from Woody straight to Hoary, or would it be better to do the (probably better tested) upgrade from Woody to Warty, then upgrade that to Hoary?

My server is using Linux software RAID 1 (a simple mirror of two identical drives).  Will this cause any problems during the upgrade to the Ubuntu versions of the raid tools (I'm using raidtools2 0.90.20010914-15 right now)?  I've considered breaking the mirror, installing Ubuntu on to the second disk, then remapping the mirror backwards once it's up and running.

Anyone have any similar stories to share?

---

### Post by az on 2005-04-05
Woody to Hoary is supported.

apt-get dist-upgrade

---

### Post by sterwill on 2005-04-05
Great!  I suppose I should follow all the extra steps in the HOWTOs during upgrade (make sure groups are configured, remove backports, etc.).  I might try this tonight.

---

### Post by az on 2005-04-05
apt-get -s dist-upgrade
may be useful if you have a lot of backported stuff...

---

### Post by wazzup on 2006-07-10
I'm a bit behind :), but I could not update woody to hoary. 

```

Get:36 http://nl.archive.ubuntu.com hoary-backports/multiverse Release [109B]
Fetched 4035kB in 1s (2023kB/s)lease 109/109B 100%]
Reading Package Lists... Error!
E: Dynamic MMap ran out of room
E: Error occured while processing kword (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```

Doing woody -> warty now and it seems to go fine. Later on warty -> hoary -> breezy -> dapper or all in 1 upgrade if I feel brave (which I probably should, because dapper means brave in Dutch)

---

