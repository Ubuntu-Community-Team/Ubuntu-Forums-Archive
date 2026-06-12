---
title: "How to shut off 'auto ethernet' ?"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by alvinmoneypit on 2011-01-17
After so recent updates, I find the network connections has changed. 

I see now that it connects to the network (dsl) by default.  I unchecked the box 'connect automatically', yet it still is connected by the time the monitor turns on when awakened from sleep or hibernation.  

How can I get the auto network connection turned off without physically pulling the plug? 


I'm running 10.10 Ubuntu desktop edition
Thanks for all responses.

---

### Post by fabricator4 on 2011-01-17
> **alvinmoneypit said:**
> I see now that it connects to the network (dsl) by default.  I unchecked the box 'connect automatically', yet it still is connected by the time the monitor turns on when awakened from sleep or hibernation.  


Reboot (just in case) and if the problem persists submit a bug report.  Definitely not expected behaviour.

Chris

---

### Post by alvinmoneypit on 2011-01-17
Thanks, Chris.

I looked at my settings and find that I have 2 wired connections according to Ubuntu, but in reality there is only one as far as I know.  "auto ethernet" is the one ubuntu says I'm using and I had set it as I had stated earlier, unchecking the box for "connect automatically". 
 I looked at my other wired connection, which is named "Auto eth0" and it also had the "connect automatically" check box which was checked.  I unchecked it and rebooted.  It did not log onto the network as it had done previously.  A little confusing since Ubuntu list that connection "last used" as 'never'.

I think that's what Ubuntu called my connection before the updates, i.e. "Auto eth0".  

I'll check later if when it goes to sleep it wakes up immediately online.

---

### Post by alvinmoneypit on 2011-01-17
It stays off line when awakened from sleep now.  I still wonder why it shows two connections when in fact there is only one.

---

