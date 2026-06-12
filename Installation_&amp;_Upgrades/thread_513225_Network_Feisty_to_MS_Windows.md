---
title: "Network Feisty to MS Windows"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by BaronSantiago on 2007-07-30
Still pretty new to Ubuntu, but just upgraded to Feisty. On previous versions I could access my Ubuntu machine from my Windows XP network. Now it asks for a username and password to access the Ubuntu machine. Fine, but it does not recognise the only user and password for that computer. Is this a problem of network configuration?

I am not yet good on command line solutions, so if anyone has any ideas please bear this in mind.

thanks

---

### Post by talby on 2007-07-30
from what I recall, windows will only ask the password if it is different from the ubuntu machine running samba, and the usernames have to be the same on both windows and ubuntu.

Try changing the samba password to match the windows one.

There is a pretty good samba guide [here, "HOWTO: Setup Samba peer-to-peer with Windows" @ubuntuforums]("http://ubuntuforums.org/showthread.php?t=202605")

---

