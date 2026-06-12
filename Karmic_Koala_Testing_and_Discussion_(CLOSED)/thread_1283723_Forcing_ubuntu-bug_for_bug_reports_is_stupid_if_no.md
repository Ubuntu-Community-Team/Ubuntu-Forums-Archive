---
title: "Forcing ubuntu-bug for bug reports is stupid if non-genuine packages aren't permitted"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-10-05
[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/443961](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/443961)

Let's say I'm using a ppa version of xserver-xorg-video-intel  but I want to report a bug against the version in the main repo.

In order to file a bug, I have to uninstall the ppa version, install  the repo version and then hope for the best with ubuntu-bug.

This needs to be fixed for Karmic.

---

### Post by exploder on 2009-10-05
> This needs to be fixed for Karmic.

The whole Intel issue needs to be resolved. Ubuntu is the only major distribution that still has issues with Intel....

---

### Post by VMC on 2009-10-05
> **exploder said:**
> The whole Intel issue needs to be resolved. Ubuntu is the only major distribution that still has issues with Intel....

Your absolutely right. My Fedora works perfectly using Intel video without any hacks.

---

### Post by exploder on 2009-10-05
> Your absolutely right. My Fedora works perfectly using Intel video without any hacks.

Yes, Fedora got it right in their last release. Intel graphics is problem free in OpenSuse milestone 8 too. I am posting from milestone 8 now, the final is not due till November but it runs nearly perfect as it is.

---

### Post by Keyper7 on 2009-10-05
> **Starks said:**
> [https://bugs.launchpad.net/ubuntu/+source/apport/+bug/443961](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/443961)

Let's say I'm using a ppa version of xserver-xorg-video-intel  but I want to report a bug against the version in the main repo.

In order to file a bug, I have to uninstall the ppa version, install  the repo version and then hope for the best with ubuntu-bug.

This needs to be fixed for Karmic.

That doesn't make any sense.

1) ubuntu-bug is not required for anything. It's *recommended* for official Ubuntu packages but if you don't want to use it you can use "?no-redirect". The bug reporting page makes that very clear.

2) The whole point of ubuntu-bug is collecting data about the context where the bug is happening. If the package is not installed such context does not exist.

There's nothing to be fixed.

---

### Post by Mr. Picklesworth on 2009-10-05
> **Starks said:**
> [https://bugs.launchpad.net/ubuntu/+source/apport/+bug/443961](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/443961)

Let's say I'm using a ppa version of xserver-xorg-video-intel  but I want to report a bug against the version in the main repo.

In order to file a bug, I have to uninstall the ppa version, install  the repo version and then hope for the best with ubuntu-bug.

This needs to be fixed for Karmic.

Good timing. I posted about precisely that to the mailing list!
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-October/009483.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-October/009483.html)

Adding ?no-redirect to the URL is not good. First of all, it demands some level of technical aptitude from the user. Granted, we don't want people reporting bugs who are totally clueless, but I like Launchpad for being amazingly easy to use. This breaks that. In fact, for me, it breaks bug reporting quite significantly because I often will try to fix a bug before filing a report. (It helps to gather some helpful data, too).

When I click a button that should do one thing and I get redirected to a Wiki page *hosted somewhere else*, I first of all feel like I am being hit by the wrong thing (the first time through I immediately hit Back and tried again, neglecting to pay the slightest attention to that Wiki page; I *know* how to file bugs for Ubuntu, thank you). The information for how to not get the Wiki page is hidden about halfway through. The whole thing looks really complicated.

Secondly, when ubuntu-bug complains about a package not being genuine, that also prevents us from submitting useful error information. We now must waste time by downgrading the package or figuring out the ?no-redirect thing, but then where's the fun GUI tool for submitting a memory dump?

A better solution would be, for example, a plugin or Firefox extension that automatically runs ubuntu-bug when filing a bug via Launchpad, making it an opt-in thing that fits with established workflows and stays out of my way when it breaks. And yes, I consider the run-around it gives me to be simply broken. It is not contributing positively for me, and where it does it could be better implemented anyway, as I mentioned.

Besides THAT, no other bugs are filed this way in Launchpad.

[SIZE="1"]Come to think of it (not in front of Ubuntu right now) does this even let people file bugs for packages which aren't installed? Needs-packaging bugs? Wont-install bugs? Bugs against components in the installer?[/SIZE]
[SIZE="3"]Edit: It does, so never mind :)[/SIZE]

---

### Post by Keyper7 on 2009-10-05
> **Mr. Picklesworth said:**
> Good timing. I posted about precisely that to the mailing list!
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-October/009483.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-October/009483.html)

Adding ?no-redirect to the URL is not good. First of all, it demands some level of technical aptitude from the user. Granted, we don't want people reporting bugs who are totally clueless, but I like Launchpad for being amazingly easy to use. This breaks that. In fact, for me, it breaks bug reporting quite significantly because I often will try to fix a bug before filing a report. (It helps to gather some helpful data, too).

When I click a button that should do one thing and I get redirected to a Wiki page *hosted somewhere else*, I first of all feel like I am being hit by the wrong thing (the first time through I immediately hit Back and tried again, neglecting to pay the slightest attention to that Wiki page; I *know* how to file bugs for Ubuntu, thank you). The information for how to not get the Wiki page is hidden about halfway through. The whole thing looks really complicated.

Secondly, when ubuntu-bug complains about a package not being genuine, that also prevents us from submitting useful error information. We now must waste time by downgrading the package or figuring out the ?no-redirect thing, but then where's the fun GUI tool for submitting a memory dump?

A better solution would be, for example, a plugin or Firefox extension that automatically runs ubuntu-bug when filing a bug via Launchpad, making it an opt-in thing that fits with established workflows and stays out of my way when it breaks. And yes, I consider the run-around it gives me to be simply broken. It is not contributing positively for me, and where it does it could be better implemented anyway, as I mentioned.

Besides THAT, no other bugs are filed this way in Launchpad.

Come to think of it (not in front of Ubuntu right now) does this even let people file bugs for packages which aren't installed? Needs-packaging bugs? Wont-install bugs? Bugs against components in the installer?

While I do agree that the Launchpad redirection needs some polish, I think there's nothing to be fixed in ubuntu-bug. Using it to report bugs in non-official packages defeats the entire purpose of it.

---

### Post by slakkie on 2009-10-06
There is a bug listed on LP for it:

[https://bugs.launchpad.net/ubuntu/+bug/443183](https://bugs.launchpad.net/ubuntu/+bug/443183)

---

