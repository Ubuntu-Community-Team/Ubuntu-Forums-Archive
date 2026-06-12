---
title: "Sleep Problem"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Cheat King on 2008-10-06
Hey, when I try to hibernate, I hear a horrible sound, and then there is a black screen with a login box. I type in the password, and then it loads back up with this message in the bottom, right hand corner:

[IMG]http://i119.photobucket.com/albums/o143/CheatKing/SleepProblem-1.png[/IMG]

I have looked in the help files and I can't find a solution. 

Thanks in advance.

---

### Post by Cheat King on 2008-10-12
Any help?

---

### Post by Xmister on 2008-10-12
You should take a look at your logs(eg. /var/log/messages, /var/log/syslog, /var/log/pm-suspend.log, /var/log/dmesg, /var/log/debug), maybe you see there something useful.

---

### Post by qubit67 on 2008-10-13
i have the same problem, R61 773215M.
The result of:

```
tail /var/log/messages
Oct 14 12:24:14 scalar kernel: [  141.059929] type=1503 audit(1223947454.087:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/6704/net/dev" pid=6704 profile="/usr/sbin/cupsd"
Oct 14 12:24:14 scalar kernel: [  141.324036] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 14 12:24:17 scalar kernel: [  144.474200] padlock: VIA PadLock not detected.
Oct 14 12:42:27 scalar -- MARK --
Oct 14 12:45:04 scalar kernel: [ 1391.520198] console-kit-dae[5637]: [COLOR="Red"]segfault[/COLOR] at 0 ip 49b1bd37 sp bfed1364 error 4 in libglib-2.0.so.0.1800.1[49abf000+b5000]
Oct 14 13:00:07 scalar kernel: [ 2294.065109] CE: hpet increasing min_delta_ns to 15000 nsec
Oct 14 13:22:27 scalar -- MARK --
Oct 14 13:42:27 scalar -- MARK --
Oct 14 14:02:27 scalar -- MARK --
Oct 14 14:22:27 scalar -- MARK --
```

hmm, i see a segfualt. I havent checked the bug reports yet.
it hadnt happened for a couple of days, i thought it was gone until I updated an hour or so ago, forgot what the new package was too.

It appears to be intermittant.

---

### Post by iponeverything on 2008-10-22
> **qubit67 said:**
> i have the same problem, R61 773215M.
The result of:

```
tail /var/log/messages
Oct 14 12:24:14 scalar kernel: [  141.059929] type=1503 audit(1223947454.087:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/6704/net/dev" pid=6704 profile="/usr/sbin/cupsd"
Oct 14 12:24:14 scalar kernel: [  141.324036] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 14 12:24:17 scalar kernel: [  144.474200] padlock: VIA PadLock not detected.
Oct 14 12:42:27 scalar -- MARK --
Oct 14 12:45:04 scalar kernel: [ 1391.520198] console-kit-dae[5637]: [COLOR="Red"]segfault[/COLOR] at 0 ip 49b1bd37 sp bfed1364 error 4 in libglib-2.0.so.0.1800.1[49abf000+b5000]
Oct 14 13:00:07 scalar kernel: [ 2294.065109] CE: hpet increasing min_delta_ns to 15000 nsec
Oct 14 13:22:27 scalar -- MARK --
Oct 14 13:42:27 scalar -- MARK --
Oct 14 14:02:27 scalar -- MARK --
Oct 14 14:22:27 scalar -- MARK --
```

hmm, i see a segfualt. I havent checked the bug reports yet.
it hadnt happened for a couple of days, i thought it was gone until I updated an hour or so ago, forgot what the new package was too.

It appears to be intermittant.

The sleep problems is being caused by the console-kit segfault.

[https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/269651](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/269651)

If you go down to the James Westby post on 2008-10-20 you will find a fixed deb for ibex.

---

