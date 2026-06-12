---
title: "Problems after booting for the first time"
date: 2005-03-08
forum: Installation &amp; Upgrades
---

### Post by peji on 2005-03-08
Hi everybody,

 Trying to install ubuntu 4.10 in a laptop with 6Gb and 128Mb of RAM, all the process is ok until ubuntu reboots for the first time, after this a message pops up:

 hub 1-0:1.0: over-current change on port 2

 This message is continously in the screen and it's impossible to introduce any command.

 Any feedback will be welcome. 

 Thanks in advance.

 Peji

---

### Post by jsien on 2005-04-12
[QUOTE=peji]Hi everybody,

 Trying to install ubuntu 4.10 in a laptop with 6Gb and 128Mb of RAM, all the process is ok until ubuntu reboots for the first time, after this a message pops up:

 hub 1-0:1.0: over-current change on port 2

 This message is continously in the screen and it's impossible to introduce any command.

 Any feedback will be welcome. 

 Thanks in advance.

 Peji[/QUOTE]
 I am trying 4.10 on a compaq armada 100s and having the exact problem.

---

### Post by glycolized on 2005-04-15
I have a Compaq Notebook 100.

I have the same exact problem as well.

Installation seemed to go fine, then this error on first boot.

---

### Post by glycolized on 2005-04-15
OK, I just found this from a google search:
[I]
The messages mean that the card is reporting a change in the over-current 
status.  This isn't an error, it's just an informational message.[/I]

From this thread:
[http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg12901.html](http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg12901.html)

So, I just let it keep loading, watching that message scroll by, and it eventually loaded up.  It just took a while (I ran out to get food while I let it run).

---

### Post by jsien on 2005-04-18
you are right :-P

---

