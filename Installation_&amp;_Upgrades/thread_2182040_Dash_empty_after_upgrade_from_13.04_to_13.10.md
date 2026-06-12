---
title: "Dash empty after upgrade from 13.04 to 13.10"
date: 2013-10-19
forum: Installation &amp; Upgrades
---

### Post by tomdkat on 2013-10-19
Today, I upgraded my Ubuntu 13.04 (64-bit) system to 13.10.  The upgrade went fine and the system boots ok.  When I opened Dash to run the synaptic package manager, so I could re-enable some repositories disabled during the upgrade, I noticed Dash returned no results for frequently used applications, nor did it return any results for ANY application types I applied a filter for.  For example, Dash reports no "System" applications or no "Internet" applications.  As a result, I can't locate the synaptic package manager and can't re-enable the repositories disabled during the upgrade.

So, how can I reset this?

Thanks!

Peace...

---

### Post by rihikz on 2013-10-19
Hello. Not sure how to exactly do this myself, without looking it up, but you might try reinstalling unity.

---

### Post by tomdkat on 2013-10-20
Thanks for the reply.  I hope a better solution is available.  :)   Good thing I had a terminal icon in the launcher, otherwise I'm not sure I would be able to open a terminal window to run the applications I need at the command line.

Peace...

---

### Post by vasilisc on 2013-11-01
```
sudo apt-get -o DPkg::options::=--force-confmiss --reinstall install unity-scopes-master-default
sudo apt-get -o DPkg::options::=--force-confmiss --reinstall install unity-scopes-runner
sudo apt-get -o DPkg::options::=--force-confmiss --reinstall install unity-scope-home

```

---

