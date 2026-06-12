---
title: "Upgrade from xenial tries to skip yakkety and then fails"
date: 2017-10-04
forum: Installation &amp; Upgrades
---

### Post by potatochip on 2017-10-04
Hello,

I'm trying to upgrade a PC from xenial LTS. My understanding is it should upgrade to yakkety and then I can upgrade again to zesty.
I've edited /etc/update-manager/release-upgrades and Prompt=normal

I check my version;

>lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:        16.04
Codename:       xenial

Try to upgrade from command line (no GUI on this box)

>sudo do-release-upgrade
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [836 B]
Get:2 Upgrade tool [1,268 kB]
Fetched 1,269 kB in 0s (0 B/s)
authenticate 'zesty.tar.gz' against 'zesty.tar.gz.gpg'
extracting 'zesty.tar.gz'
[screen is terminating]

Zesty upgrade fails, which is probably expected behaviour. 
But why is it going to zesty and not yakkety. Is there any clue as to what's going on?

I've run apt-update and apt-get upgrade so I'm up to date.

Thanks,

Simon

---

### Post by howefield on 2017-10-04
> **potatochip said:**
> ...Zesty upgrade fails, which is probably expected behaviour.

Not much help as I always do clean installs however, as I understand it upgrading to a new version of Ubuntu for some time now will attempt to go the latest supported release without the need to upgrade sequentially through each release, so, no, not expected behaviour.

---

### Post by grahammechanical on 2017-10-04
> But why is it going to zesty and not yakkety. Is there any clue as to what's going on?

Yakkety (Ubuntu 16.10) reached end of life 20 July 2017. So. Yakkety is not the next available supported release. Ubuntu 17.04 (Zesty) is.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)


Regards.

---

### Post by potatochip on 2017-10-04
Cool, I didn't realise that releases went unsupported so quickly and that you could skip releases.
I'll investigate what is going on with the error then.

Thanks!

---

### Post by coffeecat on 2017-10-04
> **potatochip said:**
> Cool, I didn't realise that releases went unsupported so quickly

Only the intermediate releases which are supported for 9 months only. If you want longer support, go for the LTS releases (long-term support) ones which are supported for 5 years. It's easy to tell which are the LTS releases - they are released in April in an even-numbered year. Hence the currently supported LTS releases are 14.04 (released April 2014) and 16.04 (released April 2016). The release number rather than name gives you release year and month.

---

### Post by howefield on 2017-10-04
> **potatochip said:**
> Cool, I didn't realise that releases went unsupported so quickly and that you could skip releases.

Unless you have good reason to upgrade it might be better to wait another 6 months to April next year when the next Long Term Support is released, LTS releases like your current 16.04 have 5 years of support.

---

### Post by potatochip on 2017-10-04
Looks like my apt sources were buggered. All good now.

Thanks for the info!

---

