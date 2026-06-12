---
title: "Can't boot ubuntu 15.10 after upgrade"
date: 2016-04-15
forum: Installation &amp; Upgrades
---

### Post by e10 on 2016-04-15
Same problem here but on **sda6**. Upgraded from 14.04 to 15.10 5 days ago without problem.
Events:
The Firefox browser crashed; try to relaunch; couldn't due that it was already running; open system monitor but couldn't see processes list, it kept on process activity; I shut down gently by the menu bar, at restart it came to the *[initramfs]* prompt.

All i get is: *The superblock cannot be read...*
*e2fsck -b 32768 /dev/sda1* don't work, it gave me same message, same with 8193.

with every command with sudo: *sudo is not found*.

*e2fsck -C0 -p -f -v /dev/sda1* gives: fsck not found

*dumpe2fs /dev/sda1 | grep -i backup* gives:
[I]dumpe2fs 1.42.12 (29 aug 2014)
Bad magic number in super-block while trying to open /dev/sda1
_
[/I]**I just realized that I was entering the wrong sda... Now it's OK. Thanks for help.**

---

### Post by howefield on 2016-04-15
Post moved to its own thread. Posting in an older thread marked solved is unlikely to increase your chances of attracting assistance.

---

