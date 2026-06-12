---
title: "OpenSSH extern ip"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by herrbrand on 2008-10-01
hello

I compiled openssh and it works fine on LAN. i add a link in the router but it won't work from my outside IP. I found more people with this problem but no selutions.

Robbert

---

### Post by Herman on 2008-10-01
Have you tried 'port forwarding'?
Most routers have a very good firewall built into them and that would usually do a very good job of stopping all or just about all unwanted traffic from the outside world from getting into your LAN.
The problem is, it will probably also stop you from getting in too, unless you set up 'port forwarding'.
Here is a link to a website that shows you how to set up port forwarding with all kinds of different routers, [PORT Forward.com]("http://www.portforward.com/default.htm")
You should look up your brand and model of router there and set your router up accordingly.

---

### Post by davidryder on 2008-10-01
What is the model # on your router? I had the same problem, you just have to open the port in your router config. 

[http://192.168.1.1](http://192.168.1.1) or [https://192.168.1.1](https://192.168.1.1) (assuming that is the IP address of your router).

If it's a linksys router, it should look like this:

---

### Post by herrbrand on 2008-10-01
I have an siemens gigaset SX551. I already forward the port 5222. I us that port for openssh.

Robbert

---

### Post by Herman on 2008-10-01
How did you test to make sure that your port forwarding was successful?

---

