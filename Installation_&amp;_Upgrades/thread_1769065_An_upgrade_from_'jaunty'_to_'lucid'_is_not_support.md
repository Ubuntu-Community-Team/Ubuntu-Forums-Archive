---
title: "An upgrade from 'jaunty' to 'lucid' is not supported with this tool"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by ubrox on 2011-05-27
I seem to be stuck in a limbo. I am trying to update my system from 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

Admittedly, I havent kept this system up to date for a while. A couple of days ago, I started the update-manager and it did prompt me to upgrade to 10.04 LTS. I postponed it to take a backup. 

Today I try the same and the CLI command doesnt even offer the upgrade any more.

sudo apt-get dist-upgrade

So I fire up the update-manager, it does show me the upgrade but fails with the message

An upgrade from 'jaunty' to 'lucid' is not supported with this tool

I get the same message for sudo do-release-upgrade as well.

So how can I upgrade?

---

### Post by skeebs on 2011-05-27
Have you been following my thread of "upgrading to latest version from 9.04"? I'm still doing it nut I'm now opting for a fresh installation. Have  look there if not done so you may find some answers :)

[http://ubuntuforums.org/showthread.php?t=1767403](http://ubuntuforums.org/showthread.php?t=1767403)

---

### Post by ubrox on 2011-05-27
OK, I will try that. I am downloading the CD now

---

### Post by Hedgehog1 on 2011-05-27
If you have your data in a separate '/home' partition you can install 11.04 over your 9.x '/' (root) partition.

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

### Post by ubrox on 2011-05-27
I did the CD upgrade to 9.10 and then to 10.04 LTS using the dist-upgrade / do-release-upgrade

It worked like a charm. 

Thank you Skeebs

---

### Post by gavarchand on 2011-08-17
> **kalyanakrishna said:**
> I did the CD upgrade to 9.10 and then to 10.04 LTS using the dist-upgrade / do-release-upgrade

It worked like a charm. 

Thank you Skeebs.

---

### Post by gavarchand on 2011-08-17
> **skeebs said:**
> Have you been following my thread of "upgrading to latest version from 9.04"? ??I'm still doing it nut I'm now opting for a fresh installation. Have  look there if not done so you may find some answers :)

[http://ubuntuforums.org/showthread.php?t=1767403](http://ubuntuforums.org/showthread.php?t=1767403)...

---

### Post by gavarchand on 2011-08-17
> **kalyanakrishna said:**
> I seem to be stuck in a limbo. I am trying to update my system from 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

Admittedly, I havent kept this system up to date for a while. A couple of days ago, I started the update-manager and it did prompt me to upgrade to 10.04 LTS. I postponed it to take a backup. 

Today I try the same and the CLI command doesnt even offer the upgrade any more.

sudo apt-get dist-upgrade

So I fire up the update-manager, it does show me the upgrade but fails with the message

An upgrade from 'jaunty' to 'lucid' is not supported with this tool

I get the same message for sudo do-release-upgrade as well.

So how can I upgrade?...

---

