---
title: "[jaunty][karmic]PPPoE problem"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by laleshii on 2009-10-15
I have a problem with a pppoe connection. I've tried every possible methods and I can't figure out what's wrong with my connection.:mad:

The connection works on Windows;
Tried doing pppoeconf from the console while NetworkManager had my network card configured via DHCP. Entered the user and password with no success. Activated debug option in /etc/ppp/options

I can't paste the output because I haven't had a network connection or some kind of removable devices, but I can tell you the following.

It communicates with the server. At some point the server sends
rcvd [CHAP Challenge] .... user="rd4.serv.net" 
snt [CHAP ] ...  user="myusername"
... (some echo Requests)
CHAP authentication failure.

Can anybody give some tips about what can it be or how to better the debug the process?

Thanks in advance,
laleshii

---

