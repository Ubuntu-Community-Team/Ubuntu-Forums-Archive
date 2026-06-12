---
title: "About upgrade Ubuntu 20.04 desktop to Ubuntu 22.04 desktop"
date: 2022-07-21
forum: Installation &amp; Upgrades
---

### Post by satimis on 2022-07-21
Hi all,

**[COLOR="#FF0000"]Upgrade Ubuntu 20.04 desktop to Ubuntu 22.04 desktop[/COLOR]**

SSD 500G
Ubuntu 20.04 desktop
KVM/QEMU

Free space 104G

I have backup the complete SSD.  Please see my another posting;

About backup the complete SSD hard-drive
[https://ubuntuforums.org/showthread.php?t=2477308&p=14105068#post14105068](https://ubuntuforums.org/showthread.php?t=2477308&p=14105068#post14105068)

I'll follow below tutorial to proceed;

How to upgrade from Ubuntu 20.04 LTS to 22.04 LTS
[https://www.cyberciti.biz/faq/upgrade-ubuntu-20-04-lts-to-22-04-lts/](https://www.cyberciti.biz/faq/upgrade-ubuntu-20-04-lts-to-22-04-lts/)

running command lines to do the job.

Pls advise what other attention I need to observe.

Thanks in advance.

Regards

---

### Post by Impavidus on 2022-07-21
The upgrade from 20.04 to 22.04 is expected to be officially released about two weeks from now, so you'll need the -d option. Or just wait a few more weeks.

The guide you found mostly focuses on servers and does some things that aren't needed on desktops. I assume you have local access to your desktop. It tells you to re-enable third party sources after the upgrade, but you have to make sure those sources have software for your new version of Ubuntu.

The upgrade can be aborted while still in the download phase, so a breaking internet connection is no problem. When installation has started, try not to abort. Fixing the inconsistent system may be hard.

Here is the official guide: [https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades). Unfortunately, it's not very detailed and a bit old, so it may not be very helpful.

Have you read the release notes and known bugs?

---

### Post by satimis on 2022-07-21
> **Impavidus said:**
> The upgrade from 20.04 to 22.04 is expected to be officially released about two weeks from now, so you'll need the -d option. Or just wait a few more weeks.

The guide you found mostly focuses on servers and does some things that aren't needed on desktops. I assume you have local access to your desktop. It tells you to re-enable third party sources after the upgrade, but you have to make sure those sources have software for your new version of Ubuntu.

The upgrade can be aborted while still in the download phase, so a breaking internet connection is no problem. When installation has started, try not to abort. Fixing the inconsistent system may be hard.

Here is the official guide: [https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades). Unfortunately, it's not very detailed and a bit old, so it may not be very helpful.

Have you read the release notes and known bugs?
Thanks for your advice.

In such a case I prefer waiting for another 2 weeks.  There is no urgency.

I have Ubuntu 22.04 desktop running on VM of Oracle VirtualBox on another hard-drive.  So far no problem found.

I need Ubuntu 22.04 for running GIMP 2.10.  There is problem running it on Ubuntu20.04

Regards

---

