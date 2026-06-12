---
title: "cannon ip1500 printer driver"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by a rogers on 2007-02-18
i have just installed ubuntu 6.06 ,but cant get my cannon ip 1500 printer to work using the installed drivers. can anyone advise?

---

### Post by tubasoldier on 2007-02-18
Buy a new printer? The Canon ip series is not supported under CUPS (common unix printing system). 

Maybe there is a printer driver out there that I do not know about. But more than likely you will have to pay for it.

---

### Post by a rogers on 2007-02-18
thanks

---

### Post by Stewart MacPherson on 2007-02-21
I am having a similar problem

Turboprint apparently have a "pay-for" driver (and also a free version) which I have downloaded as a    .deb file      (a google on Turboprint will get to their site)

When I try to install it however I get an error saying "Dependency is not satisfiable: libglib1.2"

Documentation from Turboprint's site says to install the GTK library using

sudo apt-get install libgtk1.2

Issuing this command from terminal results in an error  "Couldn't find package libgtk1.2"

I do not have an internet connection on my Ubuntu PC (another problem to be resolved later) so where can I get this library and how do I install it?

( I am genuinely a green green beginner at this so words of one syllable or less will assist )

:-) 
 
Mac from the Mountains

---

### Post by keithweddell on 2007-02-21
I got an IP2000 working using the bjc-8200 driver.  This was based on a recommendation (found by extensive googling) from someone who had just tried all of the Canon drivers until he found one that worked.   It might just be worth working through the Canon drivers by trial and error.

Keith

---

