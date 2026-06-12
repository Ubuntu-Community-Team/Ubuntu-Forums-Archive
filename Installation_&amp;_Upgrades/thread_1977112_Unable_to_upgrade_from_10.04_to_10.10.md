---
title: "Unable to upgrade from 10.04 to 10.10"
date: 2012-05-09
forum: Installation &amp; Upgrades
---

### Post by Vitaminc23456 on 2012-05-09
I'm trying to get my system up to date completely, but for some reason I cannot upgrade from 10.04 to 10.10. I'm using the update manager and I keep getting this message.

 W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

I'm not entirely sure what it means, and if there is any kind of workaround I would gladly like to hear it

---

### Post by Vitaminc23456 on 2012-05-09
I'm trying to get my system up to date completely, but for some reason I cannot upgrade from 10.04 to 10.10. I'm using the update manager and I keep getting this message.

W:Failed to fetch [http://security.ubuntu.com/ubuntu/di...ty/Release.gpg](http://security.ubuntu.com/ubuntu/di...ty/Release.gpg) Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.canonical.com/ubuntu/...ck/Release.gpg](http://archive.canonical.com/ubuntu/...ck/Release.gpg) Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

I'm not entirely sure what it means, and if there is any kind of workaround I would gladly like to hear it

---

### Post by PaulW2U on 2012-05-09
10.10 is no longer supported.

It's probably possible to upgrade to 10.10 as the repositories have been archived but it's not advisable. You'd be better off either staying with 10.04 or consider moving to the latest LTS release, 12.04.

---

### Post by jadtech on 2012-05-09
change your server this one is not working

---

### Post by wilee-nilee on 2012-05-09
As suggested 10.10 is end of life. You can upgrade to 12.04 though. I would wait till the 12.04.1 is released in July and back up and clone the 10.04.1 to be sure your covered first. The LTS final versions are released after the main release.

clonezilla.org

---

### Post by Vitaminc23456 on 2012-05-09
if I'm going to upgrade to a LTS does that mean I'm going to have to go the ISO route?

---

### Post by wilee-nilee on 2012-05-09
> **Vitaminc23456 said:**
> if I'm going to upgrade to a LTS does that mean I'm going to have to go the ISO route?

No you can do it with a command, I forget at this point, to bring up the update manager with it showing.

Some people have had problems I don't know the percentage, but I would not do it with a cloned 10.04.1 myself, but thats just how I roll. :D

---

### Post by TBABill on 2012-05-09
10.10 is no longer supported so you may be trying to update to repositories that are no longer in place.

---

### Post by drs305 on 2012-05-09
Duplicate threads merged. Please only open one thread per topic.

---

