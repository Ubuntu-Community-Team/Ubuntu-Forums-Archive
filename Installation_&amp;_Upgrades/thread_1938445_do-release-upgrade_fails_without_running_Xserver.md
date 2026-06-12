---
title: "do-release-upgrade fails without running Xserver"
date: 2012-03-09
forum: Installation &amp; Upgrades
---

### Post by ankman on 2012-03-09
Currently I have oneiric but assume this problem might appear for other releases too.

I run Ubuntu on a computer without display (no mouse or keyboard too, which I access remotely via ssh), so no X server is running. That's why I chose do-release-upgrade and also ran it in a screen session, in case the ssh connection would terminate so the upgrade process would not die.

The last upgrade was in October or November 2011 here from natty to oneiric. I ran into a broken upgrade at one point where apparently an "X-popup" should had been displayed, about half way through. I had to kill the screen session and after quite some trouble (lock files from the main upgrade process weren't removed and other obstacles) I was able to start aptitude which was able to complete the upgrade.

Anyway, I consider it a design flaw if an "X popup" would come and ask for something in do-release-upgrade (which IMO is meant to not use X). There are other means to let the upgrader ask a question without using X.

---

### Post by Old_Grey_Wolf on 2012-03-11
try using do-release-upgrade -m server

---

### Post by ankman on 2012-03-11
> **Old_Gray_Wolf said:**
> try using do-release-upgrade -m server

Thanks. Will try that when the next upgrade is due and come back here to report. I might not upgrade the first days after the release is available (April 12th 2012) but a few weeks later though.

---

