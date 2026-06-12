---
title: "update/x-server problem."
date: 2005-10-03
forum: Installation &amp; Upgrades
---

### Post by Kaparen on 2005-10-03
Hello! I Installed Ubuntu 5.04 (?) Hoary and everything worked OK except the graphics but I fixed the problem with this link:

[https://wiki.ubuntu.com/NvidiaManual](https://wiki.ubuntu.com/NvidiaManual)

no problems there. 
Yesterday I tried to update Hoary, there were 102 updates so I just clicked the instyall button. Half way through the installation halted and I was forced to press the resetbutton. I booted up and tried to update again but got a message saying that I had to do a 'dpkg --configure -a' in superuser mode which I did. rebooted again, updated, Ubuntu asked for my Hoary i386 CD, installed the updates and everything worked OK. 

Before I went to bed I did a reboot just to see if everything were allright. 
The Nvidia splash screen just blinked 3 times, pausing a fewseconds in between then I get this blue screen saying "cannot start up X-server, your graphics interface, probably a setup problem". Thing is I can´t press "yes" to see what is wrong because my keyboard doesn´t work, like it never got loaded. 

Could the "dpkg" have resetted my changes in xorg.conf and I´ll have to do them all over again. haven´t tried anything yet because I don´t want to mess things up even more. 

What have I done with the "dpkg" commando?
How do I fix the problem?

thank you!

---

### Post by Kaparen on 2005-10-03
OK I think I solved it, I just made a sudo mv xorg.backup xorg.conf and reinstalled the nvidia graphic drivers. Worked, almost, like a charm. 

What kind of file is xorg.conf? 
by deleting it, could I have lost any more information than just the graphic driver?
I have not altered it in any way except the nvidia settings, I was more thinking about the updates  I made in ubuntu.

?!

---

