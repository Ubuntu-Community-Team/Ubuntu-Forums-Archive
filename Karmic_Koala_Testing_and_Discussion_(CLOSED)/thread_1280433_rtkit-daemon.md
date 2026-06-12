---
title: "rtkit-daemon?"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jhawk on 2009-10-02
This is on a new install today from live CD, only downloads from Ubuntu.
Got around to setting up tail and got a suprise.

Setup:
Eterm -O -q -x --buttonbar 0 --scrollbar 0 -g 262x23+10-34  -e multitail -s 2 /var/log/syslog /var/log/kern.log

And to my suprise:

Oct  2 01:00:15 intel-box rtkit-daemon[1410]: Failed to make ourselves RT: Invalid argument  u

Need to research this one!

Please check the logs.....

location: /usr/lib/rtkit/rtkit-daemon and Elf file

jhawk

---

### Post by hugmenot on 2009-10-03
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/406702](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/406702)

---

