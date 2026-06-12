---
title: "Boot problem after installation"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by kushalshah on 2007-08-03
Hi, 
I heard about UBUNTU and tried installing it after using XP for 5 years. My PC configuration is P4 1.7 G, 1.25GB DDR RAM, 120 GB HDD. My OS got installed pretty well without any problem. The problem started when i booted for the first time. On the loading screen, the loading meter gets stuck at around 20 percent and the loading does not continue. It gives me no error whatsoever, it just halts. This is not the problem with UBUNTU only.. I have tried Fedora, OpenSUSE also, all have given me similar problems. I anyone can relate to this problem and reply to the same i would be grateful. I really want to use Linux and experience the bug free OS. Thanks in advance for the suggestions.   

KUSHAL SHAH

---

### Post by 505 on 2007-08-03
Linux is not bug free, as you've noted from your experience.
To diagnose what goes wrong, to the following. When you see the boot loader Grub (where you can select what OS to start), press 'e' to edit the entry. There will be a long line that ends with 'quiet splash'. Remove these last two words and press 'b' to boot. You'll see text scrolling on your screen so fast you can't read it, but that is not important. What is important is the text right before it halts. That should give you some clue as to why it stops. Use that to search for a solution, or report back here.

---

### Post by kushalshah on 2007-08-03
hey

I did as you asked me to. I got tonnes and tonnes of errors in that. Jus to giv u a brief. Last 3 read like this
[130.491415][<xxxxxxxxx] do_page_fault+0x128/0x5f0
[130.491415][<C02XXXXX] do_page_fault+0x0/0x5f0
[130.491415][C02eeb4C] error_code+0x7C/0x90

huh!!!!.. didnt understand a s***.... i am presently going mad coz i am attamepting this install from last 2 months now .. I hope you can help me .. Do i have to change any settings in BIOS??.. please do let me know .. thanks

Kushal

---

