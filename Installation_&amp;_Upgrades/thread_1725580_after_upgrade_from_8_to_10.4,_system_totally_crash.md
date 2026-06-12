---
title: "after upgrade from 8 to 10.4, system totally crashed"
date: 2011-04-09
forum: Installation &amp; Upgrades
---

### Post by ipfreak on 2011-04-09
hi gurus:

i tried to upgrade two hardy them to 10.4 lcui and failed miserably. after upgrading, both fail to finish rebooting process; they stuck at maintenance mode.

are there ways to rescue them? something went very wrong...

---

### Post by Hedgehog1 on 2011-04-10
Lets get a look at what shape your partitions are in and what can be saved (and get you running again).

Please boot off your 10.04 LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.


***The Hedge***

:KS

---

### Post by ipfreak on 2011-04-10
INIT:ureadahead main process (2677) terminated with status 5 libudev:udev_monitor_new_from_netlink:error getting socket:invalid argument mountall:mountalll.c:3204 Assertion failed in main:udev_monitor_new_from_netlink (udev, &quot;udev&quot;)  init:mountall main process (2680) killed by ABRT signal;  General error mounting filesystems  A maintenance shell will now be started and reboot system.   root#     ok, now i am trying to following your instructions and running systems on livcd

---

