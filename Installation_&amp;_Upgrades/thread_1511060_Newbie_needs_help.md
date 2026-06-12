---
title: "Newbie needs help"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by ny2sf on 2010-06-16
Hello, 
 
I am new to Ubuntu and having trouble. A friend downloaded Ubuntu onto the laptop and I am using it wirelessly.  It moves very, very slow when I try to open any new links. it takes minutes for anything to come up and there is a res bar in the lower right hand corner.  i was informed to check the drivers, the only driver installed is the proprietary software modem.  Help, i really would like to get this up and running. What do i need to do? Thanks in advance.

---

### Post by lechien73 on 2010-06-16
It could be to do with IPV6 resolution. You could try:

[LIST=1]
[*]Go to System > Preferences > Network Connections
[*]Click on **Wireless**
[*]Highlight your connection and click **Edit**
[*]Click on **IPV6** and make sure it's set to *Ignore*
[/LIST]
Also, in Firefox, you could try the following:

[LIST=1]
[*]In the address bar type: **about:config**
[*]In the Filter box type: **ipv6**
[*]Change the value of the **network.dns.disableIPv6 **key to *true*
[*]Restart Firefox
[/LIST]

---

### Post by ny2sf on 2010-06-17
Hi, thanks.  That procedure helped a bit.  It is moving much faster than before.  It is still having trouble loading as it gets hung up.  there is also a delay in action. it takes a few seconds for the action to be completed after a click. 
 
I appreciate you breaking it down, as I am very "un" tech savvy.

---

