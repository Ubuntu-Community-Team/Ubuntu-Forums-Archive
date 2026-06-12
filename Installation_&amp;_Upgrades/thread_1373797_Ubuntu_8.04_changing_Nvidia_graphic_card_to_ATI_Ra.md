---
title: "Ubuntu 8.04 changing Nvidia graphic card to ATI Radeon, Problems?"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by TelcontarVI on 2010-01-06
Hi, i'm going to change my old Nvidia Graphic card wich runs very well in Ubuntu by an ATI HD Radeon 4770. 

Will Ubuntu recognize it when i plug it and start the computer, will Ubuntu reconfigure by itself?... or i'm going to have problems like not to be able to start the X server and only be able to enter to the console.

Need i to remove the nvidia graphics driver before to plug in the new card?

I have downloaded a program called Envy, which is supposed to reconfigure ubuntu properly... it's ok?

Finllay, can i backup the curent configuration so that if the new card is not well installed i can return to the old without problems?

P.D Sorry for my bad english, but un the spanish ubuntu forums nobody answer me.

---

### Post by maybeway36 on 2010-01-06
If there's no /etc/X11/xorg.conf file, that should mean everything is autodetected. In that case, I think you should just be able to replace the card.

---

