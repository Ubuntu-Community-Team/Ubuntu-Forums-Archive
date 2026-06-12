---
title: "Updating Clamav"
date: 2005-05-22
forum: Installation &amp; Upgrades
---

### Post by Usha on 2005-05-22
I tried going to here [http://ubuntuguide.org/#antivirusserver](http://ubuntuguide.org/#antivirusserver) , and I actually already installed it through synaptic, but I tried going through those manual steps, and it told me that:

 sudo freshclam
ClamAV update process started at Sun May 22 15:27:42 2005
WARNING: Your ClamAV installation is OUTDATED - please update immediately!
WARNING: Local version: 0.83 Recommended version: 0.85.1
main.cvd is up to date (version: 31, sigs: 33079, f-level: 4, builder: tkojm)
daily.cvd is up to date (version: 889, sigs: 1572, f-level: 5, builder: ccordes)WARNING: Your ClamAV installation is OUTDATED - please update immediately!
WARNING: Current functionality level = 4, required = 5

So I'm kind of perplexed on what to do next, I thought I was trying to update but it won't, so how do I update it then?

Thanks in advance

---

### Post by netrattler on 2005-05-22
Nothing you can do about this at the moment. They have not updated Clamav in the repositories yet. Basically what I did was uninstalled Clamav and installed the deb package from their website. 

Joe

---

### Post by shufla on 2005-06-22
Hi,

Use [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/) (only universe is enough).

Lukasz

---

