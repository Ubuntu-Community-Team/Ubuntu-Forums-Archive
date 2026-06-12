---
title: "Upgrade from 9.10 directly to latest?"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by b1lancer on 2011-05-25
I understand that I can upgrade to the next release using ubuntu's upgrade wizard. But it's been a while and there's 11.04 now. What are some recommendations?

---

### Post by Hedgehog1 on 2011-05-25
If you have your data in a separate '/home' partition you can install 11.04 over your 9.10 '/' (root) partition.

First, define your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Then define your '/home' partition:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

***The Hedge***

:KS

p.s. To learn how to move your '/home' into it's own partition: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

---

### Post by b1lancer on 2011-05-26
Thanks!

I guess everything is already in my /home folder because I just use the default places such as desktop documents music etc... and I understand all that is under the /home folder. Am I correct?

---

### Post by Hedgehog1 on 2011-05-26
No, just having a '/home' folder is not the same thing.

You need to move your data into a separate partition from the '/' (root) where it installed by default:

[IMG]http://img684.imageshack.us/img684/7977/mbrpariondemo16.png[/IMG]

This allows you to format and reinstall the OS in your '/' partition, but leave your data in it's own partition untouched.

To learn how to move your '/home' into it's own partition: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

***The Hedge***

:KS

[IMG]http://img694.imageshack.us/img694/2095/bartsimpsonchalkboard.png[/IMG]

---

