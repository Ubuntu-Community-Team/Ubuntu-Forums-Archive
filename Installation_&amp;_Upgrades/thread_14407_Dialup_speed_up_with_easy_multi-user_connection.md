---
title: "Dialup speed up with easy multi-user connection"
date: 2005-02-07
forum: Installation &amp; Upgrades
---

### Post by geofff on 2005-02-07
At last I've succeeded in getting a usable dialup connection. I don't know why but the default dialler supplied with Ubuntu was my problem. I tried various fixes re IPv6 but none worked. My download speed for pdf files was between 0.8 - 1.0 kbps. - painful! My web page download seemed even worse. My pdf downloads are now 6 times faster and my web pages seem at least 10 times faster (although I've no way of measuring)

The solution for me was to follow the instructions at [www.ubuntulinux.org/wiki/DialupModemHowto](www.ubuntulinux.org/wiki/DialupModemHowto) to set up ppp, and to load "modem lights". I didn't as suggested make a connection script as it is dead easy to connect/disconnect by clicking the left part of the icon on the panel. After testing it I deleted the connection details in Network-admin (Computer> System Configuration> Networking)

As a bonus it is simple to add other users to ppp so that all users can connect/disconnect. 

I am a real novice and even I found this quite easy. If you've tried everything else do try this!

---

