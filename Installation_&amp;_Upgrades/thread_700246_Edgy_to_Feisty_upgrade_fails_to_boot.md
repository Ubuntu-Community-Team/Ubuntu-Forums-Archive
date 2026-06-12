---
title: "Edgy to Feisty upgrade fails to boot"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by dunks on 2008-02-18
Hi there, I recently upgraded from Edgy to Feisty, everthing seemed to work fine until I rebooted and the server which now appears to hang on booting. The server sadly was remote (Yes, not the best idea to upgrade like this on a co-located machine) so I replicated what I did on VMware and right enough, it hangs just after loading the "/etc/rc.local" script. I had a good look around and there seems to be a fix for this, as explained here[ https://answers.launchpad.net/upstart/+question/9887]("https://answers.launchpad.net/upstart/+question/9887") , I gave this a try after booting sucessfully with the rescue kernel, editing the required files and rebooted, upon booting it seemed to work, but with problems logging in, it seems as if theres an endless loop of consoles, each one prompting for login. Although SSH now works fine, i'm not keen on having this problem about local logins and I was wondering if anyone has any ideas on how to resolve this? Cheers.

---

