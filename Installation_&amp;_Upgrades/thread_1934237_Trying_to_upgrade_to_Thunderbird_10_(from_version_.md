---
title: "Trying to upgrade to Thunderbird 10 (from version 9) on Ubuntu 11.10"
date: 2012-03-01
forum: Installation &amp; Upgrades
---

### Post by jcarrete on 2012-03-01
Hi All,

I have been trying to get the newest version of Thunderbird installed on my Ubuntu 11.10.  Unfortunately, although I found a source that said this would happen automatically, this has not occurred.  I tried by adding the corresponding official and stable repositories but I get nothing but error messages wen updating the software sources.

Also, I tried by clicking on the "Download the latest version" within the about window and it gets stuck.

Any suggestions on how to get Thunderbird upgraded.

Cheers,

jcarrete

---

### Post by ottosykora on 2012-03-02
well yes, all this goes automatic. When a version is ready in the repository it will be installed.

Are you updating with update manager, or how exactly?

What version do you see in synaptic or software center?

Did you try 

sudo apt-get update
sudo apt-get upgrade

---

### Post by jcarrete on 2012-03-02
This is interesting.  I never tried to check the version with Synaptic which says I do indeed have version 10.0.2.  However, the About screen in Thunderbird says I have 9.0.1.  I am puzzled.

I dug a bit further and it seems I also have thunderbird-mozilla-build package in version 9.0.1 while all the other Thunderbird packages are in version 10.0.2.

I uninstalled everything (both 10.0.2 version and 9.0.1 version) and then used Ubuntu software centre to install.  Since the verstion on Ubuntu Software Centre is 10.0.2 so the end result was to have a true upgrade.

Thanks ottosykora to suggest to check the version in Synaptic.

Cheers,

jcarrete

---

