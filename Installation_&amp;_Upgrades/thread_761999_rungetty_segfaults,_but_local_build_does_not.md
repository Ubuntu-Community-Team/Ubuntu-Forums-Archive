---
title: "rungetty segfaults, but local build does not"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by Joshua Swink on 2008-04-21
I've got a fresh install of 8.04-rc, and rungetty is segfaulting.

I compiled the package locally, and the resulting binary does NOT segfault.

Anyone know why this would be? It's supposed to be the same source package, the same everything pretty much, so in theory if the package's binary segfaults, the locally-built binary should also segfault. But it runs just fine. (The reason I built it locally was to enable debugging symbols.)

I'm debating whether to open a bug to rungetty, but this seems like more of a compiler issue.

---

