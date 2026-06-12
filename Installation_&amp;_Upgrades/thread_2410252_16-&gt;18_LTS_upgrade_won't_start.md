---
title: "16-&gt;18 LTS upgrade won't start"
date: 2019-01-13
forum: Installation &amp; Upgrades
---

### Post by Paul King on 2019-01-13
I am using Ubuntu Studio 16.04.5 LTS, and I am attempting an upgrade.

The Software Updater offers an upgrade, but clicking the "Upgrade ..." button makes the window disappear and nothing appears to happen. 

In the last software update, I received an error which said that the upgrader "stopped working" (after upgrading). I can't seem to find a log of this error, but if I recall what I error dump which I sent correctly, I believe apt had crashed, or something like that. 

These crashes are a common occurrence, but until now it hadn't bothered me, since it appeared to upgrade my software anyway. But now it's a problem, since it is preventing an upgrade from happening. /var/log doesn't seem to have an indication of this error: I looked under /var/log/apt and /var/log/unattended-upgrades, and found nothing there that looked like a crash message. /var/log/installer has no message file with a more recent timestamp than 2013.

This time, I recall seeing in the error log I sent a message suggesting that an upgrade was being attempted, but, again, apt had crashed. After that, I could start the Software Updater, be told my system was up-to-date, click on "Upgrade ...", and the window would simply disappear, with no further communication.

Has anyone else encountered this error? How do I fix this?

Paul King

---

