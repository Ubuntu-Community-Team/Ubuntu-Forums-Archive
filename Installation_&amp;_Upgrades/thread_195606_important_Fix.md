---
title: "***important Fix****"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by nick holme on 2006-06-13
It took a few days to pin this down but here's my contribution.

After upgrading to Dapper, I found that I couldn't use synaptic and a few other administration tools from "System, Administration". If I opened a terminal and entered "sudo synaptic" then it worked but a message appeared each time I tried any command saying "unable to look up *systemname* via gethostbyname()". I eventually noticed that I had my system name set at "Ubuntu Main" as I had been experimenting with more than one ubuntu machine on my network. It occured to me that I had experienced problems in the past with Linux software when using a name with spaces in it. I changed the system name in /etc/hosts and /etc/hostname to simply Ubuntumain  i.e. without any spaces - rebooted and everything is now fine. I hope this helps others as I came across a number of threads exploring the gethostbyname() problem and the synaptic not working problem but none had this particular cure as an option.

---

