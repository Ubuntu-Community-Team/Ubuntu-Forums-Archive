---
title: "hp 722c won't print: &quot;Job stopped due to filter errors&quot;"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by scheutz2002 on 2008-02-25
I installed xubuntu on a relative's broken windows machine.  It has an hp
722C printer.  Printer configuration appears to work, but nothing comes out.
The jobs just stay in the print queue.  After any new attempt, /var/lob/cups/error_log
has these new lines:

E [24/Feb/2008:16:08:55 -0600] PID 10900 (/usr/lib/cups/filter/foomatic-rip) stopped with status 3!
E [24/Feb/2008:16:09:07 -0600] [Job 8] Job stopped due to filter errors.

dmesg also gets these: 

[178291.806148] ppdev0: registered pardevice
[178292.469729] audit(1203891502.288:7):  type=1503 operation="inode_permission" requested_mask="rw"
denied_mask="rw" name="/dev/tty" pid=10972 profile="/usr/sbin/cupsd"
[178292.646713] audit(1203891502.288:8):  type=1503 operation="inode_permission" requested_mask="rw"
denied_mask="rw" name="/dev/tty" pid=10975 profile="/usr/sbin/cupsd"
[178292.659835] audit(1203891502.288:9):  type=1503 operation="inode_permission" requested_mask="r" d
enied_mask="r" name="/etc/pnm2ppa.conf" pid=10977 profile="/usr/sbin/cupsd"
[178307.095147] ppdev0: unregistered pardevice

Why would it be trying to access /dev/tty?

Also, in the web interface to cups, there was a message about permssion
problems on /dev/parport0, which I can't reproduce right now. 

/dev/tty is crw-rw-rw- 

/dev/parport0 was crw-rw----.  I changed it to crw-rw-rw-, to no avail.

---

### Post by prazgod on 2008-03-22
I have the same problem with a HP 2600n networked

This is an upgrade from gutsy to hardy beta

"Job stopped due to filter errors" in the cups error log

---

### Post by flunardelli on 2008-04-14
Try this: usermod -a -G lp USER

;)

---

