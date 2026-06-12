---
title: "Critical update for KMail, when for Ubuntu?"
date: 2012-10-24
forum: Installation &amp; Upgrades
---

### Post by Magnentius on 2012-10-24
Hi all,

I use Lubuntu 12.10 with kmail installed.

The latest version in the repositories for kmail is 4.9.2, but this version has a very serious bug in the filters which causes kmail to duplicate messages. Using filters in kmail 4.9.2 is therefore impossible, which renders kmail for me unuable. This is a pity really, because I do think that kmail (kmail2 too) is a great piece of software.

See for a description of this bug [https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/883459]("https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/883459").

This bug has been fixed in kmail version 4.9.3, but still only 4.9.2 is available in the repositories. So I was wondering: will 4.9.3 come soon to Ubuntu? I have to stress that 4.9.2 is unusable.

And if we're stuck with 4.9.2 in the repos (which I do not hope), is there a way to manually upgrade to 4.9.3, without being a developer?

Thanks for your answer!

---

### Post by bra|10n on 2012-10-24
Kubuntu developers follows the KDE release schedule as closely as possible and so the link provided below gives you the planned release date of KDE 4.9.3;

[http://techbase.kde.org/Schedules/KDE4/4.9_Release_Schedule](http://techbase.kde.org/Schedules/KDE4/4.9_Release_Schedule)

---

### Post by Magnentius on 2012-10-24
So it comes november 6th 2012. Thanks!

---

### Post by snowpine on 2012-10-24
Ubuntu is "open source" software, meaning that development is transparent, meaning that every time something is changed or updated, you can read about it! :)

For kmail, the changelog is here: [http://changelogs.ubuntu.com/changelogs/pool/universe/k/kdepim/kdepim_4.9.2-0ubuntu2/changelog](http://changelogs.ubuntu.com/changelogs/pool/universe/k/kdepim/kdepim_4.9.2-0ubuntu2/changelog)

One scenario that might happen is that 4.9.2 will stay in 12.10, and if the bug is fixed, the patch will be applied to 4.9.2 and you'll read about it in the changelog. Ubuntu typically avoids post-release version bumps, preferring instead to patch the released/supported version. Of course some people use PPA's to stay on top of these things...

Anyway with fixed-release distros like Ubuntu, you can't necessarily tell just from the version number whether a bug has been fixed; you need to read the changelog. Here is a good article about the process (written for Red Hat but applicable to Ubuntu): [https://access.redhat.com/security/updates/backporting/?sc_cid=3093](https://access.redhat.com/security/updates/backporting/?sc_cid=3093)

---

### Post by Magnentius on 2012-10-24
Well, I  hope that the bug will be fixed in the Ubuntu 4.9.2 version.

I'm afraid when using the latest version of kmail, it might be unstable. Wine was like that a few years ago.

---

### Post by snowpine on 2012-10-24
> **Magnentius said:**
> Well, I  hope that the bug will be fixed in the Ubuntu 4.9.2 version.

I'm afraid when using the latest version of kmail, it might be unstable. Wine was like that a few years ago.

No need to "hope" because you can visit the bug report, see what is the status of the bug, maybe even submit some additional details of your own if you think it will help the developers. I also see there is a link to a patch on there if you would like to take matters into your own hands and fix the problem today. :)

---

