---
title: "Upgrade to Natty fails"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by Inglor on 2011-05-25
Hello all,

I am trying to do an upgrade from 10.10 to 11.04

When I start the ```
do-release-upgrade
``` from console and give password after some time it gives me an error on Calculating the changes.

I followed the instructions and filled in a [bug report](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/773995) but it turns out it wasn't a bug.


I think I downgraded my Xorg packages as suggested on the bug-report to the official ubuntu ones but still getting the error.

Can anyone propose something else?
I have a slight idea that my system has more "unofficial" packages installed.

Is there a way to find out which ones and downgrade them?
I am always saying downgrade them since the:
```
sudo apt-get update && sudo apt-get upgrade
```
doesn't do something.

Here follows the error:
> 
An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be
caused by held packages.

This can be caused by:
* Upgrading to a pre-release version of Ubuntu
* Running the current pre-release version of Ubuntu
* Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the
'update-manager' package and include the files in
/var/log/dist-upgrade/ in the bug report.


Restoring original system state

Aborting


Thanks
inglor

---

### Post by Hedgehog1 on 2011-05-26
I think you are going to need to the an clean install of Natty.

if you have your data in a separate '/home' partition you can install 11.04 over your 10.10 '/' root partition while leaving the data in your '/home' partition untouched:

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

