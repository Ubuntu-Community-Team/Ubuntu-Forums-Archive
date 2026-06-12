---
title: "Long story .... need help.... confused on changing video card issue...."
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by sent17inel on 2007-08-24
ok heres my story and dilema... A friend of mine asked me to install ubuntu on his system. Fiesty Fawn to be specific. He has a gateway with a pentium 3 processor, 512 mb of ram and a nvidia card that used the legacy driver. Thats all i know off hand about his video card right now. He wanted the compiz fusion eye candy so i installed it but his video card wasnt powerful enough to run the program so i called and told him. He said he had an nvidia geforce 5800 i think or something along those lines. He says he took it out of another computer a while back because it was overheating. I said ok ill install it. So without changing anything on the ubuntu install which was setup to run his orgininal old nvidia card i just opened the box and popped in the new nvidia card in the same place. the agp slot. When i plug everything in i got nothing but a black screen., i turned of the computer and put in the old nvidia card and still got the black screen. I then proceeded to plug in my monitor into the onboard integrated video card and i finally got a display. Ubuntu tried to load but then said that i had a problem with X server .... I half expected that so right now im reinstalling ubuntu... my only fear is how the heck do i get the old video card to work again? it just doenst wanna display anything...... and what went wrong? please help asap as i want to get this computer out of my life......

---

### Post by Pumalite on 2007-08-24
For the old card you said 'legacy driver'?: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Try 7185. If not, try 9639
For black screen: if command line: sudo dpkg-reconfigure xserver-xorg. Accept most defaults; choose 'vesa' as your driver.

If no command line; try Crtl+Alt+F1 or F2 or Alt+F1, etc

---

### Post by Pumalite on 2007-08-24
Let me know if you need help installing proprietary driver.

---

### Post by sent17inel on 2007-08-24
Ya but when i first installed linux on that box i didnt have to have the monitor connected to the onboard video card like i do now. Will installing those drivers work? Im not sure if the computer is even recognizing the video card... because when i put in the live cd it doesnt show the video card as present under i think "device manager"? or whatever that thing is called. It only shows the integrated graphics contorller.....

---

### Post by Pumalite on 2007-08-24
You have to first get IN the system with: sudo dpkg-reconfigure xserver-xorg ; then worry about appropiate drivers.

---

### Post by sent17inel on 2007-08-24
Ive reinstalled ubuntu. so im in the system now. when i check device manager the old video card is not listed. Even though i know its connected to the motherboard.

---

### Post by Pumalite on 2007-08-24
You need a new video card it seems. Make sure is compatible with your system and supported by Ubuntu at the same time.

---

### Post by sent17inel on 2007-08-24
sh#t so the video card is fried?

---

### Post by Pumalite on 2007-08-24
You can review the connections, etc

---

