---
title: "Broken package on the system?"
date: 2007-07-10
forum: Installation &amp; Upgrades
---

### Post by Seven06Renault on 2007-07-10
So I had an error that said:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I did that, it seemed to work, then Java 6.0 showed up as another update in Update Manager.  But then when I clicked "Update" or what not, it said I have a broken package on my system and need to use the "Broken" filter to find it.  Where might I find this filter and what does it mean in terms of what I have to do?  Thanks a lot.

---

### Post by tgoose on 2007-07-10
On Synaptic, click Custom Filters on the bottom left. That will show you the broken package. From there I'm afraid I don't know. Last time I had a broken package I think it's ```
sudo apt-get install -f
``` that fixed it, but I couldn't be sure.

---

