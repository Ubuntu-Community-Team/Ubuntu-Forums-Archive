---
title: "Problem starting ubuntu after upgrade to 12.04"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by IronSentinel on 2012-05-06
hi all, first of all please edit/move this thread if not properly posted..

i just recently upgrade from 10.04 to 12.04 using upgrade manager and when i restarted there is a problem at startup right after the bios

the following message appears:
[B][FONT=Courier New]
[/FONT][/B][B][FONT=Courier New]** (plymouthd:320): WARNING **: Cannot sapwn a  message bus without a machine-id: Unable to load  /var/lib/dbus/machine-id or /etc/machine-id: Failed to open file  '/var/lib/dbus/machine-id': No such file or directory  undevd[343]:specified group 'colord' unknown

The disk drive for / is not ready yet or not present.
Continue to wait, or Press S to skip mounting or M for manual recovery[/FONT][/B]

(note that where it says plymouthd:320, it changes the number each time, 309, 320, etc)

if i press S:

[B][FONT=Courier New]Skipping / at user request
The disk drive for /tmp is not ready yet or not present.
Continue to wait, or Press S to skip mounting or M for manual recovery[/FONT][/B]

now if i press M:

[FONT=Courier New][B]Filesystem check or mount failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and continue booting after re-trying filesystems. Any further errors will be ignored
root@lucy-buntu:~# [/B][/FONT]

so.. i tried searching in internet for this problem but nothing seems to work..

did anybody experiences something similar? any help?

thanks!

---

### Post by weijun on 2012-05-12
I got the same thing on my sony laptop. Any solution?

---

### Post by darkod on 2012-05-12
Can you boot the machine with the ubuntu cd in live mode, open terminal and post the output of:
sudo fdisk -l (small L)
sudo parted /dev/sda print all

---

