---
title: "vista need help with ubuntu"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by lowram00 on 2007-09-19
ok i have a dell m1330 with vista ulitmate and im tryin run a livecd  of ubuntu but i always get the [B] BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in Shell (ash)
Type 'help' for a full list of commands

/bin/sh: can't access tty; job control turned offis error  [/B]     and ive try everything but i cant get it to run any help would be liked plz thanks :guitar:

---

### Post by Pumalite on 2007-09-19
Try this:

At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

---

