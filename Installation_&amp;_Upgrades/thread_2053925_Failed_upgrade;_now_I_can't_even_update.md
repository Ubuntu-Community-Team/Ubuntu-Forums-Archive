---
title: "Failed upgrade; now I can't even update"
date: 2012-09-06
forum: Installation &amp; Upgrades
---

### Post by lesliek on 2012-09-06
I have a netbook with no CD drive. I wanted to upgrade its OS from 10.04 to 12.04. I downloaded to it the alternate iso, mounted that and ran the upgrade from it, all in accordance with instructions I found at the Ubuntu site. All went well.

I then wanted to do the same upgrade with my main computer and thought I'd save time by copying the iso to my main computer and following the same procedure.

For some reason, that didn't work. I got a message something like, unable to find packages on CD. So, I gave up on that idea and decided to do a network upgrade. Before doing that, I wanted to do an update to 10.04, but that didn't work. I got a message about needing a partial upgrade before I could update and when I tried that I got a message about update-manager-kde being marked for removal but being on the removal blacklist.

I then did various things to try to overcome that, but have now got myself into a position where I'm getting this message:

E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Error occurred while processing libuninum5 (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

I'm really in over my head now!

What should I be doing to get things back to where they were before my unsuccessful upgrade attempt?

---

### Post by raja.genupula on 2012-09-06
open your terminal and type/paste this 

```
sudo rm -rf /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid_universe_bin  ary-amd64_Packages
sudo apt-get update 
```

---

### Post by lesliek on 2012-09-06
Thanks very much for your reply.

I solved my last message problem by following this: [http://aziest.wordpress.com/2011/01/24/how-to-increase-your-apt-cache-limit/](http://aziest.wordpress.com/2011/01/24/how-to-increase-your-apt-cache-limit/)

As to my ultimate problem though, I realised what happened and think I should record it, just in case it matters to anyone else.

Before my attempt to upgrade via a mounted iso aborted, all my software channels had been reset as part of the upgrade process. Then, when the upgrade couldn't continue, it didn't restore my software channels to where they'd been. That's why I couldn't even update 10.04 anymore. 

When I realised that, I decided that the only way to fix it was to run the upgrade process again, this time from the network. That would again set the software channels and use them for the upgrade.

So far, that's working, since it's in the midst of downloading the upgrade right now.

Thanks again.

---

### Post by raja.genupula on 2012-09-06
Thats really glad news , now please mark your thread as solved from thread tools .

---

