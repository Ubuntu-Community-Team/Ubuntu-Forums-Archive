---
title: "Dual boot"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by tenrten on 2007-05-27
I want to dual boot windows and ubuntu. the option, guidec is not avaibel, it is not showing. Please give me some tips. Thanks Yall.

+Tenrten :popcorn:

---

### Post by rillip on 2007-05-27
Am I understanding you already have Ubuntu and Windows installed, but don't see Windows on menu.lst?

---

### Post by merlinus on 2007-05-27
Sounds to me that the guided partitioning option is not available, for some reason.....

Wonder why????  Maybe because of windows?

-merlin

---

### Post by rillip on 2007-05-27
If you want to keep Windows and are installing Ubuntu, it's best to use manual partitioning anyways.

Just back up any sensative Windows data, then resize the partition to give you room to install Ubuntu on.  Any size you want, minimum 5 gigs probably.

Then, it tells you right on there how many partitions you need; root and swap come to mine, but I believe there's a third.  Simply create those partitions with the sizes and filesystems you want (swap should be at least 500mb, at most about 2gig, and use the swap filesystem; evertyhing else I would make ext3 or fat32, if you want the data on the partition to be shareable), then click make changes, and continue with installation.  There's a number of install guides out there if you just search the net for them.

---

