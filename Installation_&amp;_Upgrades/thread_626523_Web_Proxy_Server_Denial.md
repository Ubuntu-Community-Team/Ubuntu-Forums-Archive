---
title: "Web Proxy Server Denial"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by Visudo on 2007-11-29
I am trying to update Ubuntu 7.04.

I have installed Ubuntu 7.04 at work and at first I couldn't check for updates using Update Manager. 
So I configured the Proxy Server using Network Proxy Preferences. 

I can now check for updates but receive the following error message:

Access to the Web Proxy Server is Denied.


Can anyone please help me with this? I have other problems and you geniuses have sorted them out!!

Many thanks

Visudo

---

### Post by ilrudie on 2007-11-29
You can try adding a line to apt.conf file.  
The file can be found here:
/etc/apt/apt.conf

add the line

Acquire::http::Proxy "http://<username>:<password>@<proxy>:<port>";


replace <username> with your username, <password> with your password, <proxy> with the fully qualified proxy (or an IP address should work), and <port> with the port.

Goodluck

---

### Post by Visudo on 2007-11-29
ilrudie,

I spoke to my boss and he has shown me how to allow my computer through the Proxy Server and the Firewall to get the updates and the packages I need, but thank you anyway for your help!

Visudo

---

