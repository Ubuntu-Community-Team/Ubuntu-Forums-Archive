---
title: "module options in Ubuntu 6.06?"
date: 2006-10-24
forum: Installation &amp; Upgrades
---

### Post by wkulecz on 2006-10-24
Ubuntu lacks "standard" /etc/modules.conf file.

I'm trying to add card= options for saa7134 module.

I found /etc/modprobe.d/options and added the line.

Problem is I need two capture cards and the card= option doesn't seem to apply to the second card, not sure its really doing anything for the first card but I don't get the [/rant] no eeprom message in dmesg for the saa7130[0] like I do for saa7130[1]

Basically I seem to have stumbled on the syntax to make the first card take the option, but I've no idea how to make the second driver instance use the option.

--wally.

---

### Post by wkulecz on 2006-10-25
options saa7134 card=42 worked for /dev/video0, the problem was the second card was not taking the option and thus would not work.

Found the solution on the Video For Linux Mailing List archives via an ask.com search:

options saa7134 card=42,42

--wally.

---

