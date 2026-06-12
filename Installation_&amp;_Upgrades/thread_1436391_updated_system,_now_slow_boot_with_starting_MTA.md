---
title: "updated system, now slow boot with starting MTA"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by wallydallas on 2010-03-22
Steps below to reproduce this bug, and fix it
===============================================

Ubuntu 8.04 clean install
Ran update under system, Administration, Update manager
after updates my laptop boots very slowly

result: slow 5 minutes to boot, shows terminal screen error
"starting MTA"

expected result: quick boot from power up, 60 seconds, Ubuntu graphical boot without any ugly black and white text on screen

I solved the problem googling: MTA ubuntu 

Bigger question: What caused this and what can help Ubuntu mature to a point where it will not need an engineer to fix these errors. The posted fix was not newbie friendly.   This error and the posted fix is something I'd expect from windows.  

steps to fix:
- boot your pc slowly
- go to apps, accessories, terminal
- type in the command below:
sudo mv S20exim4 K20exim4 

- type in your password 
- you should not see any error message
- if you receive an error, you will have to change the "20" in the command
- use the command ls
- read the screen results, looking for KZZexim4
- notice the ZZ on your computer is not "20"
- run the mv command again, using your number rather than 20

- reboot your PC to see if the fix worked

---

### Post by lemming465 on 2010-03-25
Slowly starting mail daemons are often a symptom of DNS problems.  What kind of response do you get to "dig www.google.com"?

---

