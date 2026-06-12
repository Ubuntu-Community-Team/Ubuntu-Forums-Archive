---
title: "Accepting MSFT Eula in terminal?"
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by dreams@12 on 2012-01-07
Hi guys,

While trying to install ubuntu restricted extras using the following command

sudo apt-get install ubuntu-restricted-extras

I got a message with some agreement policy of microsoft. 
Please help me out as to what it is all about and how can i get rid of it
and continue further with my installations.

Looking forward to your replies at the earliest.

---

### Post by spacecheck on 2012-01-07
> **dreams@12 said:**
> Hi guys,

While trying to install ubuntu restricted extras using the following command

sudo apt-get install ubuntu-restricted-extras

I got a message with some agreement policy of microsoft. 
Please help me out as to what it is all about and how can i get rid of it
and continue further with my installations.

Looking forward to your replies at the earliest.

This would be a popup asking you to agree with the use of MS true-type fonts license, which are installed as part of the 'restricted' package. To agree, you hit the 'Tab' key until the 'Agree' button is highlighted and then click 'Enter'.

Should you have problems in the future, please be sure to start you own thread, instead of interrupting another's thread about an entirely different problem.

Good luck!

---

### Post by drsrinivas294 on 2012-01-08
Hii,me too faced the similar problem and solved it through following suggestion below,it worked well.


I would suggest using a different server. 
Open 'software sources' go to 'Download from: Main Server' and change it  to 'other' then choose 'best server' wait a few moments and close.

open terminal  	Code:
 	sudo apt-get update && sudo apt-get upgrade

---

### Post by oldos2er on 2012-01-08
Posts moved to their own thread. Please start your own thread rather than hijacking someone else's; thanks for understanding.

---

