---
title: "package &quot;base-files&quot; became obsolute after upgrade"
date: 2022-07-30
forum: Installation &amp; Upgrades
---

### Post by mrq42 on 2022-07-30
Ubuntu 22.04 x64.
After the latest update the package ***base-files*** listed   obsolete in synaptic. What is wrong?

---

### Post by Impavidus on 2022-07-30
This is what you should have (except for a different server):```
$ apt-cache policy base-files
base-files:
  Installed: 12ubuntu4.1
  Candidate: 12ubuntu4.1
  Version table:
 *** 12ubuntu4.1 500
        500 http://nl.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     12ubuntu4 500
        500 http://nl.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```
Local or obsolete means that synaptic cannot find a source for the package. It should be in the main repository and you've got the right version. Something wrong with your software sources? Check /etc/apt/sources.list. jammy-updates main should be enabled. Or something wrong with your mirror? Try changing to a different server.

---

### Post by Claus7 on 2022-07-30
Hello,

I see that is not only in my system. In my case though is under upgradable packages for a couple of days now, yet it doesn't allow me to proceed to the upgrade. I'm using the main server. I would advice you to ignore it for the time being and soon enough I guess that will be updated. After my upgrade to jammy, I have faced similar issues with other packages as well, yet sooner or later they were fixed.

```
$ apt-cache policy base-files
base-files:
  Installed: 12ubuntu4.1
  Candidate: 12ubuntu4.2
  Version table:
     12ubuntu4.2 500 (phased 50%)
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages
 *** 12ubuntu4.1 100
        100 /var/lib/dpkg/status
     12ubuntu4 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy/main amd64 Packages

```

Changing server didn't change the state either.

Regards!

---

### Post by Impavidus on 2022-07-31
I see an upgrade waiting now too (phased at 70%). I think we have to assume this was a server glitch: the old version of the package was gone before the new version was available. Nothing to worry about. Upgrading base-files (and 10 other packages) now. A lot is going on; less than 12 hours ago I had another big upgrade.

---

### Post by mrq42 on 2022-07-31
*base-files *were upgraded, but now I get

The following packages have been kept back:
  python3-distupgrade ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk

---

### Post by deadflowr on 2022-07-31
> The following packages have been kept back:
python3-distupgrade ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk

These are being phased updated as part of the overall ubuntu-release-upgrader packages.

You can see what is currently in the phased-updates queue here: [https://people.canonical.com/~ubuntu-archive/phased-updates.html]("https://people.canonical.com/~ubuntu-archive/phased-updates.html")
I also see the ubuntu-release-upgrader current in the queue has few error reported.
(Those error reports are typically private so you won't be able to access or read them)

To learn more on the basics of phased-updates here: 
[https://wiki.ubuntu.com/PhasedUpdates]("https://wiki.ubuntu.com/PhasedUpdates")
and some more here: 
[https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345]("https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345")

---

### Post by Claus7 on 2022-08-01
Hello,

with today's updates, base-files package was upgraded. Now there are 20 or so packages listed as upgradable, yet they follow the same logic as base-files. I cannot see them in the phased-updates link though. Among those packages are libreoffice and mesa ones. JFYI.

Regards!

---

### Post by grahammechanical on 2022-08-01
For some years now the Ubuntu developers have followed the policy called Phased Updates. They send out upgraded packages to 10% of the users. If no one reports any problems then they send out the upgraded packages to another 10% of the users. And so one until the upgraded packages have been sent to all users. The purpose is to minimise user dissatisfaction and at the same time fix any reported bugs before the problem package gets sent to most of the users.

It is of the opinion that what you are seeing is due to the Phased Updates policy.

Regards

---

### Post by Claus7 on 2022-08-01
Hello,

> **grahammechanical said:**
> For some years now the Ubuntu developers have followed the policy called Phased Updates. They send out upgraded packages to 10% of the users. If no one reports any problems then they send out the upgraded packages to another 10% of the users. And so one until the upgraded packages have been sent to all users. The purpose is to minimise user dissatisfaction and at the same time fix any reported bugs before the problem package gets sent to most of the users.

It is of the opinion that what you are seeing is due to the Phased Updates policy.

Regards

so this means that I will see these packages as candidate upgraded packages, and when reasonable satisfaction is reached, then I will have the ability to actually upgrade them? I'm not so sure if this is the case with my system, since these packages are not listed as phased ones from the link of *deadflowr*. Anyway, using ubuntu for so many years, this is the first time I come across this (after upgrading to jammy). The thing is, as the OP observed, that some packages, instead of being under the category upgraded, are listed under the category obsolete, which might mess one's system if one tries to remove them, not knowing that actually are about to get upgraded.

Regards!

---

