---
title: "downgrading to dapper"
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by icksa on 2006-10-03
Hi:
I was trying to install a package today, and I noticed that I was running into problems with dependencies. When I looked into it I saw that synaptic said a bunch of packages had versions > dapper and I think this is preventing me from installing a bunch of stuff...

I did have a couple of non-standard repositories in my sources.list, and I removed them, but synaptic wont downgrade all of the packages...

Is there a way to get synaptic to downgrade everything to the versions in the official repositories?

Thanks

---

### Post by pay on 2006-10-03
I think you can (but don't quote me) do ```
sudo apt-get install --reinstall xxx
```and that will install whichever one is in the repos.

---

### Post by icksa on 2006-10-04
Hi:
THanks for your reply, I managed to fix everything by reinstalling the old versions of packages one at a time...luckily there were only 4 I could find. I've read some disscussions/debates about whether users should be able to automatically download ALL of their packages and I understand the problems with this...

Is there anyway to at least automatically identify packages that have versions past what the standard repositories say they should have?

I had to resort to trying installing random packages that depend on lots of stuff to hopefully identify these...

Thanks

---

