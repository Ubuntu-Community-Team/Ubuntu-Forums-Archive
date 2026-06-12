---
title: "create automated startup command for Canon's ccpd daemon for LBP printers"
date: 2017-03-03
forum: Installation &amp; Upgrades
---

### Post by pdc on 2017-03-03
so the CAPT driver that Canon provides for its LBP printers; creates what is called a ccpd daemon; (in addition to installing drivers); and it needs to be started with the command > [COLOR="#FF0000"]sudo /etc/init.d/ccpd start[/COLOR]

back in 2012, to automate it [https://ubuntuforums.org/showthread.php?t=1982917](https://ubuntuforums.org/showthread.php?t=1982917) the suggestion was a 3 step process; taken from post #6 in the above thread:

1) create a udev rule called 85-canon-capt.rules that goes inside /etc/udev/rules.d
2) Modify the file 70-printers.rules in /lib/udev/rules.d
3) create an Upstart job, putting a file ccpd-restart.conf inside etc/init

I successfully installed Canon's newest 64bit CAPT driver for our LBP in a 16.04 ubuntu; the old advice no longer works to automate the command at startup;

I would be very grateful for advice on how to do this with 16.04

---

