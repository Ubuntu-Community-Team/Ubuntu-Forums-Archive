---
title: "Ugrade from Jaunty to Karmic fails with a dependency problem"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Lazy123 on 2009-10-01
Here is the bugreport [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/437087](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/437087)

And if I type "sudo apt-get -s dist-upgrade" the last line will be:
```

E: Couldn't configure pre-depend openoffice.org-core for openoffice.org-filter-binfilter, probably a dependency cycle.

```

Would it be safe to remove Openoffice, upgrade to Karmic and then try to install Openoffice again?

---

### Post by NormanFLinux on 2009-10-01
Wait til the end of the month to upgrade, when the official release is available. Beta software is not meant to be installed on machines you use on a regular basis.

---

### Post by Hakkatuka on 2009-10-01
Remove openoffice.org-filter-binfilter then upgrade. Install it again after the upgrade, or just wait until it is resolved.

---

### Post by Lazy123 on 2009-10-01
Well, the front page suggests to test the beta out, but it is kinda hard when the upgrade fails before it even starts. :)

I have used Linux systems since Debian Woody so I'm not afraid of couple of minor bugs, but it would be nice if someone would confirm it is just Openoffice that is broken at the moment.

---

### Post by Hakkatuka on 2009-10-01
It was just OpenOffice.org for me.

---

### Post by nanog on 2009-10-01
> Would it be safe to remove Openoffice, upgrade to Karmic and then try to install Openoffice again? 

Yes.

---

### Post by Lazy123 on 2009-10-01
Thanks for quick replies. Removing openoffice.org-filter-binfilter worked and now I have Karmic beta installed.

---

### Post by DivingWind on 2009-10-06
F#$k yeah, love this community! Had the same prob with openoffice, now all resolved.

---

### Post by ronocdh on 2009-10-12
It should be noted that the real bug report is [here]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/442651"). OP posted a duplicate.

Also, although it's probably common knowledge by now, this bug definitely affects those trying to upgrade to the beta, too (not just to Alpha 6).

---

