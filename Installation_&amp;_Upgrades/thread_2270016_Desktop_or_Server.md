---
title: "Desktop or Server"
date: 2015-03-19
forum: Installation &amp; Upgrades
---

### Post by Tony_Clarke on 2015-03-19
Sorry  if this has been asked before, im new to Ubuntu and have an old pc I wish to set up as a home server with the ability to send sign up confirmation emails. My dilemma is do I install desktop then virtual box  for the server, or just install server.

My machine will take both every easily and the ports need to open have been opened on the router, also my ISP Is NOT blocking ports 22, 25, and 80.

Thanking you all in advance,

Tony

---

### Post by Lars Noodén on 2015-03-19
Virtualbox is not needed.  If you install the Desktop system you can add the individual daemons you need, such as an SMTP server like exim or postfix.  If you plan on just logging into it with SSH and managing it that way then you do not even need the desktop and should just go with the Server image.

---

### Post by papibe on 2015-03-19
Hi Tony_Clarke.

+1 to  Lars Noodén's answer.

In other words, all those services can be setup on either on a server or a desktop. It just a matter of how comfortable are you using the command line, and how much hardware resources do you have. 

If you need a GUI, select a desktop environment that uses less resources. For instance, Lubuntu, Xubuntu or Ubuntu Mate.

Just a thought.
Regards.

---

### Post by Tony_Clarke on 2015-03-19
Thank you for the relies, so I take it that desktop will also be able to host my website as well.

---

### Post by Lars Noodén on 2015-03-19
Yes, just add a web server like Nginx or Apache2.

---

