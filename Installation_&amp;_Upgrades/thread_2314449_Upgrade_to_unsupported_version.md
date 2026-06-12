---
title: "Upgrade to unsupported version"
date: 2016-02-21
forum: Installation &amp; Upgrades
---

### Post by thomas92 on 2016-02-21
Can I upgrade to an unsupported version of ubuntu? I want to know it because I want to move from 14.04 - 14.10 - 15.04 and finally to 15.10.

---

### Post by sammiev on 2016-02-21
If you wait a few months, you will be able to upgrade from 14.04LTS to 16.04LTS.

To update from 14.04 -> 14.10 -> 15.04 -> 15.10 (which 15.10 has a short life) is a lot of work and time and a lot can go wrong. 

If your computer is running well at this time, I would wait.

Always backup your data first before doing anything.

---

### Post by grahammechanical on 2016-02-21
This is the policy & practice.

If we want stability we install an LTS version. The interim releases only have 9 months support and they are where new stuff like Linux kernels are tried out. The LTS release are kept up to date with hardware developments by means of point releases.

For example, Ubuntu 14.04.4 was recently released. It comes with the Linux kernel & X stack that are in 15.10.

> In an effort to support a wider variety of hardware on an existing LTS  release, the 14.04.4 point release will ship with an updated kernel and X  stack by default. This newer hardware enablement stack will be  comprised of the kernel and X stack from the Wily 15.10 release.

To upgrade an existing 14.04 installation to 14.04.4 with the wily (15.10) hardware enablement stack please read the section "LTS hardware enablement stack" in the 14.04.4 release notes.

[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes)

Those release notes will also show what other areas of Ubuntu (such as Unity & Libreoffice) will also be upgraded. Ubuntu 14.04.4 is not 15.10 but it has the hardware enablement stack of 15.10 and a few of the other improvements to Ubuntu that appeared in 15.10.

Regards.

---

### Post by oldos2er on 2016-02-21
> **thomas92 said:**
> Can I upgrade to an unsupported version of ubuntu? I want to know it because I want to move from 14.04 - 14.10 - 15.04 and finally to 15.10.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) but it would be much easier to run a clean install of 15.10.

---

### Post by thomas92 on 2016-02-21
In that link there is shown how to upgrade from unsupported ubuntu to supported. I want the oposite. From 14.04 to 14.10 firstly.

---

### Post by deadflowr on 2016-02-21
upgrades from 14.04 will go directly to 15.10 now.

---

### Post by grahammechanical on 2016-02-21
> [COLOR=#000000]In that link there is shown how to upgrade from unsupported ubuntu to supported. I want the oposite. From 14.04 to 14.10 firstly.[/COLOR]

Look carefully.

> [COLOR=#333333][FONT=Ubuntu]To begin the upgrade, make sure you have a sources.list like the following, with CODENAME being your release, e.g. quantal.[/FONT][/COLOR]
> 
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-security main restricted universe multiverse


The 14.10 (utopic) repositories are now at old.releases.com. So, you need to update 14.04 & then edit sources.list and change the present trusty URLs to

deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) utopic main restricted universe multiverse, as an example. Then update/upgrade/dist-upgrade and you should then be on 14.10.

That method will take us from an end of life release to another end of life release OR from a supported release to an end of life release that is next in line.

Regards

---

### Post by Bashing-om on 2016-02-21
thomas92; Hello;

As deadflowr advises; should workie direct now.
See: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1497024](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1497024) <- release upgrades should jump over unsupported releases

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by howefield on 2016-02-21
> **deadflowr said:**
> upgrades from 14.04 will go directly to 15.10 now.

+1

Set Software & Updates > Updates > to notify for any New Version.

Then check for available update via terminal.. (should show that 15.10 is available)

```
sudo do-release-upgrade -c
```  

and upgrade with

```
sudo do-release-upgrade
```

Wouldn't recommend it just as I wouldn't recommend upgrading via each individual release, although probably less stressful than 14.04 > 14.10 > 15.04 > 15.10 :) Much prefer clean installs, but tested the above on a virgin 14.04 install and posting this from 15.10.

```
hugh@trusty:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.10
DISTRIB_CODENAME=wily
DISTRIB_DESCRIPTION="Ubuntu 15.10"
hugh@trusty:~$ 
```

Not completely without glitch however that may well have been me rather than the system.

I'd recommend waiting a few weeks for 16.04 which is released the month after next (April 21st) unless you have a throw away install that you don't mind risking.

Remember any upgrade has risks and that you should backup all important files and remove any proprietary drivers, if they are being used.

---

