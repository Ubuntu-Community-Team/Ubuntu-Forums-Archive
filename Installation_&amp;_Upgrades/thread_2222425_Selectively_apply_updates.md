---
title: "Selectively apply updates"
date: 2014-05-06
forum: Installation &amp; Upgrades
---

### Post by Joseph_Xu on 2014-05-06
I have a couple Ubuntu servers and when I see messages like '9 packages can be updated, 9 updates are security updates', I would go 'sudo apt-get update' and 'sudo apt-get upgrade' to apply these updates. However, how can I selectively apply some of the updates available? Here is the use case. I would like first apply 9 updates to my test box and try them out. By the time I finish testing, there might 7 more new updates available but I haven't test them yet. So then, I would only like to apply the same 9 updates that have been tested to my production box, not the 7 new ones. Is there anyway like that?

Comments are welcome.

---

### Post by lukeiamyourfather on 2014-05-06
You can specify the exact package you want after the upgrade argument. If nothing is specified it simply upgrades everything to the latest.

---

### Post by ibjsb4 on 2014-05-06
Synaptic PM will give you a GUI and allow you to pick and choose updates and other things.

[https://help.ubuntu.com/community/SynapticHowto#To_Upgrade_a_Package](https://help.ubuntu.com/community/SynapticHowto#To_Upgrade_a_Package)

[https://apps.ubuntu.com/cat/applications/synaptic/](https://apps.ubuntu.com/cat/applications/synaptic/)

---

