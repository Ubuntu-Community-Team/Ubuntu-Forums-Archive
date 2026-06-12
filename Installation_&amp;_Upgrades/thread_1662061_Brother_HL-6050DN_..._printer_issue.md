---
title: "Brother HL-6050DN ... printer issue"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by xigen on 2011-01-07
Ubuntu 10.4 32 bit
(??).27 kernel
CUPS 1.4 printing system
system-config-printer 1.2.0 (A cups configuration tool)
Brother HL-6050DN

My printer (Brother HL-6050DN) worked yesterday.  Today, I get the message: Paused - "Unable to locate printer 'BRN_3C811E'!"

Perhaps this is related to the .27 kernel (*I really have no idea)

I tried reinstalling CUPS... and got the same error

..

When I go to the configuration interface - and try to check the 'enabled' box (Printing - localhost --> Policies -> 'enabled box' apply); the 'enabled' box does not stay checked.

..

I also tried to use:  [http://www.cups.org/](http://www.cups.org/)
Which has a terrific interface.  Unfortunately, I did not get the issue resolved.

Best,

MW

---

### Post by xigen on 2011-02-01
Solved.

1) find printer IP
-- look at test page
-- or use the printer control panel

2) put IP address in the printer config
system ->admin -> printing 
*see screenshot

3) check the box: enable printer

.

---

### Post by gandalf2000 on 2011-02-21
Thank  you very much xigen.  Mine stopped working for some reason and I couldn't get it going.  Thanks to you for  this solution it now works.

---

### Post by xigen on 2013-04-10
$ system-config-printer

somehow it works best to use the command (above) rather than the GUI which is incomplete.

---

