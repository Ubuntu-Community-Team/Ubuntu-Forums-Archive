---
title: "Some web connections don't work after upgrade to feisty"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by amarnik on 2007-04-23
Hi

I had 2 ubuntu desktops installed (one at home and one at work)
On Friday I did upgrade to Feisty and at home everything works fine (except vmware but I am still trying to fix it)
but at work internet connection works kind of weird.
I can get to some of the websites like this one, or google or many other but I cannot get to vmware.com etrade.com at all. I cannot even ping them
Whenever I open one of these websites I get headers and sometimes I get some of the html but ofter that it freezes and I can't get anything else.

My DNS setting are fine (I can get to some of the websites)
I found similar problem on the forum and I turned off ipv6 as proposed there but it didn't help at all.

If you want to see some of my config let me know. I have to fix it because I cannot work without fully functional internet.

---

### Post by amarnik on 2007-04-23
Hi with help of my friend I solved the problem

If you experience the same just add this line to starting script:

echo 0 > /proc/sys/net/ipv4/tcp_window_scaling

---

