---
title: "Network troubles"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by anund on 2005-04-10
I have a small problem with a computer of a friend of mine, whom I have convinced to install Hoary :) 

This computer sits on a ADSL line with PPPoE, but the connection is handled by a broadband router, to which the computer is connected with a standard LAN connection.

When Ubuntu is installed, LAN networking is working perfectly. But the /etc/resolv/conf is wrong. When I manually change it to the right settings, Internet connection is working. 

But when the computer restarts, the settings in /etc/resolv.conf are reset.

How can I have the system keep the settings? Or is this something router-specific?

---

### Post by arctic on 2005-04-10
i guess this howto will answer all of your questions. read it carefully. if not, please report back.

[http://ubuntuforums.org/showthread.php?t=5690](http://ubuntuforums.org/showthread.php?t=5690) 
good luck :)

---

### Post by anund on 2005-04-12
Thank you very, very much. That solved the problem :-)

---

