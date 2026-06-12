---
title: "Live installer keeps restarting when setting static IP"
date: 2019-06-03
forum: Installation &amp; Upgrades
---

### Post by Karl1982 on 2019-06-03
I've had this problem for a while now and have reproduced it on a number of systems.  I've been working around it by using the older (non-live?) version of the Ubuntu Server installer.  Specifically I am referring to:

ubuntu-18.04.2-live-server-amd64.iso
ubuntu-18.04.2-server-amd64.iso

Environment: VMware ESXi 6.5, using default VM hardware settings for Ubuntu OS.

What happens is if I use the live installer, when I get to the network settings, if I leave it on DHCP then everything is fine.  However, if I set a static IP, as soon as I try to go to the next screen, the live installer resets.  It goes back to the first screen asking for my language.  This is 100% repeatable and has happened to me on several different host servers that I use across several different (and hashed) downloads of the ISO.  I believe it has something to do with being on VMware ESXi 6.0/6.5 as I have used the same install disc on an older ESXi host (5.5 I believe) and did not have the issue.

Using the older style installer, I have no problems.  I'm very surprised that I haven't seen other people having this problem since it seems to be a pretty stable issue, and there is a lot of Ubuntu running in VMware ESXi out there.  Has anyone seen this or does anyone know if there's a way to fix it?  It sounds like Canonical is looking to axe the old style installer, so I'd like to get onboard with the new one.  If I can actually get my OS installed.

---

### Post by PaulW2U on 2019-06-03
Take look at the following bug reports which I think describe your issue:

[https://bugs.launchpad.net/subiquity/+bug/1826537](https://bugs.launchpad.net/subiquity/+bug/1826537)
[https://bugs.launchpad.net/subiquity/+bug/1821966](https://bugs.launchpad.net/subiquity/+bug/1821966)

The issue has been fixed in Ubuntu 19.04 and will be fixed for the Ubuntu 18.04.3 release in due course. There's a couple of ways to work around the problem in comment #3 of the first bug report. Hope that helps.

---

