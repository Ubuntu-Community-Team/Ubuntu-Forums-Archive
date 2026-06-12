---
title: "Update stuck (12.04)"
date: 2013-08-11
forum: Installation &amp; Upgrades
---

### Post by Cocolate on 2013-08-11
I checked its not posted under these key terms..

I installed 12.04 without network connection. I am now running the updates with Internet.

When installing the updates. Half way through the installation the updates freeze on Libre-office and remain stuck at this point for hours...

upoon restarting I receive this error

```

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first.
```

I then run this command

```

sudo rm /var/lib/dpkg/lock
```

And that allows me to begin installation again.

Here is a code of my lshw


Im going out for a couple hours and when I return I hope this information is descriptive enough. Ive really got a busy day and this is holding me up.

Thanks

---

### Post by Cocolate on 2013-08-11
Idk why last night after restarting the updates were stuck in the same place (Libre0ffice) but this morning I just restarted again and all the updates installed [solved] lololo.

---

