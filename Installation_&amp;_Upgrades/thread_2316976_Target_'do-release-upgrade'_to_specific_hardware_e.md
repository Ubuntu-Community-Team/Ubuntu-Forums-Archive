---
title: "Target 'do-release-upgrade' to specific hardware enablement stack / minor version"
date: 2016-03-12
forum: Installation &amp; Upgrades
---

### Post by unkmunk on 2016-03-12
Hi all and thank you in advance for any assistance I may receive.


[LIST]
[*]Currently I run an Ubuntu server on 12.04.5 LTS.
[*]I'd like to upgrade to Ubuntu server 14.04 LTS.
[*]If I 'do-release-upgrade', I will be moved to '14.04.3 LTS'.
[*]14.04 in general is supported through [2019 April]("https://wiki.ubuntu.com/Kernel/Support?action=AttachFile&do=get&target=Ubuntu+Kernel+Release+Schedule.png").
[*]The 'hardware enablement stack 14.04.3 is only supported through [2016 August]("https://wiki.ubuntu.com/Kernel/Support?action=AttachFile&do=get&target=14.04.x+Ubuntu+Kernel+Support+Schedule.png").
[/LIST]

I run LTS because it is in business and I like the extended support time frame.  I could wait until 2016 August to upgrade to 14.04.5 but I would prefer to upgrade to something more mature, additionally, I have the resources and time to do the upgrade now whereas 2016 August is more of an unknown.

My question then is, is there a way to re-target 'do-release-upgrade' such that I will migrate to 14.04.1 rather than 14.04.3?

Again I thank all for their time to consider my question.

---

### Post by deadflowr on 2016-03-12
[s]No
You'll get 14.04.4 and it's hardware stack (based on 15.10;wily werewolf).

Luckily, if only a server without a graphics stack, updating the the xenial kernel in August will be a cinch.
Since the server command is far simpler:
```
sudo apt-get install --install-recommends linux-generic-lts-xenial
```
or at least that is what it should be when the time comes.

Desktop HWE upgrades are a bit more complex, with all the Xserver and mesa packages and all.
More here: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)[/s]

See post #3.
I'm asleep at the wheel, evidently.

---

### Post by kansasnoob on 2016-03-12
Release upgrades always go to the original kernel series and X-stack if you're using do-release-upgrade. If you upgrade using a DVD/USB then the new kernel series will be dependent on the point release of the installation media.

You see on my current Trusty:

```
lance@lance-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty

```

But installation media used was either 14.04 or 14.04.1 so:

```
lance@lance-desktop:~$ uname -a
Linux lance-desktop 3.13.0-76-generic #120-Ubuntu SMP Mon Jan 18 15:58:41 UTC 2016 i686 athlon i686 GNU/Linux

```

The last digit indicating point release is updated along with 'base-files' regardless of the HWE stack:

```
base-files (7.2ubuntu5.4) trusty; urgency=medium

* /etc/issue, /etc/issue.net, /etc/lsb-release, /etc/os-release: Bump
version number to 14.04.4 in preparation for the point release.

-- Adam Conrad <adconrad@ubuntu.com> Tue, 16 Feb 2016 09:29:13 -0700

base-files (7.2ubuntu5.3) trusty; urgency=medium

* /etc/issue, /etc/issue.net, /etc/lsb-release, /etc/os-release: Bump
version number to 14.04.3 in preparation for the point release.

-- Adam Conrad <adconrad@ubuntu.com> Mon, 03 Aug 2015 10:39:14 -0600

base-files (7.2ubuntu5.2) trusty; urgency=medium

* /etc/issue, /etc/issue.net, /etc/lsb-release, /etc/os-release: Bump
version number to 14.04.2 in preparation for the point release.

-- Adam Conrad <adconrad@ubuntu.com> Tue, 03 Feb 2015 02:06:57 -0700

base-files (7.2ubuntu5.1) trusty; urgency=medium

* /etc/issue, /etc/issue.net, /etc/lsb-release, /etc/os-release: Bump
version number to 14.04.1 in preparation for the point release.

-- Adam Conrad <adconrad@ubuntu.com> Tue, 22 Jul 2014 09:22:44 -0600

base-files (7.2ubuntu5) trusty; urgency=medium

* /etc/issue{,.net}, /etc/{lsb,os}-release: Prepare for 14.04 LTS release.

-- Matthias Klose <doko@ubuntu.com> Thu, 10 Apr 2014 23:58:33 +0200 
```

[This]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") doesn't specifically address Precise to Trusty but it does for upgrading to Precise:

> anyone upgrading to Precise will not be automatically upgraded to the new Trusty HWE stack

[This]("https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes#LTS_Hardware_Enablement_Stack") may say it more clearly:

> Perform an update or upgrade to Trusty from a previous Ubuntu release. Only those installing from the 14.04.2 media or newer will automatically receive a newer hardware enablement stack by default. 

Confusing ain't it ;-)

---

### Post by deadflowr on 2016-03-12
^^^
Sometimes you install so many ways, you forget which way is up.
Thanks

Revised post #2

---

### Post by kansasnoob on 2016-03-12
> **deadflowr said:**
> ^^^
Sometimes you install so many ways, you forget which way is up.
Thanks

Revised post #2

The whole LTS HWE procedure needs to be better documented. I only know what I know because I've been iso/upgrade testing since 2008 so I get filled in by the QA team(s). And other times I only find out after I file a bug report expecting certain behavior only to learn later that what I expected was wrong :redface:

---

