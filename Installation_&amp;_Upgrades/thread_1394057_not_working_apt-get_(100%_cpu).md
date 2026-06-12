---
title: "not working apt-get (100% cpu)"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by narvik on 2010-01-30
Hi.
Yesterday I installed a fresh Ubuntu 9.10. Everything worked fine at first. When I added thunderbird it recommended a package thunderbird-gnome-support which I also tried to install. But since then everytime I install or remove something it outputs
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```
and the apt-get process takes up 100% cpu. Also when I log in the system the process "/usr/bin/python /usr/lib/update-notifier/apt-check" takes 100% cpu and there is an icon in the toolbar saying that a problem occured when checking for the updates.
Anyone knows how to solve this issue?
Thanks in advance.

---

### Post by bedge on 2010-07-08
Try running 'pstree -Alap', that'll show you what processes have been spawned by apt and it's errant friends.
Find the lowest level process in that tree and that's the one that's spinning.
Then run 'ps ax | grep <pid of errant proc from above>'
Look and the command line used to run it. That may offer some clue.

Run strace <same pid> to connect to this process to see what it's stuck/spinning on.

-Bruce

---

