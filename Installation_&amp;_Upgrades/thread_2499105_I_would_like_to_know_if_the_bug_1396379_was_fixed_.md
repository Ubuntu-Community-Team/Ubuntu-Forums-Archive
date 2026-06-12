---
title: "I would like to know if the bug 1396379 was fixed in the 24.04  installer"
date: 2024-07-12
forum: Installation &amp; Upgrades
---

### Post by buntus2 on 2024-07-12
I wonder if the bug was fixed and if the fix was merged in ubuntu installer. Here is the bug [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
The problem was Grub installs itself on the Windows partition (first drive, internal drive) of a dual boot system instead installing itself on the second drive(second drive, external boot Ubuntu drive).

On launchpad is not clear if this bug was fixed. Also is not clear if was merged to some versions of Ubuntu.

At the end of comments if shows something like [TABLE="class: bug-activity"]
[TR]
[TD="colspan: 2"]Changed in ubiquity (Ubuntu):[/TD]
[/TR]
[TR]
[TD="align: right"]**status**:[/TD]
[TD]Fix Released &#8594; Confirmed
[/TD]
[/TR]
[/TABLE]

But there is not marked in green to indicate that the problem was solved.
If I download the latest version of Ubuntu like 24.04, will I have issues with this bug?

---

### Post by tea for one on 2024-07-12
Ubuntu 24.04 has a new installer and does not use ubiquity.
The installer package is a snap:ubuntu-desktop-bootstrap	stable/ubuntu-24.04.
You will be able to nominate where Grub is installed and your choice will be respected.
In essence, the previous ubiquity problem has disappeared.

---

### Post by oldfred on 2024-07-12
Some flavors used Ubiquity though 23.10.
I use Kubuntu and it still had Ubiquity & issues with 23.10, but it changed to Calamares installer with 24.04 which did not have that issue.

Some unoffical flavors may still be using Ubiquity.

---

