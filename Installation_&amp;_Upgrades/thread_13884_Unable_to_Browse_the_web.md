---
title: "Unable to Browse the web"
date: 2005-02-03
forum: Installation &amp; Upgrades
---

### Post by weed on 2005-02-03
hi peeps i have just completed my 1st ubuntu installation everything else is working fine i configured my net connection settings to my isp using pppoe.  connecting direct using my dsl modem to my ISp . I have managed to get connected i have been assigned an ip address , but the problem arises when i try to browse the web. 
pages are not loading i tryed disconnecting and reconnecting but the problem still occurs. are they any settings i have missed out or steps i have to take inorder to get it working. 

help is appreciated.

---

### Post by domzo on 2005-02-03
This is a guess, but pppoe stands for point to point protocol over ethernet, which would suggest you should be connecting via a local network. If you're connecting direct try ppp instead.

As I say, this is a guess, I've not played around with Ubuntu much yet.

domzo

---

### Post by Joeb on 2005-02-03
[QUOTE=weed]hi peeps i have just completed my 1st ubuntu installation everything else is working fine i configured my net connection settings to my isp using pppoe.  connecting direct using my dsl modem to my ISp . I have managed to get connected i have been assigned an ip address , but the problem arises when i try to browse the web. 
pages are not loading i tryed disconnecting and reconnecting but the problem still occurs. are they any settings i have missed out or steps i have to take inorder to get it working. 

help is appreciated.[/QUOTE]

Does your dsl modem assign you an address (DHCP) or did you manually enter one?  If manually, did you enter a DNS server?  Without it, you won't be able hit web sites, because it translates the web address to an ip address.  Even if your modem did assign you ip address, your ISP might still require you to manually enter a DNS address.

---

### Post by thestarman on 2005-02-03
[QUOTE=weed].... I have managed to get connected i have been assigned an ip address, but the problem arises when i try to browse the web. 
pages are not loading....[/QUOTE]

Weed,  I would concur with Joeb's remark that you need to check your DNS setting!  What's happening to you is exactly what happens to anyone without a way to convert domain names to IP numbers via a DNS server!  As he said, your ISP may require you to enter one manually, but it might be some problem getting one assigned to you automatically too.

The Starman.

---

### Post by weed on 2005-02-07
my dns settings are configured properly they are automatically assigned, tried manually still no change, changed browser same effect.. i even tryd connecting my adsl router which automatically configures my system wen using windows , it works perfectly fine, am able to ping get a response . once i boot up ubuntu in fact any other distro or live cd am unable to surf the web yet i have a valid ip and local ip. may its smthn small that i havent thought of.

---

