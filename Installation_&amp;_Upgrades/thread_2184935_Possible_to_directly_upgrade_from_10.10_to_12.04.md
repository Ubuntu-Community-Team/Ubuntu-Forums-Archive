---
title: "Possible to directly upgrade from 10.10 to 12.04?"
date: 2013-10-31
forum: Installation &amp; Upgrades
---

### Post by Shabutaro on 2013-10-31
Hi, because of various reasons i never updated my Ubuntu past 10.10, but the day i have to upgrade has come. Now as 11.04 is also obsolete and i can't use the 'update to new version' anymore, do not have a seperate /home partition and also no means of backupping my ~400GB /home directory i wanted to ask you if it is possible to directly upgrade to 12.04. 

I have hopes of just changing the sources.list from maverick to precise and do a apt-get update will solve this problem, but i am scared to do this without asking beforehand. A friend of mine told me it is possible to directly upgrade 10.10 to 12.04, but i haven't heard from him how and due to personal reasons i can't get in touch with him now.

Thank you in advance for you help.

Shabutaro

---

### Post by fantab on 2013-10-31
I don't think you can. Even if you could I won't recommend it. To upgrade your path will be 10.10-11.04-11.10-12.04. It will be messy, time consuming affair.

Do a Clean install of 12.04 or 13.10.

1TB External/Internal disks are not very expensive. Buy one. Consider it time that you upgraded the HDD as well.

When you install Ubuntu do use a separate /home or a simple data partition to store your data to avoid situations like these.

Gook Luck....

---

### Post by carlwsnyder on 2013-10-31
You can directly upgrade from 10.04 to 12.04, which is that to which your friend may have been referring, but NOT from 10.10, only LTS to LTS or regular version to regular version.

---

### Post by Shabutaro on 2013-10-31
Ok so the next stop would be 11.04. One line in the how-to confuses me a bit: > Please make sure you have the following sources.list, change CODENAME to your release. Is 'your release' my current 10.10 maverick or 11.04 natty, the one i want to upgrade to.

I am referring to this guide: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by carlwsnyder on 2013-10-31
According to the [https://help.ubuntu.com/community/EOLUpgrades/Intrepid](https://help.ubuntu.com/community/EOLUpgrades/Intrepid) guide, CODENAME in that listing is your initial code name, ie. maverick.  During your update, it will be changed to natty, but you must, in the beginning make sure all of your /etc/apt/sources.list point to one and only one version of repository.

---

### Post by Shabutaro on 2013-10-31
So this should be allright as i don't really need backports or propesed? Or should i for my own safety include those, too?

> # Required
 deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) maverick main restricted universe multiverse
 deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) maverick-updates main restricted universe multiverse
 deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) maverick-security main restricted universe multiverse
 

---

