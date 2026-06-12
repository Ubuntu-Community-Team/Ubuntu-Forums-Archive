---
title: "OS &quot;Rebuild&quot; Rather Than Install"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by beamendslrs on 2008-05-29
Hi All,
as a result of a problem raised in another thread, is it possible to do a "rebuild" of the OS (Gusty) rather than a full install? I'm thinking as in Windows where you can do a a re-install without trashing your data. 

The machine is work No. 1 machine, and last time re-installing everything (dbases, business apps etc) took about a week to get everything back to normal (and I lost my data - duff CDR!) so stating all over again (again!) isn't really an option.

Cheers
Richard

---

### Post by housam on 2008-05-29
You can upgrade to the next version through the update manager.

---

### Post by beamendslrs on 2008-05-29
> **housam said:**
> You can upgrade to the next version through the update manager.

Thats a thought! Is Hardy stable?

It's a pity you can't force an "uprdage" to the current version, that would be nice... save an awful lot of grief!

Cheers
Richard

---

### Post by zvacet on 2008-05-29
> It's a pity you can't force an "uprdage" to the current version, that would be nice...

Yes,you can do that.

```
sudo apt-get update && sudo apt-get upgrade
```

to be sure that your system is up-to-date.System>admin>update manager>check for updates ans you should see message that new version is available for upgrade.
Second option is to download Hardy alternate CD and upgrade with it.You can find upgrade instructions [here.]("https://help.ubuntu.com/community/HardyUpgrades")

---

### Post by Thanh-BKK on 2008-05-30
Hi :)

Isn't it possible, to keep a current version, to just boot from the Live CD, then "install" and, at the partitioner, just use the existing partitions and NOT format them? Thereby, effectively, overwriting the system with itself without touching personal data. 

Should work, no? 

Sorry, i'm too much of a newbie to know this kind of thing, just an idea. 

Best regards.....

Thanh

---

### Post by beamendslrs on 2008-05-30
> **zvacet said:**
> Yes,you can do that.

```
sudo apt-get update && sudo apt-get upgrade
```

to be sure that your system is up-to-date.System>admin>update manager>check for updates ans you should see message that new version is available for upgrade.
Second option is to download Hardy alternate CD and upgrade with it.You can find upgrade instructions [here.]("https://help.ubuntu.com/community/HardyUpgrades")

Sadly that, or upgrading to Hardy, won't work - I just can't get the dammed apt to ignore the damaged mysql-connector-obdc package.

SURELY there must be away - I needed to install some vital software a week ago for work, and all I've achieved is a near nervous break down! This is the king of stuff I associate with Windows - yet I've never had to re-install Windows. All I need is apt-ignore-that-bloody-package-and-get-on-with-it

is that too much to ask?

(Sorry to get snotty, but my linux experiences to date have not been very good, and in work environment it's costing me money - lots of it).

Cheers
Richard

---

### Post by zvacet on 2008-05-30
>  I just can't get the dammed apt to ignore the damaged mysql-connector-obdc package.

What is a damage?Do you need that package for your work?I´m not saying I will solve this,but with more information somebody will.

---

### Post by beamendslrs on 2008-06-02
> **zvacet said:**
> What is a damage?Do you need that package for your work?I´m not saying I will solve this,but with more information somebody will.

This is what dpkg returns:

beamends@beamends-1:/tmp$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of quasar-server:
 quasar-server depends on xinetd; however:
  Package xinetd is not installed.
dpkg: error processing quasar-server (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing mysql-connector-odbc-setup (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 quasar-server
 mysql-connector-odbc-setup

synaptic won't start ("need to reinstall mysql-connector-*")
apt saya pretty much the same thing.

I have tried *all* apt and dkpg options I can find, and read all the documentation I can find - this sort of thing just seems to be quietly ignored or "Oh, just reinstall the os!".

Cheers
Richard

---

### Post by antlachance on 2008-06-02
Just download the alternative cd here: [http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/) and scroll down to alternative cd.  It's what I used to update and it worked perfect.  I was having problems with Update Manager but the cd worked fine.

Anthony

---

### Post by beamendslrs on 2008-06-03
Right, I've found a solution. Probably a bit dodgy but seems to work ok.

Back up stuff!!!!

grep for "package-name"   (mysql-connector-odbc in my case)

look files found in /var/apt and var/dpkg

open such files and carefully delete references to "package-name" (usually a block of text giving info about that package).

et voila - done - "package-name" is gone!  No apparent affect on any other packages - all seems well. No need to re-install or upgrade!

Cheers
Richard

---

### Post by zvacet on 2008-06-04
Did you install **xinetd** as dependency for quasar-server?

---

