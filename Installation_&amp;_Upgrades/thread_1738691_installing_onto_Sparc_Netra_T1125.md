---
title: "installing onto Sparc Netra T1125"
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by kin37ik on 2011-04-25
g'day, have a bit of a problem with installing ubuntu onto my SPARC netra T1125 as my SPARC server has a CD rom drive but **[COLOR=Red]doesnt[/COLOR]** have a video card and no monitor ports at all so it makes installation difficult without being able to see what im doing.

i was told id have to install over/using a serial port and use some GUI software that uses the serial ports, is this the only way i can install it or can i somehow tap into my SPARC using the ethernet port to get a GUI so i can see what im doing? cheers.

---

### Post by TheHesser on 2012-12-13
Hey kin37ik,
I don't know if you already solved it but this is how I did it on my Netra T1 105:
I have a cysco serial to LAN cable and connected it to an old laptop to the LOM port on the server.
I installed Putty and connected to the server using the Serial setting. Then when you power the server it will show on the screen.
If you don't see anything right click on the top bar of Putty and select Special Command -> Break

I hope this helps.

TheHesser

---

