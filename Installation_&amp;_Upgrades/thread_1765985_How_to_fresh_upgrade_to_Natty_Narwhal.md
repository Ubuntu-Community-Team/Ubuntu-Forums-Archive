---
title: "How to fresh upgrade to Natty Narwhal"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by jacqueshappy on 2011-05-23
I've had trouble in the past when upgrading at prompt to 11.04 and have since been told that it is in fact usually better to remove my version of ubuntu and then fresh install the new version. How do I do this and keep all my files and programmes or is it not possible?
Possibly ubuntu's biggest yet only flaw...?

---

### Post by Frogs Hair on 2011-05-23
Save your files to a USB/CD . You will have to reinstall your programs because when you run the installation disk the drive will formatted if you choose to use the entire disk. There may be updated versions of your programs on the new release also. [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by jacqueshappy on 2011-05-23
> **Frogs Hair said:**
> Save your files to a USB/CD . You will have to reinstall your programs because when you run the installation disk the drive will formatted if you choose to use the entire disk. There may be updated versions of your programs on the new release also. [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Can't I keep them on the computer somewhere? 
I don't have a usb big enough...

Also, I need my usb to install ubuntu 11.04

---

### Post by jacqueshappy on 2011-05-23
Also

How do I actually get rid of ubuntu in the first place before reinstalling it as natty

---

### Post by Hedgehog1 on 2011-05-23
If you boot from the 11.04 LiveCD/LiveUSB, you may have an upgrade path offered in the 'install 11.04'.

[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]

**If this is not offered**, if you have your data in a separate '/home' partition you can reinstall 11.04 over your 10.10 '/' partition and be sure to not format the '/home' partition:

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

