---
title: "Problem installing package, now can't install anything"
date: 2012-01-17
forum: Installation &amp; Upgrades
---

### Post by paulb42 on 2012-01-17
Hello

I attempted to install Nokuntu as I was looking for a Linux equivalent of Nokia PC Suite. It said there were a lot of additional packages required, so it installed them first then the Nokuntu installation itself failed - it said either the package was corrupt or I had no permission (I do). I tried downloading it several times, just incase.

I tried removing the unwanted packages via Ubuntu tweak but this said that it needed to reinstall Nokuntu and couldn't find an archive for it.

I tried going into Synaptic package manager but that gave the same message and terminated. The message is :
> E: The package nokuntusp needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

How can I get round this? I can live without Nokuntu but would like the ability to use the package manager!

Update: Tried removing the package via Ubuntu Software Centre and got this:
> installArchives() failed: dpkg: error processing nokuntusp (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 nokuntusp

Thanks
Paul

(Ubuntu 10.04)

---

### Post by zvacet on 2012-01-19
TRy with 

```
sudo apt-get install --reinstall nokuntusp
```

---

