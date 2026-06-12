---
title: "vista / kubuntu"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by Bashed on 2007-02-03
I've already installed Vista Ultimate on a single partition (120GB). What I did to create a new partition safely is use the disk management tool in Vista. I created a new partition at 30GB, 1st partition now down to 80GB estimate.

I booted off the latest feisty Kubuntu cd and attempted to install. My problem is the mount partition and swap partition on step 6 (or 7).  It won't let me use partition two (which is the new 30GB partition, labled drive E: ) for swap and mount. Now I'm not 100% sure how this works but why is this not letting me use this method?  It automatically selected /media/sda1 on the 80GB Vista partition and / on the 30GB linux (new) partition I wish to use and install to. That method did not work either.

Where to go from here?

---

### Post by Kateikyoushi on 2007-02-04
You need a swap and a / partition, the swap can small 512 MB should do.
Readm ore about linux partitions here. [LINK]("http://www.psychocats.net/ubuntu/partitioning")

---

### Post by Bashed on 2007-02-04
I got install going all the way to 94% until it failed. The error was something about grub failing on hd0 or such?  I was unable to provide a screenshot.

Any ideas even though I didn't provide a clear error message?

---

### Post by Bashed on 2007-02-05
Sorry to bump this but could someone lend me a hand on this? I do not want to mess anything up :)

---

### Post by Bashed on 2007-02-06
Anyone? I'm surprised, normally people respond so fast :)

---

### Post by Bashed on 2007-02-12
Can someone kindly help me out here?

---

### Post by Kateikyoushi on 2007-02-12
I looked around for a similar situation and found a bug in the launchpad. [LINK]("https://launchpad.net/ubuntu/+source/grub-installer/+bug/14135")

Do you use only sata drives per chance ?

---

### Post by Bashed on 2007-02-12
sata is what I use

---

