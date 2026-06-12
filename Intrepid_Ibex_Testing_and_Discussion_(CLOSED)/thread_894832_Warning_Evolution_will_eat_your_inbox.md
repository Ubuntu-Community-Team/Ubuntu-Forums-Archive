---
title: "Warning: Evolution will eat your inbox"
date: 2008-08-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by David A Knight on 2008-08-19
Update today has caused evolution to chew up my inbox and generally screw up horribly.  Backup before running.

Only the inbox seems to be effected.

---

### Post by mattduckman on 2008-08-19
i don't see this issue.

i have two accounts, both configured for IMAP

what's your setup like? and what exactly do you mean by chew up, eat, and screw up horribly?

---

### Post by kimda on 2008-08-20
Hi. I have the same issue and made a bug report. 

[https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/259741](https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/259741)

---

### Post by David A Knight on 2008-08-20
> **mattduckman said:**
> i don't see this issue.

i have two accounts, both configured for IMAP

what's your setup like? and what exactly do you mean by chew up, eat, and screw up horribly?

Was a POP3 box, chew up I mean the body contents all disappear, all emails in the box end up with ? as the subject and not date, folder gives sync warnings doing anything, trash then can't empty.  All the other folders were fine, just the inbox damaged.

It has been enough to give me the kick I needed to switch to using IMAP so I have copies on the server + client.

---

### Post by Toe on 2008-08-20
The latest update seems to have fixed the problem.
Good thing I keep backups.

---

### Post by Nullack on 2008-08-20
Can I make a suggestion please - if we include package numbers related to these bugs its easier for the bug squad to manage it and also easier for the testers to try and replicate reports :)

---

### Post by antono on 2008-08-31
> **Toe said:**
> The latest update seems to have fixed the problem.
Good thing I keep backups.

Nope. The problem is here and now. My inbox is empty after migration.

apt-cache show evolution
Package: evolution
Priority: optional
Section: gnome
Installed-Size: 8656
Maintainer: Debian Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Original-Maintainer: Evolution Maintainers <pkg-evolution-maintainers@lists.alioth.debian.org>
Architecture: i386
Version: 2.23.90-0ubuntu1
Replaces: evolution-common (<< 2.6.2-3), evolution-plugins (<= 2.22.2-1)
Provides: imap-client, mail-reader
...

---

### Post by Nullack on 2008-08-31
Can I please suggest you add a comment to the bug stating its occuring on that revision too

---

