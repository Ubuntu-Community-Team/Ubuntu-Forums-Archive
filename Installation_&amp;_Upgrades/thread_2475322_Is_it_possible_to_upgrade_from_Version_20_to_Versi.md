---
title: "Is it possible to upgrade from Version 20 to Version 22?"
date: 2022-05-22
forum: Installation &amp; Upgrades
---

### Post by jasongeek on 2022-05-22
I just built my server with Ubuntu 20.04 but just noticed there's a 22.04 version. Is it possible to upgrade my server to this version or do I have to start all over?

---

### Post by Bashing-om on 2022-05-22
Hello jasongeek - Welcome to the Forum :D

> 
Is it possible to upgrade my server to this version ...

Yes !

The upgrade process from 20.04 to that of 22.04 is held until the release of the first point (22.04.1) to address any final bugs discovered. However, there is a means available for those who so desire.
in terminal run:
```

sudo apt update
sudo do-release-upgrade -d

```

[INDENT]my bit to try and help
[/INDENT]

---

### Post by grahammechanical on 2022-05-22
Not official for another six months. Ubuntu Long Term Support (LTS) versions have what is called point releases. In about six months time 22.04 will become 22.04.1 and so on every six months until the end of standard support in five years.

At the time of the first point release the Ubuntu developers will make it easy to do an online upgrade to Ubuntu 22.04 whether server or desktop edition.

Regards

Edit I offer this information

> Upgrading to a development release of Ubuntu is available using the -d flag. However, using the development release or this flag is not recommended for production environments.

> Upgrades from one LTS to the next LTS release are only available after  the first point release. For example, Ubuntu 18.04 LTS will only upgrade  to Ubuntu 20.04 LTS after the 20.04.1 point release. If users wish to  update before the point release (e.g. on a subset of machines to  evaluate the LTS upgrade) users can force the upgrade via the -d flag.

[https://ubuntu.com/server/docs/upgrade-introduction](https://ubuntu.com/server/docs/upgrade-introduction)

---

### Post by Impavidus on 2022-05-22
As said already, the upgrade process from 20.04 to 22.04 hasn't been released yet, but you can try it already. It may work.

However, as you just installed it and haven't spend much time configuring, it will be faster to clean install 22.04.

---

### Post by jasongeek on 2022-05-22
Thanks alot! It really helps. I'll wait because my sites will be production sites.

---

### Post by ubfan1 on 2022-05-22
Probably don't use the "-d" on do-release-upgrade anymore, 22.04 is no longer a development release ;^)  Try without an option, or maybe the -p (proposed).

---

### Post by guiverc on 2022-05-22
I'll provide the following Ubuntu 22.04 LTS release notice

[https://fridge.ubuntu.com/2022/04/21/ubuntu-22-04-lts-jammy-jellyfish-released/](https://fridge.ubuntu.com/2022/04/21/ubuntu-22-04-lts-jammy-jellyfish-released/)

In it you'll read the following

> Users of Ubuntu 21.10 will soon be offered an automatic upgrade to  22.04. Users of 20.04 LTS will be offered the automatic upgrade when  22.04.1 LTS is released, which is scheduled for the 4th of August. For  further information about upgrading, see: ...


ie. the *release-upgrade* process will open **after **the release of Ubuntu 22.04.1 LTS, which is scheduled for 4 August 2022.  That date refers to the ISO release date, the actual *taps* for upgrades are usually opened the following week, however there is no set date other than it's not before ISO release date.  If it's delayed (*be it days, or even weeks*) there will be reason for it, so for production systems I'd just wait.  

Of course always read the release notes, announcements etc..  eg. the link I provided has links for people wanting to know how to upgrade for desktop and server systems, with a lot more details to consider.

There is no real *new* detail here than prior comments; but I *believe* some details here are more accurate/precise (*in small ways*).  

Also note 20 & 20.04 are different systems, with Ubuntu Core 22 currently still in *beta*, though upgrades from 20 to 22 involve no user-level program changes meaning the impacts for servers are very different to 20.04 to 22.04 systems where the whole system (inc. user programs) are upgraded; no user-program changes is a benefit of the UC 20 & 22 system

---

