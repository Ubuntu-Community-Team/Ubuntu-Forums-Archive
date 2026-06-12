---
title: "should i upgrade bodhi e17 10.04LTS to 12.04LTS?"
date: 2012-06-14
forum: Installation &amp; Upgrades
---

### Post by slixz85 on 2012-06-14
hi i know bodhi doesn't have a release of 12.04LTS but from update-manager if i upgrade it from 10.04LTS to 12.04LTS, am i going to run into problems since it uses r17 and not all of that new gnome unity shell crap or whatever it is? i have just upgraded through update-manager before and had some real issues but i would like to upgrade if it should be fine

---

### Post by black veils on 2012-06-14
dont do that.

bodhi will release their 12.04 based version in july. you need to do a fresh install of that.

afterwards, for the rolling release versions, its the usual:

```
sudo apt-get update && sudo apt-get dist-upgrade
```when you use the update manager, you should set it to *not*  notify of a new ubuntu version.

---

### Post by slixz85 on 2012-06-14
> **black veils said:**
> dont do that.

bodhi will release their 12.04 based version in july. you need to do a fresh install of that.

afterwards, for the rolling release versions, its the usual:

```
sudo apt-get update && sudo apt-get dist-upgrade
```when you use the update manager, you should set it to *not*  notify of a new ubuntu version.

ok. i had a feeling that would be a problem. could you list a few good lightweight rolling releases. i kinda like that idea.

and so is bodhi going to be a rolling release?

---

### Post by black veils on 2012-06-14
bodhi is already rolling release but every LTS based version requires a fresh install.


from the bodhi project leader himself:

          [1.4.0   March 2012      1.5.0   June 2012 – Last Update release to our 10.04 base      2.0.0   July 2012 – First Stable release to our 12.04 base      2.1.0   September 2012 – First Update release to our 12.04 base      2.2.0   December 2012      2.3.0   March 2013      2.4.0   June 2013      2.5.0   September 2013      2.6.0   December 2013      2.7.0   March 2014      2.8.0   June 2014 - Last Update release to our 12.04 base      3.0.0   July 2014 - First Stable release to our 14.04 base    ]("http://jeffhoogland.blogspot.co.uk/2011/12/bodhi-linux-release-schedule.html")

---

