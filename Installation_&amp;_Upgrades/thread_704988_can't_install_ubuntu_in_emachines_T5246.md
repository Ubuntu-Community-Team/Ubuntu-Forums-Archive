---
title: "can't install ubuntu in emachines T5246"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by sheine on 2008-02-22
The computer has an AMD AthlonX2 Processor 4200+ and Nvidia Get Force 6100. The problem is that the best resolution that it will give me is 800x600 which means that I cannot see the install button after I click the install icon. 

I had a similar problem with another computer but found a way to install it. After I installed it, I copied the configuration file from Simply Mepis and replaced the Ubuntu file. Everything then worked. If I could install Ubuntu from a script, I could pull the same  trick again as Simply Mepis works in my new computer.

---

### Post by logos34 on 2008-02-23
1. Try 'Safe graphics' option from the menu.  
2. Or on the desktop move the top and bottom panels to the sides---that should clear just enough extra space at the lower edge to see the 'continue'/back buttons.
3. Another option is to run

sudo dpkg-reconfigure xserver-xorg

4.  If none of that works get the text-version **alternate** install CD

---

### Post by sheine on 2008-02-23
Thanks to logos34. I put the panels on the side, installed Ubuntu hardy, and then copied xorg.conf from Mepis. Ubuntu is now the way that I want it.

---

