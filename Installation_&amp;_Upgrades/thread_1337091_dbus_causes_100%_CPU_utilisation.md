---
title: "dbus causes 100% CPU utilisation"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by grifff on 2009-11-25
I recently upgraded  my Via based home server from 9.04  to 9.10, and ever since I've had high load on the machine.  When I look at the processes using top I can see that total CPU usage is ~100%, although the numbers for individual processes don't add up to anything like this:
[IMG]http://img267.imageshack.us/img267/2097/top1s.png[/IMG]

After some experimentation I found that stopping dbus (sudo stop dbus) made the CPU usage drop back down to normal, just as it was before I upgraded:
[IMG]http://img21.imageshack.us/img21/3123/top2m.png[/IMG]

Restarting dbus causes the 100% CPU usage again.  The session bus is very quiet, but the system bus seems pretty (see attached output of sudo dbus-monitor --system --profile), but I've no idea what is causing all these events.

Can anyone help?

---

### Post by grifff on 2009-11-26
After much playing around and googling I solved my own problem here.

The neverending dbus messages were caused by gdm, although I haven't a clue why.  As I don't need gdm running normally (its a low powered machine used as a NAS, local DNS  and print server) I simply disabled it by editing /etc/init/gdm.conf and adding a line to make it only start on runlevel 3 instead of always:

start on (runlevel [3]
          and filesystem
          and started hal
          and tty-device-added KERNEL=tty7
          and (graphics-device-added or stopped udevtrigger))

---

### Post by grifff on 2009-11-26
<deleted>

---

