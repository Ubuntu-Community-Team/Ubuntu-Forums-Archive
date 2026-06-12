---
title: "HP dv2000 laptop - Feisty problems :("
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by s3raphim on 2008-01-04
Well I have a new shiny HP dv2416us.  Two days ago I put Gutsy on it.... then I read a lot about power management and started all over with Feisty.  I'm having two really big, and possibly related problems:


1) I got the Broadcom wireless up and running nicely with the ndiswrapper howto's that everyone has posted.  
/etc/network/interface looks like:

auto lo
iface blah blah blah 

(only these two lines)

and for a little while everything was hunky dory.  Then I rebooted.  About 75% of the time, when I reboot, the wireless does not work.  The current permutation is the Network Manager can't find it, the little light stays red, and ifconfig sees it and shows "loopback"

then the second problem.
2) My computer is supposed to go to sleep about 20minutes.  Then it is supposed to wake up.  I left a completely working machine alone, came back, and on wakingit up could not see my mouse and the wireless card and died (i.e. little blue light is now red)

HELP

One another note, dbus restart shows avahi errors, but on making the recommended (bug #?) change of removing mdns4 from the host line in /etc/nsswitch.conf (or something) , nothing was improved so I put it back,

I'm very sad.  I want my machine to be happy :(  Any suggestions welcome.  I'm not a complete n00b, but I've never run Linux on a laptop before.  I tried to do my homework, but some guidance at this point would be much appreciated.

kernel: 2.6.20-16-generic

---

### Post by s3raphim on 2008-01-04
Yet another side note:  I tried white-listing usbcore to see if it helps with the sleeping problem....no word yet as to whether it actually worked.

---

