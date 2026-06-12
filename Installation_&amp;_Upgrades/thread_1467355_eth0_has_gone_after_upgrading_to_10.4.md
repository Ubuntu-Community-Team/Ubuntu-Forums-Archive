---
title: "eth0 has gone after upgrading to 10.4"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by marciano#1 on 2010-04-30
I´ve just upgraded to 10.4
I have to load kernel 2.6.31.20 instead of default 2.6.32.21 (it freezes)
When the system starts up eth0 is missing. 
sudo modprobe e1000
lspci | grep net doesn't display anything
I am using an on board ethernet rj (intel)
Thanks for any help

---

### Post by verlyn13 on 2010-05-07
Same problem with new 10.04 install.  Wireless adapter is detected, but eth0 is gone. (have onboard lan)

---

### Post by Pratheek on 2010-05-07
did u try to configure the VPN connection ???

---

### Post by nicolastroche on 2010-05-07
I allways must use "sudo pppoeconf" for mi DSL, but in lucid lynx I havent to do it. I go to VPL, and there you can find LAN and DSL (if you use it, just like me)

---

### Post by verlyn13 on 2010-05-07
No, I'm a bit of a n00b, especially when it comes to network problems.  Only did the basic default install, since I have had no problems with my network devices for all previous installations over the last two years.

How do I go about trying to configure the VPN connection?

---

### Post by marciano#1 on 2010-05-07
Sorry, I forgot to post my solution.
It seems lan card has been reseted.
I turned off my computer and unplugged network wire for ten seconds.
After pluggin the wire and turning on it was fixed

---

### Post by Bergfex on 2010-05-09
I have the same problem. Interesting is that also "WinXP¨ has no LAN after shutting down Lucid. But if I turn off the computer (and plug off the electricity cable) than everything is working again. I have read from such problems also in the German forum. There they writing that they have to remove also the Laptop-battery before starting again. Have someone of you an idea why this is happens? Is there a possibility to fix it?

PS.: I'm using Ubuntu

---

### Post by hatebreed on 2010-05-09
I lost my connection also when I upgraded. I unplugged and plugged back in and nothing happened, then I left clicked the network icon at the top of the screen and clicked auto eth0 and it worked again. It's like after the upgrade it configures the card for manual config instead of auto.

---

