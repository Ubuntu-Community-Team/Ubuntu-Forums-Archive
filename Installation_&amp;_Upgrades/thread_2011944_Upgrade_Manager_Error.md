---
title: "Upgrade Manager Error"
date: 2012-06-28
forum: Installation &amp; Upgrades
---

### Post by overcast on 2012-06-28
Hi,

I am seeing error of upgrade manager on ubuntu 12.04. Please take a look at the attatched image and see the error. 

[IMG]http://s18.postimage.org/nudhd21nb/Screenshot_from_2012_06_28_13_37_25.png[/IMG]

It says "not connected to the internet" but the system is connected and is working fine. I don't know why only one update is missing and not resumed. After this error there are no further upgrading available. 

Any suggestion on clearing this error? or cleaning ap-get cache so that i can start from scratch without this error?

---

### Post by dino99 on 2012-06-28
cant watch this image ;)

sudo apt-get update

---

### Post by overcast on 2012-06-28
Sorry here is the URL for image. You can copy the image URL from quote. 

> [http://s18.postimage.org/nudhd21nb/Screenshot_from_2012_06_28_13_37_25.png](http://s18.postimage.org/nudhd21nb/Screenshot_from_2012_06_28_13_37_25.png)

---

### Post by dino99 on 2012-06-28
well maybe the us.archive was down or this update-manager is still too buggy, better to use synaptic and purge update-manager.

---

### Post by overcast on 2012-06-28
How to use synaptic update manager for canonical updates?

---

### Post by dino99 on 2012-06-28
sudo apt-get install synaptic
sudo synaptic

then set your repo activated choice inside tabs

---

### Post by overcast on 2012-06-28
I already have synaptic but not sure how to select upgrade repository for ubuntu 12.04.

---

### Post by overcast on 2012-06-28
Solved.

I configured the synaptic for the best mirror for repository. I fixed the packages which has the issue and now things are working.

---

