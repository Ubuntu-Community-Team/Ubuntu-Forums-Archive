---
title: "Distribution Upgrade Shows Incorrect Download Speed"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by chrisolof on 2007-10-11
The Distribution Upgrade program (from 7.04 to 7.10) says "kb/s" (kilo**bits** per second) next to the download speed, but the value it is posting is clearly in kB/s (kilo**bytes** per second).  There seems to be a capitalization typo there.

I just verified by checking the speed the Dist Upgrade program is reporting against the speed the System Monitor program reports - and they match.  The System Monitor program measures download speed in kB/s (kilobytes per second), accurately, so I know the problem lies in the Dist Upgrade program.

Anyway - if others are able to verify and reproduce this error in the Dist Upgrade program then I'll be filling my first bug report (unless it's already being fixed / already reported).

---

### Post by mbp on 2008-02-05
This still seems to be present in Hardy, so I filed [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/189454](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/189454)

---

