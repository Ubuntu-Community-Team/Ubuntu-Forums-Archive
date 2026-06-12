---
title: "Touch Screen not working after upgrade to Precise"
date: 2012-01-09
forum: Installation &amp; Upgrades
---

### Post by openick on 2012-01-09
[SIZE=4]He[/SIZE][SIZE=4]llo

Touchscreen was working in a tablet PC with 11.10, but after upgrade to 12.04 it stopped working.

I followed instructions from page [http://www.ehow.com/how_12160279_troubleshoot-touch-screen-ubuntu.html](http://www.ehow.com/how_12160279_troubleshoot-touch-screen-ubuntu.html) installed utouch and x-input calibrator. But the xinput calibrator returns an error on launch:  "[/SIZE][SIZE=4]Error: No calibratable devices found.

Attaching outputs of lsub, lspci and Xorg.0.log

1. How do I identify the id of the touchscreen ? ( It is working on android 4 and another operating system's preview version) 

2. What do I do to make Ubuntu detect touch screen ?

Thank you.
[/SIZE]

---

### Post by openick on 2012-01-09
[SIZE=2]apologies for posting the message above with a large font size. [/SIZE]

---

### Post by deport on 2012-05-06
Did you have any luck?

---

### Post by openick on 2012-05-08
Dear deport,


Yes, some luck. After a long time.

I installed 11.10 in a different partition and tried different things to make touch work, but there were persistent problems, quite possibly due to conflicting drivers / software / settings 

[http://ubuntuforums.org/showthread.php?t=1952039](http://ubuntuforums.org/showthread.php?t=1952039)

Came back to the 12.04 beta partition, upgraded to 12.04 stable, and touch is working as single finger touch (on a 5 point capacitive touch screen). Now will try and make multi-touch work.

Thanks :)

---

