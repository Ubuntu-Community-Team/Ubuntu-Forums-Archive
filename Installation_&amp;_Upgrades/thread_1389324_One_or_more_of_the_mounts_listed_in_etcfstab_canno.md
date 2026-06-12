---
title: "One or more of the mounts listed in /etc/fstab cannot yet be mounted"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by nomnex on 2010-01-24
On a fresh Karmic installation, after a few days of use. I could not log-in any more this morning. Error message after the first splash screen (black & white logo)

> One or more of the mounts listed in /etc/fstab cannot yet be mounted:
/home/waiting for UUID=e2cca39c-70bb-46be-a5d1-2fdafe1dd2a1
Press ESC to enter a recovery shell

There are some threads about the same issue on Launchpad, but they are about the swap partition, and the problem occurs during a Karmic installation update.

---

### Post by tachuela on 2010-01-24
Edit /etc/fstab and replace the UUID for the correct one.

---

### Post by nomnex on 2010-01-24
UUID's were correct. There are few similar bug reports, but they are about an upgrade and dev/ are swap or root and they have mismatching UUID's. That's not the case here.

I have opened a new bug, see [1] with a workable solution > changing the UUID's for the labels, then re-editing the fstab.

[1] [https://bugs.launchpad.net/ubuntu/+bug/511963](https://bugs.launchpad.net/ubuntu/+bug/511963)

---

### Post by TwoToneSpirit on 2010-01-29
Myself and two of my friends are also having this problem, apparently independently.

It seems to be resolved by dropping to a shell and running "fsck -f -p" - I also add -v for verbose output.

It is now recurring almost everyday on my girlfriend's computer.  :-\

---

### Post by nomnex on 2010-01-29
> **TwoToneSpirit said:**
> Myself and two of my friends are also having this problem, apparently independently.

 I have opened a bug report on Launchpad, see my post above. Nobody has subscribed yet. If you experience such problem, I invite you to do it and to post your problem. 

TwoToneSpirit: "-p" flag is in a non-interactive mode. what's the "-t" flag for?

---

