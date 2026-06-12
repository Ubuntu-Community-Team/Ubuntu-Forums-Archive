---
title: "Change in update server question"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by DocFrankenstein on 2008-01-22
Hello

I'm using gutsy with GNOME. I'm not very technical when it comes to computers, it's just that gates must die. ;)

Just a couple questions in terms of updates:

1) I intsall all of the updates as they come up. Is this a good habit?

2) I'd like to make sure that the updates are authentical and I'm not being offered to "upgrade" with a virus of sorts.

Why is this my concern? One of the updates previously reversed the a component of ubuntu from version 8.12 to version 8.03 or something similar.

Now, the updates are saying that:
* l.root-servers.net. got a new IP. (LP #160176)

I just want to make sure that there is actually a new IP and I won't be updating my OS with new and improved spyware features.

Thanks

DocF

---

### Post by dierre on 2008-01-23
Hello.

Don't worry, it's a legitimate update. You can check it here:
[https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/160176](https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/160176)
and here
[http://www.ripe.net/ripe/maillists/archives/dns-wg/2007/msg00171.html](http://www.ripe.net/ripe/maillists/archives/dns-wg/2007/msg00171.html)

By the way, when the update manager says "LP # XXXXXX" (with the X being digits) it refers to a bug tracked on the launchpad system, so you can check it there to get more information.

About the other problem you mentioned (that is an update that reverted a version number), probably you refer to this:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969)

What happened is that a security update was released, but then it was discovered that such update was breaking some important functionality, so the update had to be reverted and lastly a new security update had to be issued. It's quite inconvenient, and it seldom happens, but sometimes it does.

One line summary: whenever you're unsure about an update, checking launchpad is a good thing.

(Oh, and the updates are cryptographically signed, so, unless the keyring on your machine has been tampered with, the update manager should accept only legitimate updates)

Hope that helped.

---

### Post by DocFrankenstein on 2008-01-23
Awesome. Thanks.

---

