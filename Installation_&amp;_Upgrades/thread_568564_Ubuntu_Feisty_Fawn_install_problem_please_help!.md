---
title: "Ubuntu Feisty Fawn install problem please help!"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by y2kss66 on 2007-10-06
Ok I am helping my friend install ubuntu and I first tried it with the live cd and every time after it would get past the boot screen it would get all glitchy graphically so I decided to try installing it with the alternative install cd and it installed perfectly with no problems until it booted up the first time in which the same graphic problem occured here is a picture of the problem: see end of post. he has a pentium D 3.2 ghz procesor and a pci express BFG 6600 graphics card I also believe the graphics card was over-clocked out of the box. Do any of you have and idea of what is going wrong and how I could fix it? Thanks in advance!

---

### Post by Herman on 2007-10-06
Here's a link you can read that might have some information in it that might help you, [Xserver Page]("http://users.bigpond.net.au/hermanzone/p7.html")   sudo dpkg-reconfigure xserver-xorg (video, keyboard & mouse drivers, settings).

You can turn off your Xserver by pressing Ctrl + Alt + F1 or any F key up to F6 and get a shell (black screen) that you can run commands from.

Pressing Ctrl + Alt + F7 will return you to the GUI (Desktop) , (or it will try to).

I hope that will help you at least a little bit. You could try running sudo dpkg-reconfigure xserver-xorg a few times and choosing different video drivers and maybe settings until you find out what works.
Regards, Herman.

---

### Post by y2kss66 on 2007-10-06
thanks for the idea will try today!
EDiT:
ok i am obviously new to linux and i don't understand everything it asked me so i am trying it now and will get back to you in a minute

---

### Post by y2kss66 on 2007-10-06
ok im distressed i have tried what you said and it didn't work then i deided to try ubuntu 7.10 beta, 6.10 and pclinuxos none of them worked and all ended up with similar graphics errors what coould be worng his computer worked fine with windows xp.

---

### Post by Pumalite on 2007-10-06
Herman it seems is not logged in. So, what are your specs?

---

### Post by y2kss66 on 2007-10-06
never mind i got it working i used the one command he gave me and installed teh vesa driver it worked yay!!!

---

### Post by PmDematagoda on 2007-10-06
The vesa drivers do not give you full graphical functionality, it is better if you solve your problem fully since you won't be able to run stuff such as Compiz or anything concerning graphics properly.

---

