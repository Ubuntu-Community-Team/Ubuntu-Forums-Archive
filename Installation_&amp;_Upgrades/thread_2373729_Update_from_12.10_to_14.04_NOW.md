---
title: "Update from 12.10 to 14.04 NOW"
date: 2017-10-09
forum: Installation &amp; Upgrades
---

### Post by gsv91 on 2017-10-09
Can I upgrade from 12.10 to 14.04 via update manager? For now I have problem cause of dist/quantal-* is not exists for now. Can I change "quantal" to "precise"(12.04) in sorces.list and do the update via gui of update manager? Or I have to do it in other way?

---

### Post by Impavidus on 2017-10-09
12.10 reached end of life 3.5 years ago. You've had known security bugs for all that time. A direct upgrade from 12.10 to 14.04 was never supported (although it might work), you were supposed to go via 13.04 and 13.10. A lot has changed, so the upgrade would be unreliable.

I suggest a fresh install. And skip 14.04, jump to 16.04 directly. If your computer is older, you may prefer a lighter flavour, like Xubuntu.

---

### Post by Autodave on 2017-10-09
Every 2 years, a long term service release is made. These LTSs have a service life of 5 years: security and software updates are available for 5 years after the release.  The last LTS was 16.04. 16 stands for the year of the release, 04 stands for the month (April). The next LTS will be 18.04. Releases in the interim will be 6 month releases and only supported until the next release.

I stick with only the LTSs and even then I usually wait a month after their release before installing them. Further, I do not upgrade to them but completely install the new release after copying all files that I need to save to an external HD.

---

### Post by Bucky Ball on 2017-10-09
Another important point is that LTS releases upgrade via the net to the next LTS release, leap-frogging the interim releases in between. By the sounds of it, the LTS would be your best fit for now and the future. 

As above, recommend a clean install of 16.04 LTS. You can download the ISO and create install media (disk or USB), boot from that, 'Try Ubuntu' and backup any files you need from your old install, then install 16.04. ;)

---

### Post by Autodave on 2017-10-09
You also need to consider the specs on that machine. Ubuntu is a much heavier desktop than Xubuntu. Lubuntu is even lighter yet, but very plain. However, all the same programs can be installed regardless of what desktop you choose.

---

### Post by grahammechanical on 2017-10-09
If you wish to do it, you will need to do an End of Life upgrade. This shows how.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

You need to change not just the code name of the release but the URL of the repositories from Ubuntu.com to old-releases.ubuntu.com. So, your sources list file would have something like this

> deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) quantal main restricted universe multiverse

That will allow you to update 12.10 and then move on to 13.04. You would have to repeat this process to move on from 13.04 to 13.10.

Regards & have fun

---

