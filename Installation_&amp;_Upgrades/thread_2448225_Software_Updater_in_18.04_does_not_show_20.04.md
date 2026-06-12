---
title: "Software Updater in 18.04 does not show 20.04"
date: 2020-08-04
forum: Installation &amp; Upgrades
---

### Post by deck on 2020-08-04
When I run update-manager from my user account or as root (yes, I gave root a password because I don't like continually running sudo), I do not see the upgrade to 20.04.  I would like to move on to the new release because of some changes but can't.  When I run "do-release-upgrade"  I get the following :

Checking for a new Ubuntu release
There is no development version of an LTS available.
To upgrade to the latest non-LTS develoment release 
set Prompt=normal in /etc/update-manager/release-upgrades.

Why is it trying to give me a development release?  I did the upgrade to 18.04 from either 16.04 or 14.04 through the Software Updater which should have been a stable release and not a development release.  Where is this hidden that I supposedly have a development release?

deck

---

### Post by ActionParsnip on 2020-08-04
You won't see the LTS for a week or so. It has to hit the first point release so when 20.04.1 is out you will see the release available

---

### Post by pbear42 on 2020-08-04
Or you could try this: [https://ubuntu.com/blog/how-to-upgrade-from-ubuntu-18-04-lts-to-20-04-lts-today](https://ubuntu.com/blog/how-to-upgrade-from-ubuntu-18-04-lts-to-20-04-lts-today)

---

### Post by srope01 on 2020-08-16
I am also running 18.04. In the software updater, I have the setting to "Notify me of a new Ubuntu version: For long-term support versions". 20.04.1 came out on 6 August but the option button to upgrade to 20.04 still does not appear when I run software updater. I assume this means that 20.04.1 is still not ready yet. Can someone please confirm this?

Silverrope

---

### Post by Impavidus on 2020-08-16
I can't confirm it (I freshly installed 20.04 a month ago (and before that ran 19.10)), but this isn't exceptional. For the past 21 months, you've been running 18.04 although a more recent release was available. Another week won't be a problem, right? It's assumed that you, as an LTS user, want stability above all else.

20.04.1 is ready, you can install it. The upgrade process to 20.04 may not be confirmed to be ready.

---

### Post by deadflowr on 2020-08-16
A couple issues are currently blocking opening up the upgrade path,
See: [https://discourse.ubuntu.com/t/focal-fossa-20-04-1-lts-point-release-status-tracking/17604]("https://discourse.ubuntu.com/t/focal-fossa-20-04-1-lts-point-release-status-tracking/17604")

Also, here's a bug report on the issue:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1890936]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1890936")

---

### Post by srope01 on 2020-08-16
Thanks for the replies and the links to the point release tracking. Yeah, I have been on 18.04 for quite a while so no problem for me about waiting.

---

### Post by rsteinmetz70112 on 2020-08-18
Looks like fixes have been released on the listed blocking bugs, So they should flip the switch pretty soon.

---

### Post by raccoonstrait on 2020-09-03
I noticed today that the holds on upgrading from 18.10.4 to 20.04.1  changed (one hold was removed) and therefore is getting closer. This page:

[https://discourse.ubuntu.com/t/focal-fossa-20-04-1-lts-point-release-status-tracking/17604](https://discourse.ubuntu.com/t/focal-fossa-20-04-1-lts-point-release-status-tracking/17604)

removed one of the 'holds', one other is pending, but if you follow the link for the hold:  [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1891680](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1891680) and scroll to the bottom we find:

[COLOR=#333333][FONT=Ubuntu][FONT=monospace]This bug was fixed in the package grub2 - 2.04-1ubuntu29
---------------
grub2 (2.04-1ubuntu29) groovy; urgency=medium
  * grub-install: cherry-pick patch from grub-devel to make grub-install
    fault tolerant. Create backup of files in /boot/grub, and restore them
    on failure to complete grub-install. LP: [#1891680]("https://bugs.launchpad.net/bugs/1891680")
  * postinst.in: do not exit successfully when failing to show critical
    grub-pc/install_devices_failed and grub-pc/install_devices_empty
    prompts in non-interactive mode. This enables surfacing upgrade errors
    to the users and/or automation. LP: [#1891680]("https://bugs.launchpad.net/bugs/1891680")
  * postinst.in: Fixup postinst.in, to attempt grub-install upon explicit
    dpkg-reconfigure grub-pc. LP: [#1892526]("https://bugs.launchpad.net/bugs/1892526")
 -- Dimitri John Ledkov <email address hidden> Tue, 01 Sep 2020 20:04:44 +0100
[/FONT]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][TABLE="class: bug-activity"]
[TR]
[TD="colspan: 2"]Changed in grub2 (Ubuntu Groovy):[/TD]
[/TR]
[TR]
[TD="align: right"]**status**:[/TD]
[TD]Fix Committed &#8594; Fix Released[/TD]
[/TR]
[/TABLE]

I may be wrong, and it may be too close to the weekend for an immediate response, but I think the upgrade release is nigh.

RaccoonStrait[/FONT][/COLOR]

---

### Post by coffeecat on 2020-09-04
[s]Doesn't appear to be a request for support.

*Thread moved to **Ubuntu, Linux and OS Chat**/*[/s]

Thread now merged with a support one - see next two posts.

---

### Post by raccoonstrait on 2020-09-04
Sorry, I hadn't thought of that, I thought the community would like to know about progress. I should have just replied to the original thread, which was this one:

[https://ubuntuforums.org/showthread.php?t=2448225&highlight=discourse](https://ubuntuforums.org/showthread.php?t=2448225&highlight=discourse)

Again, my apologies.

Raccoon Strait

---

### Post by coffeecat on 2020-09-04
No problem. As a reply to the thread you linked to, it's a useful piece of information. I've merged your thread with the linked one and kept the merged thread in Installation and Upgrades.

Thanks for the information.

---

