---
title: "Installation  assistance please"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by spandon on 2008-04-25
Have clean installed 8.04 onto 4 machines without problems, but cannot install on one machine.
 I have tried both 8.04 r.c. and final using both desktop and alternative cd's.

I can open a live session using the desktop cd and editing grub utilising F6 + F6 again and using the dropdown menu to activate acpi=off noapic nolapic and the live session works perfectly in all respects.

BUT - when I install from either the Desktop or the alternative cd's, everything seems to go OK with the install - at the end restart - splash screens comes up then starts to build up the bar - gets to the last segment and then hangs, have left it for half an hour to see if it will go any further - but alas no joy.

I have also tried adding onto the edit line on startup menu:
after the word spash--acpi=off noapic nolapic nomsi vga=771, but still same result - this machine worked perfectly with 6.10, 7.04, 7.10 and as reported above also works perfectly in live session - so why wont it install?????

---

### Post by dsiembab on 2008-04-25
when you see the bar hit the esc key and you will see a text based load and probably see which programs are failing.

---

### Post by spandon on 2008-04-25
Hi dsiembab,
Thanks for your reply.
Had to press esc numerous times before it took me into Text based load.
The line it has stopped on is;
Starting DHCP D-Bus Daemon DHCDBD
Thanks
spandon

---

### Post by spandon on 2008-04-26
bump

---

### Post by spandon on 2008-04-27
Cracked it!
used alternative cd
At the grub menu,escape, choose to leave graphic menu,
At the Boot: type Install acpi=off noapic nolapic
rtn and follow the prompts as usual
And this time it worked....
I also found out that I could have gone into a live session, the edited the machines grub via the terminal.
the line that needs editing is the one with splash at the end of the line, just add:
acpi=off noapic nolapic after the word splash save and restart which would have saved me many hours of pulling my hair out anf re install after reinstall
Hope this may help someone else
Don

---

