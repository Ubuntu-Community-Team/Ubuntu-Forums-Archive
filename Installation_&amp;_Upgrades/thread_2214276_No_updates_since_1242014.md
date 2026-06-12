---
title: "No updates since 1/24/2014?"
date: 2014-03-31
forum: Installation &amp; Upgrades
---

### Post by myrddinemrys on 2014-03-31
I'm using Kubuntu 13.04 64-bit (and 32-bit on another system, same prob).  I've not had any updates become available for over two months now (since 1/24/14). I know it's theoretically possible there have been no updates since then, but I find it odd, given that there are usually multiple security or bug-fix updates every week. So something's probably corrupted in the apt-get system. 

Does anyone know of a way to rebuild all apt-get related lists, etc? Here's what I've tried so far, without success:

disabling any non-ubuntu repo's
apt-get clean
apt-get autoclean
apt-get autoremove
rm -r /var/cache/apt/*.bin && apt-get update
rm -vf /var/lib/apt/lists/* && apt-get update

Any help would be greatly appreciated.

---

### Post by sandyd on 2014-03-31
> **myrddinemrys said:**
> I'm using Kubuntu 13.04 64-bit (and 32-bit on another system, same prob).  I've not had any updates become available for over two months now (since 1/24/14). I know it's theoretically possible there have been no updates since then, but I find it odd, given that there are usually multiple security or bug-fix updates every week. So something's probably corrupted in the apt-get system. 

Does anyone know of a way to rebuild all apt-get related lists, etc? Here's what I've tried so far, without success:

disabling any non-ubuntu repo's
apt-get clean
apt-get autoclean
apt-get autoremove
rm -r /var/cache/apt/*.bin && apt-get update
rm -vf /var/lib/apt/lists/* && apt-get update

Any help would be greatly appreciated.

Ubuntu 13.04 has [reached End Of Life]("https://wiki.ubuntu.com/Releases") - which is why you are not getting any updates

Please upgrade to a newer version of Ubuntu, such as 13.10 to continue with updates.

---

### Post by myrddinemrys on 2014-03-31
Wow, that's seriously short life. Less than a year? I always have upgraded once a year, whether it's an LTS or no, and usually there have been updates for the full year.

However the chart you provided definitely explains that it's EOL. Thanks! I had not even considered it would be so short.

---

### Post by Elfy on 2014-03-31
Releases changed to a 9 month life span - [http://fridge.ubuntu.com/2013/03/19/changes-in-ubuntu-releases-decided-by-the-ubuntu-technical-board/](http://fridge.ubuntu.com/2013/03/19/changes-in-ubuntu-releases-decided-by-the-ubuntu-technical-board/)

---

### Post by myrddinemrys on 2014-03-31
Thanks! I shall pay closer attention to the decisions of the Ubuntu Technical Board...

---

