---
title: "Webmin as live website using apache2"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by yahhodeol on 2010-03-17
Hi all


I have installed LAMP. Configured acc. to documentation.
I have installed webmin and able to access it.
Configured Apache2 and able to access default website [www.url.com]("http://www.url.com/") from public  network.
But now when i am trying to run [www.url.com/webmin]("http://www.url.com/webmin")   as alias, i am really confused  because whenever i type [www.url.com/webmin]("http://www.url.com/webmin") in web browser, it shows me  webmin file instead of GUI.
I followed this documentation:
[http://www.webmin.com/apache.html](http://www.webmin.com/apache.html)

Anyone have webmin running as website?


Thanks:
D

---

### Post by lisati on 2010-03-17
On my server, webmin is configured so that within my own network, I access webmin via the default port 10000 on the server. Try putting the following in the address bar of your browser:
```
https://server.lan:10000
```
(replace "server" with your server's name)

---

### Post by yahhodeol on 2010-03-18
> **lisati said:**
> On my server, webmin is configured so that within my own network, I access webmin via the default port 10000 on the server. Try putting the following in the address bar of your browser:
```
https://server.lan:10000
```(replace "server" with your server's name)



I can access webmin as hostname:10000, question is accessing it from public domaine.
Anyways thanks for replying.

---

