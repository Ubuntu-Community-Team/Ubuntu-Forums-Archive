---
title: "VisualVM does not start on Ubuntu 10.10"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by FreshP on 2010-12-03
I just installed Ubuntu10.10 (i had 9.10 before that). I am trying to run VisualVM (which was already installed) and i get the following error

"You are running VisualVM using Java Runtime Envoronment (JRE). Please use Java Development Kit (JDK) to run VisualVM"

I have Sun JDK installed. How do I instruvt VisualVM to use the JDK?

Thank you

---

### Post by FreshP on 2010-12-03
Ok I found the solution here [https://visualvm.dev.java.net/description.html#getting_started.]("https://visualvm.dev.java.net/description.html#getting_started")

For the record it is specified in file /etc/visualvm/visualvm.conf

---

### Post by mahy on 2010-12-30
Thanks for your discovery; that webpage only deals with Windows issues :-#

---

