---
title: "How to add SSD write cache to existing btrfs stripe array"
date: 2015-03-26
forum: Installation &amp; Upgrades
---

### Post by Derek_Gentle on 2015-03-26
Hello All

I am wondering if there is a way to add a write cache to an existing btrfs stripe?
The issue I am having is when writing data to the stripe, it interrupts any existing read operations, causing XBMC / Kodi / Plex to pause for anywhere from a couple seconds up to almost a minute in some cases.

I am running Ubuntu Server 14.04 on a single dual core AMD Opteron with 4GB of DDR2 ECC memory.  This is my main media server and currently has just under 6TB of data used out of a total 14TB of available space.
I opted to use raid 0 / stripe as since this is only media, I'm not too concerned about data loss. That being said, I would rather *not* have to replace this amount of data.

I've done some reading and unlike ZFS, btrfs does *not* appear to support SSD caching 'out of the box', but there are other caching options available (dm-cache, ect).
(As a side note, I was running ZFS, but it's inflexibility when the need to expand arose, I opted to go with something with more flexibility).

Can someone advise if what I want to do is possible, and if so, point me in the right direction as to how to do so?

Many thanks in advance!

---

