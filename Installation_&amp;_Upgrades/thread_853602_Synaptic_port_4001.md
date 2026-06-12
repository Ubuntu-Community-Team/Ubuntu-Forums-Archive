---
title: "Synaptic port 4001"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by zellfaze on 2008-07-08
I know it has been posted before, but all of them came to a conclusion that I really do not like.  I get an error when trying to install things saying that Synaptic cant connect to localhost:4001.  I know this to be caused by the package annon-proxy.  The issue started after I installed that, and all of the other threads about this have been related to that package too.  I was able to fix the problem (well mostly fix it) by telling Synaptic to proxy its connections through localhost:8118 (which is privoxy).

Now I have some problems with that too though, Synaptic still tries to connect through localhost:4001 for many things (such as package lists) this has caused issues with updates.

I do not want to uninstall annon-proxy, because that will leave me unable to use Tor.  Anyone have any ideas?

---

