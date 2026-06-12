---
title: "apt-get doesn't wait for confirmation"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by rockhopper on 2008-04-22
When I try to use apt-get for any job, it behaves as if I have the "enter" key pressed and does not ask for any future confirmations *automatically assumes default answer and prints a lot of blank lines similar to the case if I really have had the enter key pressed) I am sure that there is no problem with my "enter" key: it works fine with all other CLI applications.

Is this a known problem?

---

### Post by adityakavoor on 2008-04-22
The first time you enter something using apt-get, it asks confirmation. The next time you try using apt-get, it doesn't ask.

---

### Post by rockhopper on 2008-04-22
Perhaps I did not make myself clear. The problem is certainly not a feature of apt-get where it remembers my previous response and automatically assumes yes. 

The problem is similar to the case where the enter key on your keyboard is stuck and lot's of enters are being sent to the command line interface. For a proof of this, here is what happens, I do "sudo apt-get install <package>; I get lots of blank lines, the program asks for a confirmation: but since it behaves as if the enter key was being pressed, it passes the confirmation without waiting for my actual response.

---

### Post by steeldriver on 2013-02-23
Do you have an /etc/apt/apt.conf file? it's possible that an APT::Get::Assume-Yes option is set there

---

### Post by matt_symes on 2013-02-23
This is a 4 year old thread. Ancient. Thread closed.

---

