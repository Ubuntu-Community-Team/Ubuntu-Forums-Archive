---
title: "ctrl-c / ctrl-z not working"
date: 2009-09-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nomenquis on 2009-09-05
Hi,

I've got 3 boxes running karmic, one 64bit (A) and 2 32 bit (B and C).
All machines have been updated today, so they're running the same (and the latest) version of all packages.

Now, when logging into machine C from either A or B via ssh I can not kill my current job via ctrl-c (or suspend it using ctrl-z)

For instance:

ssh from A to C, start top and try to ctrl-c -> nothing happens.
It works from A to B, B to A but not A to C or B to C :(

The kind of terminal I'm using to run ssh does not seem to matter either, I can be at a local console on A running ssh from there and still can not ctrl-c on C.

If i open a local console on C and try to ctrl-c there it works however.

Does someone have any idea on what might be going on?

kind regards

---

### Post by nanog on 2009-09-05
During a recent partial upgrade ctrl z and ctrl c were remapped in my gnome-terminal.
If the same thing happened to you just click edit and then select keyboard short cuts. Disable or edit appropriate tabs.

---

### Post by nomenquis on 2009-09-06
> **nanog said:**
> During a recent partial upgrade ctrl z and ctrl c were remapped in my gnome-terminal.
If the same thing happened to you just click edit and then select keyboard short cuts. Disable or edit appropriate tabs.

Nope, that's not my problem unfortunately :(

I did some more digging, it seems that something is broken about signal handling for processes spawned under ssh on that machine.

If I try to kill the processes from the command line via SIGINT, SIGTERM or SIGHUP nothing happens. Only SIGKILL works :(
So something is eating signals on that machine, but only on that machine.

kind regards

---

### Post by azverkan on 2009-09-11
Running into the same Ctrl-C problem with Karmic.

Another thing I noticed is that when you exit sshd, the processes end up getting stuck as zombie process.


Just noticed that its a bug in udev from this thread:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/407428](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/407428)

---

