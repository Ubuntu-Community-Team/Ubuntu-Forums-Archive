---
title: "How to Upgrade from 10.10 to 11.04?"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by lads on 2011-05-14
Ok, so I downloaded the ISO, made a bootable USB and tried Ubuntu 11.04. Not perfect yet, but with enough novelty for me to want the upgrade.

To avoid burning a CD I tried it mounting the ISO, here's the result:

```

$ sudo mount -o loop /media/Kohntarkosz_/home/lads/temp/Ubuntu\ 11/ubuntu-11.04-desktop-i386.iso /media/cdrom
$ gksu "sh /media/cdrom/cdromupgrade"
sh: Can't open /media/cdrom/cdromupgrade

```

Strange, though I can't find any file named "cdromupgrade" in the ISO. Then tried mouting it with apt:

```
$ sudo apt-cdrom add /media/Kohntarkosz_/home/lads/temp/Ubuntu\ 11/ubuntu-11.04-desktop-i386.iso 
Using CD-ROM mount point /media/apt/
Identifying.. [9cdf58f02621e6ed9e2371b91e22d87e-2]
Scanning disc for index files..
Found 0 package indexes, 0 source indexes, 0 translation indexes and 0 signatures
Using CD-ROM mount point /media/apt/
Identifying.. [9cdf58f02621e6ed9e2371b91e22d87e-2]
Scanning disc for index files..

E: Unable to locate any package files, perhaps this is not a Debian Disc or the wrong architecture?

```

Even stranger, since I was able to create a bootable USB disk with Ubuntu from this ISO.

Giving up I tried to upgrade from the internet. Opened up Update Manager, went to Settings, then Updates and confirmed the "Show new distribution releases" option was set to "Normal releases". Back to the Update Manager, clicked Check, but the upgrade option simply doesn't show up.

So, how do I upgrade to Ubuntu 11.04?

Thank you,

Luís

---

### Post by Hedgehog1 on 2011-05-14
If you boot from the LiveUSB you have created, you may have an upgrade patch offered in the 'install 11.04'.

[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]

If this is not offered, if you have you data in a separate '/home' partition you can reinstall 11.04 over your 10.10 '/' partition and opt to not format the '/home' partition:

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

### Post by lads on 2011-05-17
Thank you Hedge for your reply.

Booting with the USB I do not have have the upgrade option, the other two are there, but not that one.

Out of desperation I burnt the damn CD to see if I could solve the issue that way. Again the command:

```
sudo gksu "sh /media/cdrom/cdromupgrade"
```

yields the same "Can't open" error. I believe the script isn't included in this release of the CD.

Unexpectedly, today the "New Ubuntu release '11.04' is available" option showed up for the first time in Update Manager. There must be some delay between the full Ubuntu release and the upgrade release.

I should manage to upgrade, though it requires a decent internet connection. I think it is important for an off-line upgrade option to exist, in many situations (and in some places of the world) the on-line upgrade simply isn't an option.

Thank you,

Luís

---

